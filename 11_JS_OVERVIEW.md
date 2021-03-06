# EN: JavaScript Overview

What is JavaScript?

Our first definition was:

```
"Javascript is a high-level object-oriented, multi-paradigm programming language."
- Jonas Schmedtmann.
```

But here's another one:

```
"Javascript is a high-level, prototype-based object-oriented, multi-paradigm,
interpreted or just-in-time compiled, dynamic, single-threaded,
gargabe-collected programming language with first-class functions and a
non-blocking event loop concurrecy model."
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

_This allows functional programming to happen._

## Dynamic

Remember dynamic data types? Javascript is a dynamically-typed language. The data type of a value inside a variable can be automatically changed.

## Single-threaded

_A thread is a set of instructions that is executed in the computer CPU. It's where our code is executed in the machine processor._

"Concurrency Model" is how the Javascript Engine handles multiple tasks happening at the same time.

Why would we need the "concurrency model"?

Because **Javascript runs in one single-thread**, so it can only do **one thing at a time**.

So, what about a long-running task? A task that needs a really long time to conclude itself?

Sounds like it would block the single thread. However, we want non-blocking behaviour! We achieve that by using an **event loop**.

By using an event loop, it takes long-running tasks and **executes them in the "background" and puts them back in the main thread once they are finished**.

## Check the definition again

Should make sense now.

```
"Javascript is a high-level, prototype-based object-oriented, multi-paradigm,
interpreted or just-in-time compiled, dynamic, single-threaded,
gargabe-collected programming language with first-class functions and a
non-blocking event loop concurrecy model."
- Jonas Schmedtmann.
```

---

# PT: Vis??o Geral do JavaScript

O que ?? Javascript?

Nossa primeira defini????o era:

```
// (Tradu????o minha em PT, n??o do autor original)

"Javascript ?? uma linguagem de programa????o de alto-n??vel, orientada-a-objetos, multi-paradigm??tica."
- Jonas Schmedtmann.
```

Mas aqui vai outra defini????o:

```
// (Tradu????o minha em PT, n??o do autor original)

"Javascript ?? uma linguagem de programa????o de alto-n??vel,
orientada a objetos baseada em prot??tipos, multi-paradigm??tica,
interpretada ou rapidamente compilada, din??mica, de ??nico-fio
e coletora de lixo com fun????es de primeira-classe e um modelo
de simultaneidade com la??o de evento n??o-bloqueador."
- Jonas Schmedtmann.
```

Muita coisa.

Vamos quebrar a defini????o acima em pequenos peda??os e falar sobre eles.

## Alto-n??vel

Computadores precisam de hardware para trabalhar. As linguagens de baixo-n??vel lidam com os recursos de m??quina manualmente. A linguagem "C" ?? um exemplo. As linguagens de alto-n??vel n??o precisam lidar com os recursos de m??quina manualmente porque elas trabalham com abstra????es que retiram esse trabalho manual do usu??rio. Exemplos de linguagens de alto-n??vel s??o "Javascript" e "Python".

## Coletora-de-lixo

O "Coletor de Lixo" ?? um algoritmo dentro do motor Javascript que lida com os recursos de computador automaticamente ao "limpar" a mem??ria pra que n??o precisamos fazer isso manualmente.

## Interpretada ou rapidamente compilada

Computadores s?? entendem 1 e 0.

Todo programa precisa se converter em 1 e 0 para que as m??quinas possam entend??-lo. Isso significa que todo c??digo precisa ser traduzido para a m??quina em 1 e 0. Javascript lida com essa tradu????o internamente em seu Motor.

## Multi-paradigm??tica

Um paradigma ?? uma abordagem e mentalidade de estruturar c??digo, que direciona o seu estilo e suas t??cnicas de "codar".

S??o tr??s paradigmas populares:

1. **Programa????o procedural**: ?? o c??digo organizado com algumas fun????es nele. ?? o que temos feito e mostrado at?? agora (se voc?? seguir as anota????es pelos seus ??ndices).
2. **Programa????o orientada-a-objetos"** (poo)
3. **Programa????o funcional** (pf)

Javascript permite os tr??s paradigmas acima.

?? escolha do usu??rio escolher uma que seja melhor para o seu objetivo.

## Orientado-a-objetos baseada em prot??tipos

Vamos tomar um array que criamos em Javascript como exemplo.

Esse array "copia" a si mesmo de um Prot??tipo de Array que j?? est?? dispon??vel para c??pia. Esse prot??tipo tem suas propriedades e m??todos. Nosso array criado "herda" (de "heran??a" mesmo) essas propriedades e m??todos do prot??tipo.

Mais sobre isso nas anota????es ?? frente.

## Fun????es de primeira-classe

Fun????es s??o tratadas como vari??veis em Javascript. N??s podemos passar uma fun????o como argumento de outra fun????o, e tamb??m podemos retornar uma fun????o de outra fun????o.

_Isso permite a programa????o funcional acontecer._

## Din??mica

Lembra da tipagem din??mica? O Javascript ?? uma linguagem de tipagem din??mica. O tipo de dado de um valor em uma vari??vel pode ser automaticamente mudado.

## De fio-??nico

_Um fio ?? um conjunto de instru????es que ?? executado na CPU do computador. ?? onde o nosso c??digo ?? executado no processador da m??quina._

"Modelo de simultaneidade" ?? como o motor do Javascript lida com m??ltiplas atividades acontecendo ao mesmo tempo.

Por qu?? precisar??amos de um "modelo de simultaneidade"?

Porque Javascript **executa em um ??nico-fio**, ent??o ele s?? consegue **fazer uma coisa por vez**.

E uma atividade de longo-prazo? Uma atividade que precisasse de muito, muito tempo para ser conclu??da?

Para que isso bloquearia o fio ??nico. Entretanto, n??s queremos um comportamento de n??o-bloqueio desse fio ??nico! N??s conseguimos isso usando um **la??o de eventos**.

Ao usar um la??o de eventos, ele **executa uma atividade de longo-prazo "por baixo dos panos" e devolve a conclus??o ao fio principal depois que terminar de executar.**

## Olhe a defini????o de novo

Deve fazer sentido agora.

```
// (Tradu????o minha em PT, n??o do autor original)

"Javascript ?? uma linguagem de programa????o de alto-n??vel,
orientada a objetos baseada em prot??tipos, multi-paradigm??tica,
interpretada ou rapidamente compilada, din??mica, de ??nico-fio
e coletora de lixo com fun????es de primeira-classe e um modelo
de simultaneidade com la??o de evento n??o-bloqueador."
- Jonas Schmedtmann.
```
