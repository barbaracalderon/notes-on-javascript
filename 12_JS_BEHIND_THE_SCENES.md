# EN: How JavaScript Works Behind the Scenes

What is the JavaScript Engine and how is JavaScript translated to machine code?

## Introduction

In this file, we're going to build a deeper overview of JavaScript. Read the previous file, n. 11, to get the overview.

## 1. The Javascript Engine and Runtime

The JavaScript Engine is a program that **executes** JavaScript code.

Every browser has its own JavaScript Engine. The most famous Engine is the one from Chrome: the V8 Engine. These notes are taking it into consideration.

### JavaScript Engine

The Engine is made of two fundamental structures: the **Call Stack** and the **Heap**. The Call Stack is where our code is executed: and it executes the code using the execution context. The Heap is a data structure pool that contains all objects in memory. It's where the objects are stored.

How is it translated to Machine Code?

To answer that, we gotta review our notes on Computer Science.

### Compilation vs. Interpretation

**Compilation** is the process where the entire code is **converted to Machine Code at once** and written to a binary file that can be executed by the computer. So, there two steps: first, the code is compiled (a portable file is created); second, the code (now machine code) is executed. Sidenote: execution (step 2) can happen waaaay after compilation (step 1). Both steps get our program running.

**Interpretation** is the process where there is an **interpreter** that runs through the source code and **executes it line by line**. The code is read and executed at the same time. There's just one step now. Of course, code still needs to be converted to Machine Code but it is done and executed in one step. They are much slower than compiled languages.

JavaScript used to be an interpretation language. But now it is not: it's a "just-in-time" compilation language, which is a mixed option of compilation and interpretation. This is modern Javascript. The entire code is converted into machine code at once and then executed immediately. There are 2 steps here but with no portable file.

### Engine Executes JS

Four steps.

**PARSE -> COMPILE -> EXECUTE -> OPTIMIZE**

1. The first step is to **parse** the code.

Essentially, it means the engine reads the code and is parsed into an Abstract Syntax Tree (AST) data structure: each code bit is separated according to its own category (const, functions, keywords) and saved into a tree structure. _PS: this tree has nothing to do with the DOM, they're not related in any way_.

2. The second step is to **compile** the code.

In this step, you take the AST file and compile it to Machine Code. Then, this code is executed right away (third step).

3. The third step is to **execute** the code.

As soon as the AST file is compiled to Machine Code, it is then executed. Remember, Javascript Engine works with **just-in-time** compilation. This execution happens in the Call Stack.

But let's dig a little deeper.

In order to make it all so fast, the file is compiled to an un-optimized version of Machine Code, so it can be executed right away. Then, it enters this cicle to optimaze the Machine Code... as it runs along. In the background, this code is optimazide and compiled again and again to an optimized version. It all happens during execution!

4. So, the fourth step is to **optimize** the code, as it is executed.

Just as seen above. This is what makes modern Engines so fast. All this happens in special threads that we can't access from code: completely separated from the main thread where we work in our code.

### Runtime in the Browser

The engine alone is not enough. We need the Web APIs (DOM, timers, fetch API, others) also.

Web APIs are functionalities provided to the engines... they are not part of JS. The JS gets access to the web APIs through the **global window object**. The Runtime is like a box: it contains everything related to JS that we need.

What else do we need?

The **Callback Queue**.

This is a Data Structure that contains all the callback functions that are waiting to be executed.

For example, when we place an addEventListener in an HTML element on DOM. Suppose it waits for a "click" to happen ("onClick"). The "onClick" function is a callback function because it is waiting for an event to happen so it can be executed. The callback function is placed inside the **Callback Queue**. When the **Call Stack** (inside the Engine) is empty, the **Event Loop** takes the callback function _from inside_ the **Callback Queue** and _places it inside_ the **Call Stack** (inside the Engine).

The Event Loop is essential for the non-blocking concurrency model. It is a fundamental piece of JavaScript development.

_PS: The Runtime can also happen outside the browser, for example, in the Node.js. In this case, we say "Runtime in the Node.js". It's a bit differente because Node.js does not have a browser, so it does not have the Web APIs. Instead, we have "C++ bindings & thread pool"._

## 2. Execution Context and the Call Stack

Let's imagine our code just finished compiling and is now ready to be executed. What happens now?

A **Global Execution Context** (GEC) for top-level code is created.

Exactly **one** GEC is created per program. It is the default context created for code that is not inside any function.

Top-level code is _code outside functions_. In the beginning, only code outside functions are executed and it makes sense: code inside functions are executed upon calling the function. An execution context is an environment in which a piece of JavaScript is executed - it stores all the necessary information for some code to be executed.

After the creation of a GEC, the following step is the **execution of top-level code** inside global Execution Context (EC).

And the final step is **execution of functions and waiting for callbacks**. One Execution Context (EC) is created per function - for **each** function call, a new execution context is created.

### Execution Context (EC) in detail

What is inside an EC?

| Items                | Examples                                                                              | In Arrow Functions                                       |
| :------------------- | :------------------------------------------------------------------------------------ | :------------------------------------------------------- |
| Variable Environment | let, const and var declarations; functions; arguments objects                         | NO (to "arguments objects") and YES (to everything else) |
| Scope Chain          | Basically consists of references to variables located outside of the current function | YES                                                      |
| "This" Keyword       | More coming on this                                                                   | NO                                                       |

They are all created during the "creation phase" - right before execution.

### Call Stack in detail

The Call Stack is the "place" where ECs get stacked on top of each other to **keep track of where we are in the execution**.

## 3. Scoping and Scope in JS: concepts

Each EC has a variable environment, a scope chain and a "this" keyword.

### Concepts

**Scoping** controls how our programs' variables are organized and accessed.

**Lexical Scoping** is how scoping is controlled by **placement** of functions and blocks in the code. This is influenced by where we write in our code.

**Scope** is the space or environment in which a certain variable is declared: there is global scope, function scope and block scope.

**Scope of a variable** is the region of our code where a certain variable can be accessed.

They are all different things.

### Global Scope, Function Scope and Block Scope

Here's a table to remember.

| Name           | In details                                                                                     | Variables accessibility                                                                                                                                      |
| :------------- | :--------------------------------------------------------------------------------------------- | :----------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Global Scope   | Top-level code; it resides outside any function or block code                                  | Variables declared here are accessible _everywhere_                                                                                                          |
| Function Scope | Also called local scope; it resides inside a function                                          | Variables declared here are accessible only inside the function (not outside it)                                                                             |
| Block Scope    | Everything inside curly braces (for example, if block, for loop block, while loop block, etc.) | Variables declared here are accessible only inside block (but this only applies to let and const variables). In strict mode, functions are also block scoped |

_PS: var variables only care about function scope and not block scope._

### Scope Chain

The procedure to access a variable is called "variable lookup in scope chain" which, in turn, means that a particular scope has access to variables from all **outer** scopes. The reverse is not true, though. **Pay attention to this**.

You access the parent-scope related to current-scope but not the child-scope of current-scope.

Important to note: _`let` and `const` are BLOCK-SCOPED while `var` is FUNCTION-SCOPED._

The Scope Chain has nothing to do with the **order** in which functions are called. The Scope Chain in a certain scope is equal to adding together **all the variable environments** of the all parent-scopes.

## 4. Variable Environment: Hoisting and TDZ

Remember: EC contains "variable environment", "scope chain" and "this keyword". This section is about variable environment - specifically on hoisting and the Temporal Dead Zone (TDZ).

How are variables created in JS?

Through hoisting.

Hoisting makes some types of variables accessible/usable in the code before they are actually declared. Behind the scenes, the code is scanned for variable declarations, and for each variable a new property is created in the variable environment object.

| What                                     | Hoisted?                                   | Initial Value                              | Scope                                |
| :--------------------------------------- | :----------------------------------------- | :----------------------------------------- | :----------------------------------- |
| Function declarations                    | YES                                        | Actual function                            | Block scope (true for 'strict mode') |
| Var variables                            | YES                                        | undefined                                  | Function scope                       |
| let and const variables                  | NO - (technically yes but not in practice) | \<unintiallized>, Temporal Dead Zone (TDZ) | Block scope                          |
| Function expressions and Arrow functions | Depends if declared with var or let/const  | Depends                                    | Depends                              |

The TDZ is the space from when the variable is called until it is actually defined in the code. Why have it? Because it makes easier to avoid and catch errors -> being able to access variables before declaration is a bad practice and should be avoided. It makes const variables actually work.

Why have hoisting? Because it made functions useful before actual declaration. The var hoisting is just a byproduct.

## 5. The "This" Keyword

Remember: EC contains "variable environment", "scope chain" and "this keyword". This section is about "this" keyword, a very special variable in JS.

What is it?

`this` is a special variable automatically **created for every Execution Context** (EC), which _includes every function_. This special variable takes the value of the "owner" of the function in which `this` keyword is used.

The value of "this" keyword **is NOT** static.

It changes.

It depends on **how** the function is called. Its value is **only assigned** when the function **is actually called**. This is very important.

So, how can a function be called then? Because this is important.

There are four ways.

| How to call a Function   | Meaning                                                             | `this` keyword                                                                                                                                              |
| :----------------------- | :------------------------------------------------------------------ | :---------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Method                   | A function is called inside an object, because it's an object value | `this` -> points to the Object that is calling the method                                                                                                   |
| Simple function call     | Not attached to any object                                          | `this` -> points to `undefined` in case of 'strict mode'; or it points to `window` (in the browser)                                                         |
| Arrow functions          | Not a way to call functions but important to mention                | `this` -> points to surrounding function. They don't use the `this` keyword themselves, so the `this` keyword refers to surrounding function (lexical this) |
| Event Listener           | The reaction to an event                                            | `this` -> points to DOM element that the handler is attached to                                                                                             |
| `new, call, apply, bind` | More coming in next notes                                           | More to come                                                                                                                                                |

**Important to note**: `this` does not point to the function itself and does not point to its variable environment.

You should never use an arrow function as a method. Precisely because of errors on "this" keyword.

## 6. Primitive Types vs. Reference Types (Objects)

This can cause a lot of confusion. It's important to understand how primitive types and reference types are stored in memory because they are radically different.

Remember the Engine? It consists basically of two important structures: the Call Stack and the Heap.

**Primitive types are stored in the Call Stack**. The variable points to an address in memory which, in turn, stores a value.

When we create another variable and replicates the first value to it, both variables point to the same address in memory. If we change one variable's value, then this variable will now point to another address in memory that holds the new value. The other variable will keep pointing to the previous memory address.

**Reference types (objects) are stored in the Heap**. The object points to an address in memory which, in turn, holds a value. _This value is a reference to a location in the Heap_ - that's why we call it "Reference" Types. But see? There's two steps here.

When we create another object by replicating a previous object to this new one, both objects point to the same address in memory which, in turn, points to a specific address in the Heap. If we change anything inside this object, regardless in which pointer (or name object), **the change is done in the Heap**. And it's only ONE object in the Heap, with two pointers to a memory address... which in turn points to this ONE object in the Heap.

That's why if we change an object property, it changes _apparently_ in both objects. That's because it's only one object but two pointers to the memory address in the Call Stack. The value in this memory address references to an address in the Heap _to the actual object stored in memory_. The object itself is not replicated, it's the same one, it's only one. The pointer is replicated. See the difference?

### How to copy an object

If you want to copy an object to create a new one, you should use the `Object.assign({}, originalObject)` function.

Check out the example below.

```javascript
// Original object is 'john'
const john = {
  firstName: "John",
  lastName: "Smith",
  age: 35,
};

// Let's copy the 'john' object
const johnCopy = Object.assign({}, john);

// Only NOW we can now change a property value (lastName) without
// affecting the original Object (remember it would be the same object)
johnCopy.lastName = "Jones";

console.log("John Last Name: ", john.lastName); // > Smith
console.log("JohnCopy Last Name: ", johnCopy.lastName); // > Jones
```

But, beware: **this Object.assign function only makes a shallow copy, not a deep clone**. To put this simply: if we had an object inside an object... it would not work. It would only make an actual copy on the first level (outer object).

Another way to make the same copies is using the Spread Operator. Check in the next files.

---

# PT: Como JavaScript Funciona por Trás dos Panos

O que é o Motor JavaScript e como se traduz JavaScript para código de máquina?

## Introdução

Nesse arquivo, vamos criar uma visão geral mais aprofudada de JavaScript. Leia o arquivo anterior, n.11, pra ter essa visão geral.

## 1. O Motor JavaScript e Tempo de Execução

O Motor JavaScript é um programa que **executa** o código em JavaScript.

Todo navegador tem o seu Motor JavaScript. O motor mais famoso é aquele que vem com o Chrome: o V8 Engine. Essas anotações levam esse motor em consideração.

_Engine é Motor em inglês._

### Motor JavaScript

O Motor é feito de duas estruturas fundamentais: o **Call Stack** e o **Heap**.

Esses nomes, stack e heap, são tradicionais da área de Estrutura de Dados. Dá pra traduzir como "Pilha" e "Amontoado", respectivamente. Pilha como em "pilha de pratos" e Amontoado como um "amontoado de brinquedos". Vou usar os termos em inglês.

O Call Stack é onde o nosso código é executado: e o motor executa o código usando o Contexto de Execução. O Heap é tipo uma estrutura de "piscina" que contém todos os objetos em memória. É onde os objetos são guardados.

Como o código é traduzido para Código de Máquina?

Pra responder isso, precisamos revisar as anotações em Ciência da Computação.

### Compilação vs. Interpretação

**Compilação** é o processo que o código inteiro é **convertido para Código de Máquina de uma só vez** e escrito para um arquivo binário que pode ser executado pelo computador. Então, tem dois passos: primeiro, o código é compilado (um arquivo portável é criado); segundo, o código (agora código de máquina) é executado. Notinha: execução (passo 2) pode acontecer beeeeem depois da compilação (passo 1). Ambos os passos mantém o nosso programa funcionando.

**Interpretação** é o processo em que existe um **interpretador** que percorre o código fonte e **executa linha por linha**. O código é lido e executado ao mesmo tempo. Agora só tem um passo. Claro, o código ainda precisa ser convertido para Código de Máquina mas isso é feito e executado no passo 1. As linguagens interpretadores são muito mais lentas que as linguagens compiladoras.

JavaScript já foi uma linguagem interpretadora. Mas agora não é mais: é uma linguaagem compiladora "just-in-time", que é uma mistura da opção compiladora e interpretadora. Esse é o JavaScript moderno. O código inteiro é convertido em Código de Máquina de uma vez e depois executado imediatamente. Tem dois passos aqui mas não existe arquivo portável.

_Just-in-time é uma expressão em inglês que, ao pé da letra, significa "bem-em-tempo"._

### Motor Executa JS

Quatro passos.

**PARSE -> COMPILE -> EXECUTE -> OPTIMIZE**

Ou...

Analisar -> Compilar -> Executar -> Otimizar.

1. O primeiro passo é **analisar** o código.

Isso significa que o motor lê o código e ele é analisado para uma estrutura de dado chamada Abstract Syntax Tree (AST, ou "Árvore de Sintaxe Abstrata"): cada pedaço do código é separado de acordo com sua própria categoria (const, functions, keywords) e salvo em uma estrutura de árvore.

_PS: essa árvore não tem nada a ver com o DOM, não são relacionados de nenhuma forma._

2. O segundo passo é **compilar** o código.

Nesse passo, você pega o arquivo AST e compila ele para código de máquina. Na sequência, esse código é executado imediatamente (terceiro passo).

3. O terceiro passo é **executar** o código.

Assim que o arquivo AST é compilado para código de máquina, ele é executado. Lembra aí, o Motor JavaScript funciona com a compilação **just-in-time**. Essa execução acontece no Call Stack.

Aprofundando...

Pra conseguir fazer tudo de um jeito rápido, o arquivo é compilado para uma versão não-otimizada de código de máquina, pra ser executado logo mesmo. Depois, ele entra nesse ciclo de otimização do código de máquina... enquanto ele tá rodando. Por baixo dos panos, esse código é otimizado (melhorado) e compilado de novo, e de novo, e de novo para uma versão ótima. Tudo acontece durante a execução!

4. O quarto passo é **otimizar** o código, enquanto ele é executado.

Assim como descrito acima. É isso que faz os Motores serem tão rápidos hoje. Tudo isso acontece em threads (fios) especiais que não podemos acessar por meio do nosso código: completamente separado da thread principal onde trabalhamos no nosso código.

### Tempo de Execução no Navegador

O motor sozinho não é suficiente. Precisamos dos Web APIs (DOM, timers, fetch API, outros) também.

Web APIs são funcionalidades disponíveis aos motores... eles não são parte do JS. O JS tem acesso aos Web APIs por meio da **global window object** (objeto janela global). O Tempo de Execução é como uma caixa: dentro dela tem tudo relacionado ao JS que é necessário.

O que mais precisamos?

Do **Callback Queue**.

Traduzindo ao pé da letra, da "Fila de Ligue de Volta".

Essa é uma Estrutura de Dados que contém todas as funções de callback que estão esperando para ser executadas.

Por exemplo, quando a gente coloca um addEventListener em um elemento HTML no DOM. Suponha que o elemento tá esperando um "clique" acontece ("onClick"). A função "onClick" é uma função de callback porque tá esperando por um evento acontecer pra então ser executada. A função callback é colocada dentro da Fila de Callbacks, ou **Callback Queue**. Quando o **Call Stack** (dentro do Motor) está vazio, o **Event Loop** leva a função callback _de dentro_ da **Callback Queue** e _coloca dentro_ da **Call Stack** (dentro do Motor).

O Event Loop é essencial para o modelo de "non-blocking concurrency". É uma peça fundamental do desenvolvimento do JavaScript.

_PS: O Tempo de Execução também pode acontecer fora do navegador, por exemplo dentro do Node.js. Nesse caso, a gente diz "Tempo de Execução no Node.js". É um pouco diferente porque o Node.js não tem um navegador, então não existe as Web APIs. No lugar, a gente tem "C++ bindings & thread pool"._

## 2. Contexto de Execução e o Call Stack

Vamos imaginar que o nosso código acabou de compilar e agora tá pronto pra ser executado. O que rola agora?

O **Contexto de Execução Global** (CEG) para código alto-nível é criado.

Exatamente **um** CEG é criado por programa. É o contexto padrão criado para código que não está localizado dentro de nenhuma função.

Código top-level (alto-nível) é o _código fora das funções_. No começo, só código fora das funções é executado... e isso faz sentido: código dentro da função só é executado quando a função é chamada. Um contexto de execução é um ambiente no qual um pedaço de JavaScript é executado - ele armazena todas as informações necessárias sobre o código a ser executado.

Depois da criação da CEG, o próximo passo é a **execução do código top-level** dentro do Contexto de Execução Global (CEG).

E o passo final é a **execução de funções e a espera por callbacks**. Um Contexto de Execução (CE) é criado por função - para **cada** invocação de função, um novo contexto de execução é criado.

### Contexto de Execução (CE) em detalhe

O que está dentro de um CE?

| Itens                | Exemplos                                                                          | Em Arrow Functions                                          |
| :------------------- | :-------------------------------------------------------------------------------- | :---------------------------------------------------------- |
| Ambiente da Variável | declarações de let, const e var; funções; objetos de argumento                    | NÃO (para "objetos de argumento") e SIM (para todo o resto) |
| Cadeia de Escopos    | Basicamente são as referências para as variáveis localizadas fora da função atual | SIM                                                         |
| Palavra-chave "this" | Vem mais detalhes nesse arquivo                                                   | NÃO                                                         |

Todos os três, ambiente de variável, cadeia de escopos e palavra-chave "this", são criados durante a "fase de criação" - bem antes da execução.

### Call Stack em detalhes

A Call Stack é o "lugar" em que CEs são empilhadas uma em cima das outras **para rastrear onde é que estamos na execução**.

## 3. Scoping e Escopo em JS: conceitos

Cada CE tem um ambiente da variável, uma cadeia de escopos e a palavra-chave "this".

### Conceitos

**Scoping** controle como as variáveis do programa são organizadas e acessadas.

**Escopo Léxico** é como o scoping é controlado por meio da **localização** das funções e blocos no código. Isso é influenciado por onde escrevemos no nosso código.

**Escopo** é o espaço ou ambiente no qual certas variáveis são declaradas: tem o escopo global, escopo de função e escopo de bloco.

**Escopo de uma variável** é a regição no nosso código em que uma certa variável pode ser acessada.

São todas coisas diferentes.

## Escopo Global, Escopo da Função e Escopo de Bloco

Uma tabela pra lembrar.

| Nome             | Em detalhes                                                                                    | Acessibilidade da variável                                                                                                                                                              |
| :--------------- | :--------------------------------------------------------------------------------------------- | :-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Escopo Global    | Código top-level; reside fora de qualquer função ou bloco de código                            | Variáveis declaradas são acessadas _de qualquer lugar_                                                                                                                                  |
| Escopo da Função | Também chamado de escopo local; reside dentro de uma função                                    | Variáveis declaradas aqui são acessíveis apenas dentro da função (e não fora dela)                                                                                                      |
| Escopo de Bloco  | Tudo que tá entre as chaves (exemplo, um bloco if, um bloco for, um bloco de laço while, etc.) | Variáveis declaradas aqui são acessíveis apenas dentro do bloco (mas isso só se aplica a variáveis declaradas com let e const). Em 'strict mode', funções também são de escopo de bloco |

_PS: variáveis var apenas ligam pra escopo de função e não escopo de bloco._

### Cadeia de Escopos

O procedimento para acessar uma variável é chamado de "procurar uma variável na cadeia de escopos". Cadeia aqui no sentido de "cadeia alimentar" mesmo. Isso significa que um escopo em particular tem acesso a variáveis de todos os escopos mais de fora. O contrário não é verdade. **Atenção nisso aqui**.

Você consegue acessar o escopo-pai do escopo-atual mas não consegue acessar o escopo-filho do escopo-atual.

Importante notar: _`let` e `const` são ESCOPO DE BLOCO enquanto que o `var` é ESCOPO DE FUNÇÃO._

A Cadeia de Escopos não tem nada a ver com **ordem** em que as funções são invocadas. A cadeia de escopos em um determinado escopo é igual a adicionar **todos os ambientes de variável** de todos os escopos-pai.

## 4. Ambiente da Variável: Hoisting e ZMT

Lembrando: EC é composto de "ambiente da variável", "cadeia de escopos" e "palavra-chave this". Essa parte agora é sobre ambiente da variável - especialmente sobre "hoisting" ("içando") e a Zona da Morte Temporal.

Como as variáveis são criadas em JS?

Por meio do hoisting.

Hoisting faz alguns tipos de variáveis acessíveis/usáveis no código antes que eles sejam de fato declarados. Por baixo dos panos, o código é escaneado para verificar declarações de variáveis, e para cada variável uma nova propriedade é criada no objeto ambiente de variável.

| O que                                  | Tem hoisting?                                              | Valor inicial                                   | Escopo                                          |
| :------------------------------------- | :--------------------------------------------------------- | :---------------------------------------------- | :---------------------------------------------- |
| Declaração de função                   | SIM                                                        | Função atual                                    | Escopo de bloco (verdadeiro para 'strict mode') |
| Variáveis var                          | SIM                                                        | undefined                                       | Escopo de função                                |
| Variáveis let e const                  | NÃO - (tecnicamente sim mas não na prática)                | \<uninitiallized>, Zona da Morte Temporal (ZMT) | Escopo de bloco                                 |
| Expressões de função e Arrow functions | Depende de como foi declarado, se foi com var ou let/const | Depende                                         | Depende                                         |

A ZMT é o espaço de quando uma variável é invocada até quando ela é realmente definida no código. Pra que ter isso? Porque torna mais fácil evitar e pegar erros -> ser capaz de acessar variáveis antes de declará-las é uma má-prática e deve ser evitada. Isso torna as variáveis const funcionarem.

Por que ter hoisting? Porque tornou funções úteis antes da sua declaração. O hoisting sobre o var é só um efeito-colateral.

## 5. A Palavra-chave "This"

Lembrando: EC é composto de "ambiente da variável", "cadeia de escopos" e "palavra-chave this". Essa parte agora é sobre o último ponto.

O que é o this?

`this` é uma variável especial automaticamente **criada para cada Contexto de Execução (CE)**, que _inclui cada função_. Essa variável especial recebe o valor do "dono" da função na qual a palavra-chave `this` é usada.

O valor da palavra-chave "this" **NÃO É** estático.

Ele muda.

Vai depender de **como** uma função é invocada. Seu valor **só é atribuído** quando a função **é, de fato, chamada**. Isso é muito importante.

Tem quatro maneiras de chamar uma função.

| Como chamar uma função    | Significado                                               | Palavra-chave `this`                                                                                                                                   |
| :------------------------ | :-------------------------------------------------------- | :----------------------------------------------------------------------------------------------------------------------------------------------------- |
| Method                    | A função é chamada dentro de um objeto, porque é um valor | `this` -> aponta para o Objeto que está chamando o método                                                                                              |
| Simples chamada de função | Não está colada com nenhum objeto                         | `this` -> aponta para `undefined` no caso de usar 'strict mode'; ou aponta para o `window`, no caso de um navegador                                    |
| Arrow functions           | Não é um jeito de chamar função mas vale a pena mencionar | `this` -> aponta para a função no entorno. A arrow function não usa o `this` para si, então o `this` se refere a função no entorno (é o `this` léxico) |
| Event Listener            | A reação para um evento                                   | `this` -> aponta para o elemento DOM no qual o EventListener está atrelado                                                                             |
| `new, call, apply, bind`  | Mais sobre isso nas próximas anotações                    | Vem mais aí                                                                                                                                            |

**Importante notar**: `this` não aponta para a função em si e não aponta para o ambiente da variável. Você nunca deve usar uma arrow function como método (função dentro de objeto). Exatamente por causa dos erros que surgem com a palavra-chave "this".

## 6. Tipos Primitidos vs. Tipos Referenciados (Objetos)

Causa muita confusão. É importante entender como os tipos primitivos e os tipos referenciados são guardados na memória porque o jeito é bem diferente entre eles.

Lembra do motor? Feito de duas estruturas importantes: Call Stack e o Heap.

**Tipos Primitivos são guardados no Call Stack**. A variável aponta para um endereço de memória que, por sua vez, guarda um valor.

Quando criamos uma outra variável e replicados o valor da primeira variável para ela, ambas variáveis apontam para o mesmo endereço de memória. Se a gente muda o valor de uma das duas variáveis, então esse variável agora vai apontar para outro endereço de memória que guarda um novo valor. A outra variável continua apontando para o endereço de memória anterior.

**Tipos Referenciados (objetos) são guardados no Heap**. O objeto aponta para um endereço de memória que, por sua vez, guarda um valor. _Esse valor é uma referência para uma localidade no Heap_ - por isso que a gente chama de Tipos "Referenciados". Viu? Tem dois passos aqui.

Quando a gente cria outro objeto replicando o objeto anterior para esse novo, ambos objetos apontam para o mesmo endereço de memória que, por sua vez, aponta para um endereço específico no Heap. Se a gente muda qualquer coisa dentro desse objeto, não importa por meio de qual apontador (ou nome de objeto), **a mudança é feita no Heap**. E só tem UM objeto no Heap, com dois apontadores que apontam o endereço de memória... que por sua vez aponta para o endereço desse ÚNICO objeto no Heap.

É por isso que se a gente muda uma propriedade de um objeto, ele muda _aparentemente_ em ambos os objetos - mas isso não é verdade. Isso acontece porque só existe um único objeto com dois apontadores que apontam para o endereço de memória na Call Stack. O valor guardado por esta memória na Call Stack referencia, por sua vez, um endereço no Heap _para o objeto de fato guardado na memória_. O objeto em si não é replicado, é o mesmo objeto, só existe um objeto. O apontador é replicado. Entende a diferença? Leia mais uma vez.

### Como copiar um objeto

Se você quiser copiar um objeto para criar um novo, você deve usar a função `Object.assign({}, originalObject)`.

Veja o exemplo abaixo.

```javascript
// Objeto original é 'john'
const john = {
  firstName: "John",
  lastName: "Smith",
  age: 35,
};

// Vamos copiar o objeto 'john'
const johnCopy = Object.assign({}, john);

// Só AGORA a gente pode mudar o valor da propriedade lastName sem
// afetar o objeto original (lembra que seria o mesmo objeto)
johnCopy.lastName = "Jones";

console.log("John Last Name: ", john.lastName); // > Smith
console.log("JohnCopy Last Name: ", johnCopy.lastName); // > Jones
```

Mas, cuidado: **essa função Object.assign apenas faz uma cópia rasa, não um clone profundo**. Sendo clara: se a gente tivesse um objeto dentro do objeto (por exemplo, um array dentro do objeto 'john' -> array é um objeto em JS)... não funcionaria essa cópia. Apenas faria uma cópia do primeiro nível (o objeto de fora, 'john').

Outra forma de fazer as mesmas cópias é usar o Spread Operator. Olhar nos arquivos posteriores sobre ele.