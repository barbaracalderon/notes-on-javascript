# EN: JavaScript Overview

What is JavaScript?

Our first definition was:

```
"Javascript is a high-level object-oriented, multi-paradigm programming language."
- Jonas Schmedtmann.
```

But here's another one:

```
"Javascript is a high-level, prototype-based object-oriented, multi-paradigm, interpreted or just-in-time compiled, dynamic, single-threaded, gargabe-collected programming language with first-class functions and a non-blocking event loop concurrecy model."
- Jonas Schmedtmann.
```

It says a lot.

Let's break the information into small pieces and talk about them.

## High-level

Computers need hardware to work. The low-level languages manually handle resources. "C" is a low-level language. The high-level languages do not manually handle resources because they work with abstractions that take that work from the user. "Javascript" and "Python" are high-level languages.

## Garbage-collected

The "Garbage Collector" is an algorithmn inside the Javascript Engine that handles computer resources by automatically "cleaning" the memory so we don't have to.

## Interpreted or Just-in-time Compiled

Computers only understand 1 and 0.

Every program must convert themselves to 1 and 0 so machines understand it. That means every code should be machine-translated to 1 and 0. Javascript handles that internally in its Engine.

## Multi-paradigm

A paradigm is an approach and mindset of structuring code, which will direct your coding style and technique.

There are three popular paradigms:

1. **Procedural programming**: it's organized code with some functions in between. What we have been doing so far.
2. **Object-oriented programming** (oop)
3. **Functional programming** (fp)

Javascript allows all three paradigms above.

It's the user's choice to pick one that fits best.

## Prototype-based object-oriented

Take the arrays we create in Javascript, for example.

It "copies" itself from an Array Prototype already created and available. This prototype has its own properties and methods. Our created array inhrerits these properties and methods from the prototype.

More on this later.

## First-class functions

Functions are treated as variables. We can pass them into other functions as parameters, and return them from functions. 

*This allows functional programming to happen.*

## Dynamic

Remember dynamic data types? Javascript is a dynamically-typed language. The data type of a value inside a variable can be automatically changed.

## Single-threaded

*A thread is a set of instructions that is executed in the computer CPU. It's where our code is executed in the machine processor.*

"Concurrency model" is how the Javascript Engine handles multiple tasks happening at the same time.

Why would we need that the "concurrency model"?

Because **Javascript runs in one single-thread**, so it can only do **one thing at a time**.

So, what about a long-running task? A task that needs a really long time to conclude itself?

Sounds like it would block the single thread. However, we want non-blocking behaviour! We achieve that by using an **event loop**.

By using an event loop, it takes long-running tasks and **executes them in the "background" and puts them back in the main thread once they are finished**.

## Check the definition again

Should make sense now.

```
"Javascript is a high-level, prototype-based object-oriented, multi-paradigm, interpreted or just-in-time compiled, dynamic, single-threaded, gargabe-collected programming language with first-class functions and a non-blocking event loop concurrecy model."
- Jonas Schmedtmann.
```
---
# PT: Visão Geral do JavaScript

O que é Javascript?

Nossa primeira definição era:

```
// (Tradução minha em PT, não do autor original)

"Javascript é uma linguagem de programação de alto-nível, orientada-a-objetos, multi-paradigmática."
- Jonas Schmedtmann.
```
Mas aqui vai outra definição:

```
// (Tradução minha em PT, não do autor original)

"Javascript é uma linguagem de programação de alto-nível, orientada a objetos baseada em protótipos, multi-paradigmática, interpretada ou rapidamente compilada, dinâmica, de único-fio e coletora de lixo com funções de primeira-classe e um modelo de simultaneidade com laço de evento não-bloqueador."
- Jonas Schmedtmann.
```
Muita coisa.

Vamos quebrar a definição acima em pequenos pedaços e falar sobre eles.

## Alto-nível

Computadores precisam de hardware para trabalhar. As linguagens de baixo-nível lidam com os recursos de máquina manualmente. A linguagem "C" é um exemplo. As linguagens de alto-nível não precisam lidar com os recursos de máquina manualmente porque elas trabalham com abstrações que retiram esse trabalho manual do usuário. Exemplos de linguagens de alto-nível são "Javascript" e "Python".

## Coletora-de-lixo

O "Coletor de Lixo" é um algoritmo dentro do motor Javascript que lida com os recursos de computador automaticamente ao "limpar" a memória pra que não precisamos fazer isso manualmente. 

## Interpretada ou rapidamente compilada

Computadores só entendem 1 e 0.

Todo programa precisa se converter em 1 e 0 para que as máquinas possam entendê-lo. Isso significa que todo código precisa ser traduzido para a máquina em 1 e 0. Javascript lida com essa tradução internamente em seu Motor. 

## Multi-paradigmática

Um paradigma é uma abordagem e mentalidade de estruturar código, que direciona o seu estilo e suas técnicas de "codar".

São três paradigmas populares:

1. **Programação procedural**: é o código organizado com algumas funções nele. É o que temos feito e mostrado até agora (se você seguir as anotações pelos seus índices).
2. **Programação orientada-a-objetos"** (poo)
3. **Programação funcional** (pf)

Javascript permite os três paradigmas acima.

É escolha do usuário escolher uma que seja melhor para o seu objetivo.

## Orientado-a-objetos baseada em protótipos

Vamos tomar um array que criamos em Javascript como exemplo.

Esse array "copia" a si mesmo de um Protótipo de Array que já está disponível para cópia. Esse protótipo tem suas propriedades e métodos. Nosso array criado "herda" (de "herança" mesmo) essas propriedades e métodos do protótipo.

Mais sobre isso nas anotações à frente.

## Funções de primeira-classe

Funções são tratadas como variáveis em Javascript. Nós podemos passar uma função como argumento de outra função, e também podemos retornar uma função de outra função.

*Isso permite a programação funcional acontecer.*

## Dinâmica

Lembra da tipagem dinâmica? O Javascript é uma linguagem de tipagem dinâmica. O tipo de dado de um valor em uma variável pode ser automaticamente mudado. 

## De fio-único

*Um fio é um conjunto de instruções que é executado na CPU do computador. É onde o nosso código é executado no processador da máquina.*

"Modelo de simultaneidade" é como o motor do Javascript lida com múltiplas atividades acontecendo ao mesmo tempo.

Por quê precisaríamos de um "modelo de simultaneidade"?

Porque Javascript **executa em um único-fio**, então ele só consegue **fazer uma coisa por vez**.

E uma atividade de longo-prazo? Uma atividade que precisasse de muito, muito tempo para ser concluída?

Para que isso bloquearia o fio único. Entretanto, nós queremos um comportamento de não-bloqueio desse fio único! Nós conseguimos isso usando um **laço de eventos**. 

Ao usar um laço de eventos, ele **executa uma atividade de longo-prazo "por baixo dos panos" e devolve a conclusão ao fio principal depois que terminar de executar.**

## Olhe a definição de novo

Deve fazer sentido agora.

```
// (Tradução minha em PT, não do autor original)

"Javascript é uma linguagem de programação de alto-nível, orientada a objetos baseada em protótipos, multi-paradigmática, interpretada ou rapidamente compilada, dinâmica, de único-fio e coletora de lixo com funções de primeira-classe e um modelo de simultaneidade com laço de evento não-bloqueador."
- Jonas Schmedtmann.
```
