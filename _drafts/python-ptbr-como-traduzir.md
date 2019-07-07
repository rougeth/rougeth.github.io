---
layout: post
title: 'Documentação do Python em Português: Como traduzir?'
---


Há um bom tempo venho pensando em como melhorar o atual cenário da tradução da documentação do Python para português. Inclusive, já comecei algumas iniciativas para tentar facilitar e melhorar o processo, mas nada promissor. Dessa vez, para não perder o fio da meada pretendo deixar tudo registrado, fazendo uma série de blog posts com o que encontrar pela frente.

Clique no link abaixo para ler o primeiro texto sobre a documentação em português. Nele mostro uma visão geral sobre os processos, as ferramentas usadas, comunidade e etc.

- [Documentação do Python em Português: Cenário Atual](/blog/python-ptbr-cenario-atual)

---

## Antes de começar

Antes de qualquer coisa, recomendo entrar no grupo **@pybr_i18n** no Telegram. Caso você tenha algum problema com as ferramentas usadas ou dúvidas enquanto estiver traduzindo, você encontrará apoio da comunidade por lá.

Para começar a traduzir, o primeiro passo é [criar uma conta]() no Transifex, ferramenta que a comunidade no Brasil usa para traduzir a documentação do Python.

Com a conta criada, é necessário solicitar acesso ao time de tradução. Para isso, siga os passos abaixo:
1. Acesse a página do time [clicando aqui]();
2. Escolha o projeto `Python`, referente a última versão da documentação;
3. Clique em `Join Team`;
4. E por fim, selecione a língua na qual você deseja traduzir e clique em `Join`;

Após solicitar acesso, você deverá receber uma mensagem de confirmação e aguardar algum coordenador aceitar as novas inscrições. Esse processo tende a ser rápido, mas como é manual, pode demorar algumas horas.

![]({{ site.url }}/assets/python-ptbr-como-traduzir/transifex-novo-cadastro.jpg)


## O que traduzir?

Acessando a página de tradução para português, é possível ver a lista de seções da documentação e o progresso de suas traduções. Para publicarmos a tradução no site oficial, é necessário que três seções estejam completamente traduzidas, são elas: a página de bugs, os tutoriais e a documentação das funções e bibliotecas *builtin*. A página de bugs e os tutoriais já foram traduzidos, portanto a prioridade agora são as funções e bibliotecas *builtins*.

Para facilitar na busca das seções que precisam ser traduzidas, busque por `library--` e ordene de forma crescente os resultados por progresso.

![]({{ site.url }}/assets/python-ptbr-como-traduzir/transifex-library.jpg)

## Como traduzir?

Ao escolher uma seção para traduzir, você verá todos os recursos (palavras, frases, títulos, etc) que precisam ser traduzidos. Para enviar uma tradução de um dos recursos é simples, basta digitar a tradução e clique em `Save Translation`. 

No exemplo abaixo, na seção `library-asyncio`, escolhi traduzir o trecho `Hello World!`, para isso foi necessário apenas digitar a tradução no campo de texto e clicar no botão `Save Translation`.

![]({{ site.url }}/assets/python-ptbr-como-traduzir/transifex-como-traduzir.jpg)

Como nem todas as traduções são simples que nem o exemplo, você pode precisar de ajuda com alguns trechos mais complexos. Para isso, as abas de contexto, sugestões e glossário podem ajudar com informações como, por exemplo, de onde aquele trecho pertence na documentação ou sugestão de tradução baseada nas já existentes.

Porém, priorize sempre os trechos mais simples e rápidos de se traduzir. O volume ainda é muito grande e ainda temos muitos casos como "Hello World!" na documentação.

## E como revisar?

Não se preocupe com as revisões agora, como temos um volume muito grande de trechos não traduzidos e o foco atual é chegarmos num nível em que possamos publicar a tradução no site oficial.

---

Se você tem alguma sugestão ou interesse em saber mais sobre a tradução da documentação do Python para português brasileiro, não deixe de ler o outros textos que escrevi. Junte-se ao grupo no Telegram.
