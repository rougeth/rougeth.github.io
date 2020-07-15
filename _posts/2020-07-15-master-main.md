---
layout: post
title: Git checkout main - Como mudar a branch padrão do seu projeto
date: 2020-07-15 21:05 +0100
---
Mudar a *branch* padrão do seu projeto no Github é mais simples do que parece. Você vai precisar executar alguns comandos no terminal, mas se você estiver usando Gitlab, pode fazer tudo pela interface. Vou começar pelo Github:

## Criando a main 🙏

```bash
# Comece clonando o projeto no seu PC
$ git clone git@github.com:<usuário>/<projeto>

# Se você já tiver o projeto localmente, vá para a branch master e atualize
$ git checkout master
$ git pull

# Crie o novo branch "main"
$ git checkout -b main

# Envie o novo branch para o Github
$ git push -u origin main
```

## Atualizando Github

Para atualizar o Github, acesse as configurações de *branches* do seu projeto em [https://github.com/\<usuário\>/\<projeto\>/settings/branches](https://github.com/\<usuário\>/\<projeto\>/settings/branches). Na primeira seção, **Default branch**, escolha a nova *branch* e atualize o repositório. Logo abaixo, caso exista alguma regra de proteção específica para *master*, mude para a nova *branch main*.

Para excluir a *master* de vez, acesse [https://github.com/\<usuário\>/\<projeto\>/branches](https://github.com/<usuário>/<projeto>/branches) e 🗑.

## E no Gitlab, como faz?

No Gitlab é possível fazer todo processo pelo próprio site:

- Para criar um novo *branch*, acesse:  [https://gitlab.com/\<usuário\>/\<projeto\>/-/branches/new](https://gitlab.com/\<usuário>\/\<projeto>\/-/branches/new)
- Para mudar o *branch* padrão, acesse: [https://gitlab.com/\<usuário\>/\<projeto\>/-/settings/repository](https://gitlab.com/\<usuário>\/\<projeto>\/-/settings/repository)

## Mas... por que?
[@Una Kravets](https://twitter.com/Una/status/1271181775130279936) resumiu bem em um *tweet*:

![Motivos para mudar de master para main. 1) main é um nome menor, 2) mais fácil de lembrar, 3) se faz qualquer membro do meu time mais confortável, vale a pena 4) se evita mesmo que apenas uma pessoa preta de se sentir isolada na comunidade técnica, não tem discussão](/assets/master-main/why.png)

**o/**
