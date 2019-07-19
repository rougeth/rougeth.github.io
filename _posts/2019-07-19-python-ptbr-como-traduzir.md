---
layout: post
title: 'Documentação do Python em Português: Como traduzir?'
---


Há um bom tempo venho pensando em como melhorar o atual cenário da tradução da documentação do Python para português. Inclusive, já comecei algumas iniciativas para tentar facilitar e melhorar o processo, mas nada promissor. Dessa vez, para não perder o fio da meada pretendo deixar tudo registrado, fazendo uma série de blog posts com o que encontrar pela frente.

Os links abaixo são os dois primeiros textos sobre a documentação em português que escrevi. Neles mostro uma visão geral sobre os processos de tradução, ferramentas usadas, comunidade e sobre o progresso já feito até aqui.

- [Documentação do Python em Português: O que já foi traduzido?](/blog/python-ptbr-traduzido)
- [Documentação do Python em Português: Cenário Atual](/blog/python-ptbr-cenario-atual)

---

## Antes de começar

A comunidade de tradução mais ativa está no grupo **@pybr_i18n**, no aplicativo [Telegram](https://telegram.org/). Por lá, é a forma mais fácil e rápida de encontrar apoio em casos de problemas com as ferramentas usadas ou dúvidas enquanto estiver traduzindo. Portanto, antes de mais nada, recomendo fazer parte do grupo.

Para começar a traduzir, o primeiro passo é [criar uma conta](https://www.transifex.com/signup/) no Transifex, ferramenta que a comunidade no Brasil usa para traduzir a documentação do Python.

Já com a conta criada, é necessário solicitar acesso ao time de tradução. Para isso, siga os passos abaixo:
1. Acesse a página do time [clicando aqui]();
2. Escolha o projeto `Python`, referente a última versão da documentação;
3. Clique em `Join Team`;
4. E por fim, selecione a língua na qual você deseja traduzir e clique em `Join`.

Após solicitar acesso, você deverá receber uma mensagem de confirmação e aguardar algum coordenador aceitar as novas inscrições. Esse processo tende a ser rápido, mas como é manual, pode demorar algumas horas. De qualquer forma, mande uma mensagem no grupo do Telegram.

![Mensagem de confirmação de tradução]({{ site.url }}/assets/python-ptbr-como-traduzir/transifex-novo-cadastro.jpg)


## O que traduzir?

Acessando a página de tradução para português, é possível ver a lista de seções da documentação e o progresso de suas traduções. Para publicarmos a tradução no site oficial, é necessário que três seções estejam completamente traduzidas, são elas: a página de bugs, os tutoriais e a documentação das funções e bibliotecas *builtin*. A página de bugs e os tutoriais já foram traduzidas, portanto **a prioridade agora são as funções e bibliotecas *builtins***.

Para filtrar as seções que precisam ser traduzidas, busque por `library--`, conforme imagem abaixo:

![Página listando as seções disponíveis para tradução no Transifex]({{ site.url }}/assets/python-ptbr-como-traduzir/transifex-library.jpg)

## Como traduzir?

Ao escolher uma seção para traduzir, você verá todos os recursos (palavras, frases, títulos, etc) que precisam ser traduzidos. Para enviar uma tradução de um dos recursos é simples, basta digitar a tradução e clique em `Save Translation`.

No exemplo abaixo, na seção `library-asyncio`, escolhi traduzir o trecho `Hello World!`. Para isso foi necessário apenas digitar a tradução no campo de texto e clicar no botão `Save Translation`.

![Página de tradução no transifex]({{ site.url }}/assets/python-ptbr-como-traduzir/transifex-como-traduzir.jpg)

Como nem todas as traduções são simples que nem o exemplo acima, você pode precisar de ajuda com alguns trechos mais complexos. Para isso, as abas de contexto, sugestões e glossário podem ajudar com informações extras como, por exemplo, de onde aquele trecho pertence na documentação ou sugestão de tradução baseada nas já existentes.

Porém, **priorize sempre os trechos mais fáceis e simples** de se traduzir. O volume ainda é muito grande e temos muitos casos como "Hello World!" na documentação.

### Mas e como revisar?

Como ainda temos muito o que traduzir, por enquanto não precisamos nos preocupar com revisões. Porém, mesmo que o processo de revisar seja mais simples que de traduzir, o volume é o mesmo. No próximo texto vou falar um pouco sobre as ferramentas que temos para nos auxiliar a revisar as tradução já feitas da documentação.

## Como acompanhar o progresso?

A API do Transifex é limitada em relação as estatísticas que podemos extrair da ferramenta. Por exemplo, não é possível saber quem já traduziu uma determinada seção ou quem mais vem contribuindo nas últimas semanas.

Em contra partida, dá para saber o quanto já foi traduzido e revisado em todas as seções da tradução. Usando essa informação, criei um robô no Telegram que coleta os dados diariamente e, todo domingo, envia uma mensagem comparando as estatísticas dos últimos 7 dias.


![Mensagem do bot no Telegram com estatísticas]({{ site.url }}/assets/python-ptbr-como-traduzir/bot.png)

---

Espero que com esse texto, fique um pouco mais claro como dar o primeiro passo para contribuir com a tradução da documentação do Python para português. E lembre-se, ideias e sugestões são sempre bem vindas.

**o/**
