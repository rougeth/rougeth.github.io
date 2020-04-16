---
layout: post
title: Expressões Match em Rust
date: 2020-04-16 23:41 +0100
---
Meu primeiro contato com Rust foi durante a Python Brasil 2016.  Naquele ano, foi a linguagem convidada da conferência, e a keynote Hanneli apresentou uma [excelente palestra](https://www.youtube.com/watch?v=kP5olvIlTmc) sobre o sistema de tipos do Rust. Desde então, a linguagem entrou na minha lista quase infinita de tópicos para estudar.

Recentemente voltei a estudar Rust e aproveitei para testar a nova versão do [Exercism](https://exercism.io/), uma plataforma de exercícios de diversas linguagens de programação, entre elas Python, Go, Javascript, e claro, Rust. Umas das coisas que eu acho mais legal sobre o Exercism, é que depois de resolver um exercício e submeter a solução, é possível ver como as outras pessoas resolveram o mesmo problema. E foi assim que aprendi sobre expressões `match` em Rust.


## Resolvendo ano bissexto
Um dos exercícios que resolvi no Exercism foi o ano bissexto (_leap year_ na plataforma), cujo objetivo era escrever uma função que, recebesse por parâmetro um ano e retornasse verdadeiro se aquele ano fosse bissexto, ou falso caso contrário.

> Chama-se **ano bissexto** o ano ao qual é acrescentado um dia extra, ficando com 366 dias, um dia a mais do que os anos normais de 365 dias, ocorrendo a cada quatro anos (exceto anos múltiplos de 100 que não são múltiplos de 400).
_Wikipedia_

Para resolver o exercício, usei dois blocos `if`. Poderia ter feito tudo em um bloco só, ou até mesmo em uma única linha, mas optei pela legibilidade nesse caso.

```rust
pub fn é_ano_bissexto(ano: u64) -> bool {
    if ano % 4 != 0 {
        return false;
    }
    if ano % 100 == 0 && ano % 400 != 0 {
        return false;
    }
    true
}
```

Simples, né? Se eu fosse resolver esse problema em Python, linguagem que tive mais contato, provavelmente o fluxo seria o mesmo, mudando apenas a sintaxe de uma linguagem para a outra.

Quando terminei, fui ver como as outras pessoas haviam resolvido. Foi então que vi a solução com maior pontuação no Exercism. No lugar dos `if` que eu usei, a pessoa usou uma expressão  `match` para fazer as checagens necessárias para o ano bissexto.

Expressão `match` em Rust é uma estruturas de controle de fluxo que executa um bloco de código de acordo com o valor de uma expressão ou variável. Em Python não temos tal estrutura, mas em C, por exemplo, se assemelha ao `switch`.

```rust
let x = 1;

// A expressão nesse caso dependerá do valor de `x`
match x {
    // padrão => expressão a ser executada
    1 => println!("um"),
    2 => println!("dois"),
    3 => println!("três"),
	  // O `_` funciona como um coringa, se nenhuma das
    // opções combinar com o valor de `x`, a expressão
    // presente no `_` será executada.
    _ => println!("outros"),
}
```

O exemplo acima mostra um exemplo básico do uso do  `match` em Rust.  Primeiro definimos uma variável `x` de valor 1.  Depois iniciamos um bloco usando `match`, passando a variável criada logo acima. Dentro do bloco, do lado esquerdo do `=>`, definimos as combinações possíveis do valor `x`,  e no lado direito, o que fazer em cada uma dessas combinações. No primeiro caso, se `x` for igual 1, o programa mostrará o texto `”um”`.

O código abaixo é a solução com maior pontuação no Exercism para o problema do ano bissexto:

```rust
pub fn é_ano_bissexto(ano: i64) -> bool {
    match (ano % 4, ano % 100, ano % 400) {
        (0, 0, 0) => true,
        (0, 0, _) => false,
        (0, _, _) => true,
        (_, _, _) => false,
    }
}
```

Nesse exemplo, podemos ver que também é possível enviar mais de uma variável para o `match` e criar combinações com todas elas.

## Match Arms
O lado esquerdo do `=>` se chama _match arm_,  como vimos nos exemplos anteriores, é nele que definimos as combinações possíveis que serão testadas com os valores passados ao `match`. Mas além dos inteiros ou valores exatos, é possível fazer diversos outros testes.

###  Range patterns
Podemos definir um `range` de valores como um padrão. Se o valor passado para o `match` estiver dentro dessas variação, a expressão será escolhida.

```rust
match idade {
    0 ..= 11 => "criança",
    12 ..= 17 => "adolescente",
    18 ..= 64 => "adulto",
    _ => "idoso",
};
```

Também é possível criar um _range_ de caracteres:

```rust
match c {
    'A' ..= 'Z' => true,
    'a' ..= 'z' => false,
}
```

O exemplo acima é apenas ilustrativo, o método `is_uppercase()` deveria ser usado para saber se o caracter é maiúsculo ou não.

### Operador |
Com o operador `|` é possível definir uma mesma expressão para diversas combinações diferentes:

```rust
match x {
    1 | 3 | 5 | 7 | 9 => "ímpar",
    2 | 4 | 6 | 8 | 10 => "par",
    _ => "Outros",
}
```

### Match Guards
Uma forma de refinar o critério de combinação é usando _match guards_,  que nada mais é do que uma expressão boleana definida da seguinte forma:

```rust
let par = (2, -2);
let resultado = match par {
    (x, y) if x == y => "São iguais",
    (x, _) if x % 2 == 0 => "O primeiro é par",
    _ => "Nenhuma correlação encontrada..",
}
```

Ainda nesse caso vemos que a expressão escolhida no `match` será atribuída a variável `resultado`.

Apesar da grande diferença em relação a Python, tem sido muito divertido aprender Rust. Excelente documentação e mensagens de erros extremamente úteis contribuem demais para quem está começando a estudar a linguagem. Recomendo a quem tiver a oportunidade de estudá-la.

Abaixo segue as referências que lembrei de guardar enquanto estudava Rust e escrevia essa texto.

- https://doc.rust-lang.org/reference/expressions/match-expr.html
- https://doc.rust-lang.org/rust-by-example/flow_control/match.html
- https://doc.rust-lang.org/reference/patterns.html#range-patterns

**o/**
