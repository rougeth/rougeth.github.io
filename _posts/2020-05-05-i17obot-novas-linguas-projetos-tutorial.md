---
layout: post
title: 'Atualizações no i17obot: Novas línguas, projetos e tutoriais'
date: 2020-05-05 19:16 +0100
language: pt-br
translation: /blog/i17obot-updates-languages-projects-tutorial
---
O [i17obot](https://github.com/rougeth/i17obot/) é um robô criado para auxiliar na tradução da documentação oficial do Python para português. Entre as suas funcionalidades, a principal é selecionar um trecho da documentação sem tradução e enviar para seus usuários. Nos últimos dias, tivemos 3 grandes atualizações no robô.

## Hola Robot!

O i17obot agora é bilingue! A comunidade Python que fala espanhol começou a se movimentar para traduzir a documentação. Com o interesse da comunidade e algumas mudanças no código, foi possível fazer o robô funcionar para múltiplas línguas. O i17obot ainda está sendo traduzido, mas a seleção e o envio dos trechos da documentação a serem traduzidos, já funcionam tanto para português quanto para espanhol.

Para escolher para qual língua você deseja traduzir a documentação, basta usar o comando `/languages` e robô apresentará as opções.

## Projeto Jupyter

Inicialmente criado com foco na documentação do Python, o robô agora também ajudará na tradução da documentação do projeto [Jupyter](https://jupyter.org/). A [Leticia Portella](https://leportella.com/) fez uma série de mudanças que tornaram o i17obot genérico para qualquer iniciativa de tradução, o que abre diversas novas possibilidades para o robô.

Para escolher entre a documentação do Python ou do Jupyter, use o comando `/project`. A escolha funciona de forma global, ou seja, o projeto escolhido será considerado em todos os outros comandos.

## Tutorial

O processo para para começar a traduzir a documentação não é trivial. É preciso criar uma conta na plataforma Transifex, acessar a página do time/projeto, pedir acesso, etc. Para facilitar a entrada de novos contribuidores, criei um tutorial em vídeo mostrando o passo a passo explicando o que é necessário fazer até poder de fato traduzir a documentação. Para acessar o tutorial, basta usar o comando `/tutorial` no robô.

## Próximos passos

Com as últimas mudanças, algumas partes do código ficaram mais complexas e precisam ser refatoradas. Além disso, estou planejando um pequeno tutorial em vídeo sobre como o robô funciona.

Acesse a página [projeto no Github](https://github.com/rougeth/i17obot/) para saber mais ou entre no grupo [@pybr_i18n](https://t.me/pybr_i18n).

**o/**
