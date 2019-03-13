---
layout: post
title: 'Documentação do Python em Português: Cenário Atual'
---

Há um bom tempo venho pensando em como melhorar o atual cenário da tradução da documentação do Python para português. Inclusive, já comecei algumas iniciativas para tentar facilitar e melhorar o processo, mas nada promissor. Dessa vez, para não perder o fio da meada pretendo deixar tudo registrado, fazendo uma série de blog posts com o que encontrar pela frente. Para começar, quero falar do estado atual da tradução da documentação em português.

---

## O cenário atual
Apenas outras 3 línguas além do inglês estão disponíveis no site oficial da documentação do Python: francês, japonês e coreano. Já em português, apenas cerca de 17% da documentação foi traduzida. Número que tende a cair (e já vem caindo) conforme novos textos são inseridos ou atualizados.

A [PEP 545](https://www.python.org/dev/peps/pep-0545/#add-support-for-translations-in-docsbuild-scripts) foi criada como um guia para tornar as traduções existentes da documentação mais acessíveis. Nela são descritos os requisitos necessários para publicar a tradução no site oficial. Isso inclui, por exemplo, ter os seguintes itens 100% traduzidos:

- [Tutoriais](https://docs.python.org/3/tutorial/); 
- [Bibliotecas e funções](https://docs.python.org/3/library/index.html), as famosas baterias que vêem incluídas no Python;
- [bugs.html](https://docs.python.org/3/bugs.html), página que informa em como lidar com bugs encontrados;

Dos nossos 17%, temos a página *bugs.html* toda traduzida. Já em relação aos tutoriais e bibliotecas, nem sabemos o quanto falta.

### A ferramenta
O [Transifex](https://transifex.com) é uma plataforma web, proprietária e paga de tradução. É amplamente usada por grandes empresas e, por oferecerem plano gratuito para projetos de código livre, também é usado pela comunidade Python em todo mundo. Para a comunidade brasileira, o Transifex é o ponto central de tradução. Nela está todo conteúdo já traduzido e é também a única opção para novas traduções. Eu, particularmente, não a considero a melhor opção para o projeto, talvez por ser a única opção disponível hoje, mas isso é assunto para outro texto.

### A comunidade
O esforço por parte da comunidade é sazonal, aumentando sempre pós a Python Brasil e diminuindo logo em seguida. Há um grupo no Telegram com pouco mais de 30 pessoas, mas com pouca tração. Na maioria das vezes, trocamos mensagens apenas quando alguma pessoa entra no grupo perguntando como as coisas funcionam (sintoma de que as instruções não estão claras ou de fácil acesso).

A principal referência de como colaborar está no site  [python.org/traducao](https://python.org.br/traducao/). É possível encontrar os links para os projetos no Transifex,  dicas para tradução e até uma menção à documentação do Django. Apesar do texto não estar bem estruturado e da maior parte do conteúdo ter sido feita na época em que o 2.7 era a principal versão do Python, acredito que o material continua relevante.

## Próximos passos:
Uma das etapas para publicar a tradução no docs.python.org, antes mesmo de ter as seções listadas acima traduzidas, é criar um repositório  para as traduções e adicionar-lo no projeto [docsbuild-scripts](https://github.com/python/docsbuild-scripts/), responsável por gerar o site da documentação oficial. O repositório para tradução em português já existe, agora é preciso preciso manter o Transifex sincronizado com o Github. Mas, ter as traduções em um repositório abre uma outra discussão: qual melhor ferramenta para usarmos? Ou melhor, precisamos escolher uma?

Outro passo importante é ter ciência de onde precisamos focar para ter a tradução publicada. Já usei a API do Transifex (em uma das iniciativas frustadas), sei que é possível resgatar as informações que precisamos.

Por enquanto é isso. Vou tentar manter o blog atualizado com as próximas descobertas.

o/
