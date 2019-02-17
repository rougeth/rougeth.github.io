---
layout: post
title:  "Creating a Django model instance in the past"
date:   2017-03-24 00:00:00 +0000
permalink: /posts/creating-a-django-model-instance-in-the-past/
categories: django python
---

In Django, if you want to save the date an instance was created and/or updated, you can use DateTimeField with the flags `auto_now_add` or r`auto_now`. They automatically set the field to now every time the object is created and saved, respectively. And it's common to have tasks that depends on the date a specific object was created/updated.

For example, I have an Invoice model that has a paid flag to indicate if it was paid or not and a `updated_at` field that tells me the last time that invoice was updated, using `auto_now` flag (every time an invoice is saved, the `updated_at` field is updated with the current time):


{% highlight python %}
class Invoice(models.Model):
    # ...other fields
    paid = models.BooleanField(default=False)
    updated_at = models.DateTimeField(auto_now=True)
{% endhighlight %}

To make easier to control the invoices not paid, I created a task that runs everyday to notify me of all invoices that weren’t paid and weren’t updated in the past two days:

{% highlight python %}
def check_pending_invoices():
    invoices = Invoice.objects.filter(paid=False,
                                      updated_at__lt=two_days_ago)
    if invoices:
        notify(invoices)
{% endhighlight %}

Really simple, right? Now it is time to test `check_pending_invoices` task (sure you always have every line of your app covered by tests :). This is a really simple example, so we just need to create two tests to cover the task. The first one should check if the notify function wasn’t called, since no invoice was created. To do that, I am going to use `mock.patch()` decorator from the Python built-in library unittest. The best definition of mocking a function I found is from [Mike Lin](https://www.fugue.co/blog/2016-02-11-python-mocking-101):

> A mock function call returns a predefined value immediately, without doing any work. A mock object’s attributes and methods are similarly defined entirely in the test, without creating the real object or doing any work. The fact that the writer of the test can define the return values of each function call gives him or her a tremendous amount of power when testing […]

So, I’m not actually interest in how notify works or what it returns. The test target is `check_pending_invoices` function, everything besides that is from another scope.

{% highlight python %}
from unittest import mock

class TestInvoice(TestCase):
    @mock.patch('path.to.notify')
    def test_no_pending_invoices(self, mocked_notify):
        check_pending_invoices()
        # Assert that the notify (mocked) function
        # was not called after running check_pending_invoices
        # because no invoices were created
        mocked_notify.assert_not_called()
{% endhighlight %}

The second test checks the case that at least one invoice was found by the task and here I found the problem. Before calling `check_pending_invoices`, I need to create an invoice with two specific properties: the paid flag set to false and the `updated_at` field with the date from at least two days ago. The first thing that comes to your mind is something like this:

{% highlight python %}
two_days_ago = timezone.now() - timedelta(days=2)
invoice = Invoice.objects.create(paid=False,
                                 updated_at=two_days_ago)
{% endhighlight %}

After creating the instance, if you check the value of `updated_at` field, it won’t be equal to `two_days_ago`. Can you see why this way doesn’t work? Inside `Model.objects.create()`, Django will call the `save()` method of the model and inside of it, will look every `DateTimeField` with `auto_now` flag. If it finds any, the current datetime will be set for the field. No matter what value you set, `save()` will overwrite it.

In this part of Django’s code, you can see that `timezone.now()` is used to get current datetime when the field is a `DateTimeField`. So the magic of creating a model instance in the past, is nothing more than mocking `timezone.now()` to return whatever datetime you want:

{% highlight python %}
from datetime import timedelta
from django.utils import timezone

# We can use the same struct of the first test
@mock.patch('path.to.notify')
def test_pending_invoices(self, mocked_notify):

    # First we need to create the invoice
    two_days_ago = timezone.now() - timedelta(days=2)
    with mock.patch('django.utils.timezone.now') as mocked_now:
        # Here we set a value that will be returned when
        # timezone.now() is called
        mocked_now.return_value = two_days_ago

        # Django will use the mocked_now function to set the
        # value of updated_at field
        Invoice.objects.create(paid=False)

    check_pending_invoices()

    # Assert that the notify (mocked) function
    # was called after running check_pending_invoices
    mocked_notify.assert_called()
{% endhighlight %}

Done! We created a model instance “in the past” and now our task is 100% covered by tests. Don’t forget that in the context you’re using mock, hopefully only with tests, the mocked function will not work properly. If you want to learn more about it, I recommend the text [Python Mocking 101: Fake It Before You Make It](https://www.fugue.co/blog/2016-02-11-python-mocking-101) and, of course, the Python documentation.

---

### *Update 27/03/2017*

As mentioned by @luiscastillocr on Twitter, instead of using Mock, we could use the model manager `update()` method. It will ignore fields with `auto_now` flag and, in our case, change the `updated_at` field. A possible side effect of this approach is that we’re doing a new query on the database.
