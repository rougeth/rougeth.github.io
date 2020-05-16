---
layout: post
title: Como mantenho minhas configurações do Vim
date: 2020-05-09 20:11 +0100
language: pt-br
translation: /blog/how-do-i-maintaing-my-vim-settings
cover: /assets/vim-settings-tools.jpg
cover_description: Hand Tools
---
Meu primeiro contato com o editor de texto Vim foi logo quando entrei na faculdade, em uma aula de cálculo há quase 10 anos atrás. Antes da aula começar, um colega, Dirley, que eu ainda não conhecia, estava sentado nas fileiras da frente com o laptop aberto trabalhando em algum projeto.

Tela com fundo preto e dividida ao meio, de um lado textos coloridos e do outro linhas e linhas rolando pela tela. Ele apertava algumas teclas e tudo se mexia. Sério, ele estava na [Matrix](https://www.youtube.com/watch?v=HAyqFGhEY5o)! Se me oferecesse um pílula vermelha eu tomava sem pensar duas vezes!

Foi assim que fui apresentado ao Vim. Quando me dei conta do tamanho da comunidade por trás do editor, fiquei impressionado. Milhões de configurações, atalhos, plugins, temas. E de repente, havia caido num buraco negro. Incontáveis horas perdidas ~~tentando fechar o Vim~~ configurando o editor, aprendendo os atalhos, instalando *plugins*, tentando fazer os temas funcionarem, tudo na base do *ctrl-c ctrl-v* do que achava interessante por ai.

Até que um dia decidi tentar aprender o que cada configuração fazia e por fim escolher as melhores opções para mim. Desde então, há pelo menos 6 anos, uso basicamente a mesma configuração do Vim.

Neste texto, não vou falar sobre a melhor configuração ou plugin que você deva usar, mas como se organizar para não ficar perdido quando quiser fazer alguma mudança.

## Dividir e conquistar

O `.vimrc` é o arquivo que o Vim procura as configurações do usuário. No meu caso, tenho as configurações divididas em 4 arquivos diferentes dentro da pasta `~/.vim`, com o `.vimrc` servindo apenas como um agregador dos demais arquivos. Essa estrutura de arquivos veio do querido [Humberto Rocha](https://humberto.io/), que muito me ensinou sobre Vim. 

```vim
" Configurações do Vim
source ~/.vim/config.vim

" Plugins que uso 
source ~/.vim/plugins.vim

" Configurações dos plugins
source ~/.vim/plugin_config.vim

" Atalhos
source ~/.vim/atalhos.vim
```

## Configurações do Vim

Todas as configurações exclusivas do Vim, com exceção dos atalhos, vão no arquivo `config.vim`. Como guia para escolher o que e como configurar o editor, usei bastante a própria [documentação do Vim](https://vimhelp.org/), em particular a seção [options](https://vimhelp.org/options.txt.html#options.txt). Você pode usar a documentação no site [vimhelp.org](https://vimhelp.org), mas se quiser acessá-la de dentro do Vim, aqui vai algumas dicas:

- `:help` para acessar a página inicial
- `:options` te leva direto para as opções de configuração
- Para ir direto para uma seção específica, coloque o cursor acima do nome da seção e pressione `CTRL-]`;
- Para voltar o cursor aonde você estava, use `CTRL-O`.

Uma das configurações que mais gosto, é poder abrir um arquivo no Vim com o cursor no mesmo lugar que ele estava quando fechei o arquivo pela última vez:

```vim
au BufReadPost * if line("'\"") > 0|if line("'\"") <= line("$")|exe("norm '\"")|else|exe "norm $"|endif|endif
```

Confira o restante das minhas configurações em [config.vim](https://github.com/rougeth/dotvim/blob/master/config.vim).

## Plugins

Todos os *plugins* que uso ficam listados no arquivo `plugins.vim` e são instalados pelo [vim-plug](https://github.com/junegunn/vim-plug). Até a versão 8 do Vim, lançada em 2016, era necessário usar um *plugin*, como o `vim-plug` para instalar outros *plugins*. Como `vim-plug` sempre funcionou comigo, não migrei para a opção nativa.

Os 3 *plugins* que mais gosto são:
- [ctrlp.vim](https://github.com/ctrlpvim/ctrlp.vim): Permite buscar de forma extremamente rápida os arquivos a partir do diretório que o Vim foi aberto. É sem dúvidas o *plugin* que mais uso.
- [NERDTree](https://github.com/preservim/nerdtree): Uma espécie de Finder do MacOS ou Explorer do Windows. Uso bastante quando não conheço bem a estrutura de pastas e arquivos do projeto que estou trabalhando.
- [vim-gitgutter](https://github.com/airblade/vim-gitgutter): Indica as linhas que foram adicionadas, modificadas ou removidas de acordo com Git.

Exemplo de como usar o `vim-plug` para instalar os 3 *plugins* acima:

```vim
" Ativa o vim-plug
call plug#begin()

Plug 'scrooloose/nerdtree'
Plug 'kien/ctrlp.vim'
Plug 'airblade/vim-gitgutter'

" Você pode instalar qualquer plugin direto do Github da seguinte forma:
" Plug 'perfil/plugin'

" Todos os plugins precisam ficar entre o `plug#begin()` e `plug#end()`
call plug#end()
```

## Configurações dos plugins

Cada *plugin* permite uma série de configurações diferentes, como por exemplo, os atalhos que ativam o `ctrlp.vim` ou `NERDTree`. Na época, optei por separar as configurações em arquivo um arquivo exclusivo, `plugin_config.vim`. Hoje, acredito que faria diferente, apenas o arquivo `plugins.vim` seria suficiente para gerenciá-los e configurá-los.

## Atalhos

Já o arquivo `atalhos.vim` teve sua última mudança há 5 anos atrás, na época em que reorganizei o repositório. Me limitei a poucas customizações, pois os atalhos do próprio Vim, apesar de difíceis de aprender, te permite ser bastante eficiente. Além disso, não ser muito criativo nos atalhos facilita quando é preciso usar o Vim em um computador sem as suas configurações, seja acessando um servidor remotamente ou pareando com alguém.

O atalho que mais uso é o `jj`, que foi mapeado para a tecla `ESC`, ou seja, sempre que pressiono `jj`, o Vim interpreta como `ESC`:

```vim
imap jj <esc>
```

---

Todos os arquivos estão no [Github](https://github.com/rougeth/dotvim). Você pode seguir as instruções no `README.md` para instalar ou criar um *fork* com as suas próprias configurações.

![Meme Fork All The Things](/assets/vim-settings-fork-all-the-things.jpg)

E lembre-se, para sair do Vim: `:q`

**o/**
