---
layout: post
title: 'i17obot updates: New languages, projects and tutorials'
translation: "/blog/i17obot-novas-linguas-projetos-tutorial"
language: en
date: 2020-05-06 19:33 +0100
---
The [i17obot](https://github.com/rougeth/i17obot) is a Telegram bot created to help the translation of the Python documentation to Portuguese. Its main feature is to select a string from the docs without a translation and send it to its users. In the last few days, it had 3 significant updates.

## Hola Robot!

The i17obot is now bilingual! The Spanish Python community started the efforts to translate the documentation. With their interest and a few changes in the code, it now accepts multiple languages. The bot itself is still being translated, but it can already select and send strings to be translated in both Portuguese and Spanish.

To choose which language you want to translate the documentation, send `/languages` and the bot shows the options.

## Project Jupyter

Initially created to translate the Python documentation, i17obot can also help to translate the documentation of [Project Jupyter](https://jupyter.org/). [Leticia Portella](https://leportella.com/) refactored the code, making it generic enough to accept any translation project that uses Transifex. The changes open many opportunities for the project.

To choose between Python or Jupyter documentation, send `/project` to the bot. Your choice will be considered to every other command and the daily reminder.

## Tutorial

Until you can contribute to the translation, there are a few non-trivial steps that you need to complete, like creating an account on Transifex or accessing and joining the project page. To make it a bit clear, I created a tutorial to show step by step, what is needed to start. To see the tutorial, send `/tutorial` to the bot. It's only in Portuguese for now.

## Next steps

With the last changes, part of the code grew in a complex way that now needs to be refactored. Beyond that, I'm planning to do a quick tutorial explaining how i17obot works and how to use it.

To see more, access the [project page on Github](https://github.com/rougeth/i17obot/) and join our telegram group [@pybr_i18n](https://t.me/pybr_i18n).

**o/**
