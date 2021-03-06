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

Just as seen above. This is what makes modern Engines so fast. All this happens in special threads that we can't access from code: **completely separated from the main thread where we work in our code**.

### Runtime in the Browser

The engine alone is not enough. We need the Web APIs (DOM, timers, fetch API, others) also.

Web APIs are functionalities provided to the engines... they are not part of JS. The JS gets access to the web APIs through the **global window object**. The Runtime is like a box: it contains everything related to JS that we need.

What else do we need?

The **Callback Queue**.

This is a Data Structure that contains all the callback functions that are waiting to be executed.

For example, when we place an addEventListener in an HTML element on DOM. Suppose it waits for a "click" to happen ("onClick"). The "onClick" function is a callback function because it is waiting for an event to happen so it can be executed. The callback function is placed inside the **Callback Queue**. When the **Call Stack** (inside the Engine) is empty, the **Event Loop** takes the callback function _from inside_ the **Callback Queue** and _places it inside_ the **Call Stack** (inside the Engine).

The Event Loop is essential for the non-blocking concurrency model. It is a fundamental piece of JavaScript development.

_PS: The Runtime can also happen outside the browser, for example, in the Node.js. In this case, we say "Runtime in the Node.js". It's a bit different because Node.js does not have a browser, so it does not have the Web APIs. Instead, we have "C++ bindings & thread pool"._

## 2. Execution Context and the Call Stack

Let's imagine our code just finished compiling and is now ready to be executed. What happens now?

A **Global Execution Context** (GEC) for top-level code is created.

Exactly **one** GEC is created per program. It is the default context created for code that is not inside any function.

Top-level code is _code outside functions_. In the beginning, only code outside functions are executed and it makes sense: code inside functions are executed upon calling the function. An execution context is an environment in which a piece of JavaScript is executed - it stores all the necessary information for some code to be executed.

After the creation of a GEC, the following step is the **execution of top-level code** inside global Execution Context (EC).

And the final step is **execution of functions and waiting for callbacks**. One Execution Context (EC) is created per function - for **each** function call, a new execution context is created.

### Execution Context (EC) in detail

What is inside an EC?

Each EC has a variable environment, a scope chain and a "this" keyword.

| Items inside an EC               | Examples                                                                              | Is it also in Arrow Functions?                                       |
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
| Global Scope   | Top-level code: it resides outside any function or block code                                  | Variables declared here are accessible _everywhere_                                                                                                          |
| Function Scope | Also called local scope: it resides inside a function                                          | Variables declared here are accessible only inside the function (not outside it)                                                                             |
| Block Scope    | Everything inside curly braces (for example, "if" block, "for-loop" block, "while-loop" block, etc.) | Variables declared here are accessible only inside block (but this only applies to let and const variables). In `strict` mode, functions are also block scoped |

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

**The TDZ is the space from when the variable is called until it is actually defined in the code**. Why have it? Because it makes easier to avoid and catch errors -> being able to access variables before declaration is a bad practice and should be avoided. It makes const variables actually work.

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

### Never use Arrow Functions as Methods

You should never use an arrow function as a method. Precisely because of errors on "this" keyword.

## 6. Primitive Types vs. Reference Types (Objects)

This can cause a lot of confusion. It's important to understand how primitive types and reference types are stored in memory because they are radically different.

Remember the Engine? It consists basically of two important structures: the Call Stack and the Heap.

**Primitive types are stored in the Call Stack**. The variable points to an address in memory which, in turn, stores a value.

When we create another variable and replicate the first value to it, both variables point to the same address in memory. If we change one variable's value, then this variable will now point to another address in memory that holds the new value. The other variable will keep pointing to the previous memory address.

**Reference types (objects) are stored in the Heap**. The object points to an address in memory which, in turn, holds a value. _This value is a reference to a location in the Heap_ - that's why we call it "Reference" Types. But see? There's two steps here.

When we create another object by replicating a previous object to this new one, both objects point to the same address in memory which, in turn, points to a specific address in the Heap. If we change anything inside this object, regardless in which pointer (or name object), **the change is done in the Heap**. And it's only ONE object in the Heap, with two pointers to a memory address... which in turn points to this ONE object in the Heap.

That's why if we change an object property, it changes _apparently_ in both objects. That's because it's only one object but two pointers to the memory address in the Call Stack. The value in this memory address references to an address in the Heap _to the actual object stored in memory_. The object itself is not replicated, it's the same one, it's only one. The pointer is replicated. The reference is replicated. See the difference?

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

// Only NOW we can change a property value (lastName) without affecting the original Object (remember it would be the same object)
johnCopy.lastName = "Jones";

console.log("John Last Name: ", john.lastName); // > John Last Name: Smith
console.log("JohnCopy Last Name: ", johnCopy.lastName); // > JohnCopy Last Name: Jones
```

But, beware: **this Object.assign function only makes a shallow copy, not a deep clone**. To put this simply: if we had an object inside an object... it would not work. It would only make an actual copy on the first level (outer object).

Another way to make the same copies is using the Spread Operator. Check in the next files.

---

# PT: Como JavaScript Funciona por Tr??s dos Panos

O que ?? o Motor JavaScript e como se traduz JavaScript para c??digo de m??quina?

## Introdu????o

Nesse arquivo, vamos criar uma vis??o geral mais aprofudada de JavaScript. Leia o arquivo anterior, n.11, pra ter essa vis??o geral.

## 1. O Motor JavaScript e Tempo de Execu????o

O Motor JavaScript ?? um programa que **executa** o c??digo em JavaScript.

Todo navegador tem o seu Motor JavaScript. O motor mais famoso ?? aquele que vem com o Chrome: o V8 Engine. Essas anota????es levam esse motor em considera????o.

_Engine ?? Motor em ingl??s._

### Motor JavaScript

O Motor ?? feito de duas estruturas fundamentais: o **Call Stack** e o **Heap**.

Esses nomes, stack e heap, s??o tradicionais da ??rea de Estrutura de Dados. D?? pra traduzir como "Pilha" e "Amontoado", respectivamente. Pilha como em "pilha de pratos" e Amontoado como um "amontoado de brinquedos". Vou usar os termos em ingl??s.

O Call Stack ?? onde o nosso c??digo ?? executado: e o motor executa o c??digo usando o Contexto de Execu????o. O Heap ?? tipo uma estrutura de "piscina" que cont??m todos os objetos em mem??ria. ?? onde os objetos s??o guardados.

Como o c??digo ?? traduzido para C??digo de M??quina?

Pra responder isso, precisamos revisar as anota????es em Ci??ncia da Computa????o.

### Compila????o vs. Interpreta????o

**Compila????o** ?? o processo que o c??digo inteiro ?? **convertido para C??digo de M??quina de uma s?? vez** e escrito para um arquivo bin??rio que pode ser executado pelo computador. Ent??o, tem dois passos: primeiro, o c??digo ?? compilado (um arquivo port??vel ?? criado); segundo, o c??digo (agora c??digo de m??quina) ?? executado. Notinha: execu????o (passo 2) pode acontecer beeeeem depois da compila????o (passo 1). Ambos os passos mant??m o nosso programa funcionando.

**Interpreta????o** ?? o processo em que existe um **interpretador** que percorre o c??digo fonte e **executa linha por linha**. O c??digo ?? lido e executado ao mesmo tempo. Agora s?? tem um passo. Claro, o c??digo ainda precisa ser convertido para C??digo de M??quina mas isso ?? feito e executado no passo 1. As linguagens interpretadores s??o muito mais lentas que as linguagens compiladoras.

JavaScript j?? foi uma linguagem interpretadora. Mas agora n??o ?? mais: ?? uma linguaagem compiladora "just-in-time", que ?? uma mistura da op????o compiladora e interpretadora. Esse ?? o JavaScript moderno. O c??digo inteiro ?? convertido em C??digo de M??quina de uma vez e depois executado imediatamente. Tem dois passos aqui mas n??o existe arquivo port??vel.

_Just-in-time ?? uma express??o em ingl??s que, ao p?? da letra, significa "bem-em-tempo"._

### Motor Executa JS

Quatro passos.

**PARSE -> COMPILE -> EXECUTE -> OPTIMIZE**

Ou...

Analisar -> Compilar -> Executar -> Otimizar.

1. O primeiro passo ?? **analisar** o c??digo.

Isso significa que o motor l?? o c??digo e ele ?? analisado para uma estrutura de dado chamada Abstract Syntax Tree (AST, ou "??rvore de Sintaxe Abstrata"): cada peda??o do c??digo ?? separado de acordo com sua pr??pria categoria (const, functions, keywords) e salvo em uma estrutura de ??rvore.

_PS: essa ??rvore n??o tem nada a ver com o DOM, n??o s??o relacionados de nenhuma forma._

2. O segundo passo ?? **compilar** o c??digo.

Nesse passo, voc?? pega o arquivo AST e compila ele para c??digo de m??quina. Na sequ??ncia, esse c??digo ?? executado imediatamente (terceiro passo).

3. O terceiro passo ?? **executar** o c??digo.

Assim que o arquivo AST ?? compilado para c??digo de m??quina, ele ?? executado. Lembra a??, o Motor JavaScript funciona com a compila????o **just-in-time**. Essa execu????o acontece no Call Stack.

Aprofundando...

Pra conseguir fazer tudo de um jeito r??pido, o arquivo ?? compilado para uma vers??o n??o-otimizada de c??digo de m??quina, pra ser executado logo mesmo. Depois, ele entra nesse ciclo de otimiza????o do c??digo de m??quina... enquanto ele t?? rodando. Por baixo dos panos, esse c??digo ?? otimizado (melhorado) e compilado de novo, e de novo, e de novo para uma vers??o ??tima. Tudo acontece durante a execu????o!

4. O quarto passo ?? **otimizar** o c??digo, enquanto ele ?? executado.

Assim como descrito acima. ?? isso que faz os Motores serem t??o r??pidos hoje. Tudo isso acontece em threads (fios) especiais que n??o podemos acessar por meio do nosso c??digo: completamente separado da thread principal onde trabalhamos no nosso c??digo.

### Tempo de Execu????o no Navegador

O motor sozinho n??o ?? suficiente. Precisamos dos Web APIs (DOM, timers, fetch API, outros) tamb??m.

Web APIs s??o funcionalidades dispon??veis aos motores... eles n??o s??o parte do JS. O JS tem acesso aos Web APIs por meio da **global window object** (objeto janela global). O Tempo de Execu????o ?? como uma caixa: dentro dela tem tudo relacionado ao JS que ?? necess??rio.

O que mais precisamos?

Do **Callback Queue**.

Traduzindo ao p?? da letra, da "Fila de Ligue de Volta".

Essa ?? uma Estrutura de Dados que cont??m todas as fun????es de callback que est??o esperando para ser executadas.

Por exemplo, quando a gente coloca um addEventListener em um elemento HTML no DOM. Suponha que o elemento t?? esperando um "clique" acontece ("onClick"). A fun????o "onClick" ?? uma fun????o de callback porque t?? esperando por um evento acontecer pra ent??o ser executada. A fun????o callback ?? colocada dentro da Fila de Callbacks, ou **Callback Queue**. Quando o **Call Stack** (dentro do Motor) est?? vazio, o **Event Loop** leva a fun????o callback _de dentro_ da **Callback Queue** e _coloca dentro_ da **Call Stack** (dentro do Motor).

O Event Loop ?? essencial para o modelo de "non-blocking concurrency". ?? uma pe??a fundamental do desenvolvimento do JavaScript.

_PS: O Tempo de Execu????o tamb??m pode acontecer fora do navegador, por exemplo dentro do Node.js. Nesse caso, a gente diz "Tempo de Execu????o no Node.js". ?? um pouco diferente porque o Node.js n??o tem um navegador, ent??o n??o existe as Web APIs. No lugar, a gente tem "C++ bindings & thread pool"._

## 2. Contexto de Execu????o e o Call Stack

Vamos imaginar que o nosso c??digo acabou de compilar e agora t?? pronto pra ser executado. O que rola agora?

O **Contexto de Execu????o Global** (CEG) para c??digo alto-n??vel ?? criado.

Exatamente **um** CEG ?? criado por programa. ?? o contexto padr??o criado para c??digo que n??o est?? localizado dentro de nenhuma fun????o.

C??digo top-level (alto-n??vel) ?? o _c??digo fora das fun????es_. No come??o, s?? c??digo fora das fun????es ?? executado... e isso faz sentido: c??digo dentro da fun????o s?? ?? executado quando a fun????o ?? chamada. Um contexto de execu????o ?? um ambiente no qual um peda??o de JavaScript ?? executado - ele armazena todas as informa????es necess??rias sobre o c??digo a ser executado.

Depois da cria????o da CEG, o pr??ximo passo ?? a **execu????o do c??digo top-level** dentro do Contexto de Execu????o Global (CEG).

E o passo final ?? a **execu????o de fun????es e a espera por callbacks**. Um Contexto de Execu????o (CE) ?? criado por fun????o - para **cada** invoca????o de fun????o, um novo contexto de execu????o ?? criado.

### Contexto de Execu????o (CE) em detalhe

O que est?? dentro de um CE?

| Itens                | Exemplos                                                                          | Em Arrow Functions                                          |
| :------------------- | :-------------------------------------------------------------------------------- | :---------------------------------------------------------- |
| Ambiente da Vari??vel | declara????es de let, const e var; fun????es; objetos de argumento                    | N??O (para "objetos de argumento") e SIM (para todo o resto) |
| Cadeia de Escopos    | Basicamente s??o as refer??ncias para as vari??veis localizadas fora da fun????o atual | SIM                                                         |
| Palavra-chave "this" | Vem mais detalhes nesse arquivo                                                   | N??O                                                         |

Todos os tr??s, ambiente de vari??vel, cadeia de escopos e palavra-chave "this", s??o criados durante a "fase de cria????o" - bem antes da execu????o.

### Call Stack em detalhes

A Call Stack ?? o "lugar" em que CEs s??o empilhadas uma em cima das outras **para rastrear onde ?? que estamos na execu????o**.

## 3. Scoping e Escopo em JS: conceitos

Cada CE tem um ambiente da vari??vel, uma cadeia de escopos e a palavra-chave "this".

### Conceitos

**Scoping** controle como as vari??veis do programa s??o organizadas e acessadas.

**Escopo L??xico** ?? como o scoping ?? controlado por meio da **localiza????o** das fun????es e blocos no c??digo. Isso ?? influenciado por onde escrevemos no nosso c??digo.

**Escopo** ?? o espa??o ou ambiente no qual certas vari??veis s??o declaradas: tem o escopo global, escopo de fun????o e escopo de bloco.

**Escopo de uma vari??vel** ?? a regi????o no nosso c??digo em que uma certa vari??vel pode ser acessada.

S??o todas coisas diferentes.

## Escopo Global, Escopo da Fun????o e Escopo de Bloco

Uma tabela pra lembrar.

| Nome             | Em detalhes                                                                                    | Acessibilidade da vari??vel                                                                                                                                                              |
| :--------------- | :--------------------------------------------------------------------------------------------- | :-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Escopo Global    | C??digo top-level; reside fora de qualquer fun????o ou bloco de c??digo                            | Vari??veis declaradas s??o acessadas _de qualquer lugar_                                                                                                                                  |
| Escopo da Fun????o | Tamb??m chamado de escopo local; reside dentro de uma fun????o                                    | Vari??veis declaradas aqui s??o acess??veis apenas dentro da fun????o (e n??o fora dela)                                                                                                      |
| Escopo de Bloco  | Tudo que t?? entre as chaves (exemplo, um bloco if, um bloco for, um bloco de la??o while, etc.) | Vari??veis declaradas aqui s??o acess??veis apenas dentro do bloco (mas isso s?? se aplica a vari??veis declaradas com let e const). Em 'strict mode', fun????es tamb??m s??o de escopo de bloco |

_PS: vari??veis var apenas ligam pra escopo de fun????o e n??o escopo de bloco._

### Cadeia de Escopos

O procedimento para acessar uma vari??vel ?? chamado de "procurar uma vari??vel na cadeia de escopos". Cadeia aqui no sentido de "cadeia alimentar" mesmo. Isso significa que um escopo em particular tem acesso a vari??veis de todos os escopos mais de fora. O contr??rio n??o ?? verdade. **Aten????o nisso aqui**.

Voc?? consegue acessar o escopo-pai do escopo-atual mas n??o consegue acessar o escopo-filho do escopo-atual.

Importante notar: _`let` e `const` s??o ESCOPO DE BLOCO enquanto que o `var` ?? ESCOPO DE FUN????O._

A Cadeia de Escopos n??o tem nada a ver com **ordem** em que as fun????es s??o invocadas. A cadeia de escopos em um determinado escopo ?? igual a adicionar **todos os ambientes de vari??vel** de todos os escopos-pai.

## 4. Ambiente da Vari??vel: Hoisting e ZMT

Lembrando: EC ?? composto de "ambiente da vari??vel", "cadeia de escopos" e "palavra-chave this". Essa parte agora ?? sobre ambiente da vari??vel - especialmente sobre "hoisting" ("i??ando") e a Zona da Morte Temporal.

Como as vari??veis s??o criadas em JS?

Por meio do hoisting.

Hoisting faz alguns tipos de vari??veis acess??veis/us??veis no c??digo antes que eles sejam de fato declarados. Por baixo dos panos, o c??digo ?? escaneado para verificar declara????es de vari??veis, e para cada vari??vel uma nova propriedade ?? criada no objeto ambiente de vari??vel.

| O que                                  | Tem hoisting?                                              | Valor inicial                                   | Escopo                                          |
| :------------------------------------- | :--------------------------------------------------------- | :---------------------------------------------- | :---------------------------------------------- |
| Declara????o de fun????o                   | SIM                                                        | Fun????o atual                                    | Escopo de bloco (verdadeiro para 'strict mode') |
| Vari??veis var                          | SIM                                                        | undefined                                       | Escopo de fun????o                                |
| Vari??veis let e const                  | N??O - (tecnicamente sim mas n??o na pr??tica)                | \<uninitiallized>, Zona da Morte Temporal (ZMT) | Escopo de bloco                                 |
| Express??es de fun????o e Arrow functions | Depende de como foi declarado, se foi com var ou let/const | Depende                                         | Depende                                         |

A ZMT ?? o espa??o de quando uma vari??vel ?? invocada at?? quando ela ?? realmente definida no c??digo. Pra que ter isso? Porque torna mais f??cil evitar e pegar erros -> ser capaz de acessar vari??veis antes de declar??-las ?? uma m??-pr??tica e deve ser evitada. Isso torna as vari??veis const funcionarem.

Por que ter hoisting? Porque tornou fun????es ??teis antes da sua declara????o. O hoisting sobre o var ?? s?? um efeito-colateral.

## 5. A Palavra-chave "This"

Lembrando: EC ?? composto de "ambiente da vari??vel", "cadeia de escopos" e "palavra-chave this". Essa parte agora ?? sobre o ??ltimo ponto.

O que ?? o this?

`this` ?? uma vari??vel especial automaticamente **criada para cada Contexto de Execu????o (CE)**, que _inclui cada fun????o_. Essa vari??vel especial recebe o valor do "dono" da fun????o na qual a palavra-chave `this` ?? usada.

O valor da palavra-chave "this" **N??O ??** est??tico.

Ele muda.

Vai depender de **como** uma fun????o ?? invocada. Seu valor **s?? ?? atribu??do** quando a fun????o **??, de fato, chamada**. Isso ?? muito importante.

Tem quatro maneiras de chamar uma fun????o.

| Como chamar uma fun????o    | Significado                                               | Palavra-chave `this`                                                                                                                                   |
| :------------------------ | :-------------------------------------------------------- | :----------------------------------------------------------------------------------------------------------------------------------------------------- |
| Method                    | A fun????o ?? chamada dentro de um objeto, porque ?? um valor | `this` -> aponta para o Objeto que est?? chamando o m??todo                                                                                              |
| Simples chamada de fun????o | N??o est?? colada com nenhum objeto                         | `this` -> aponta para `undefined` no caso de usar 'strict mode'; ou aponta para o `window`, no caso de um navegador                                    |
| Arrow functions           | N??o ?? um jeito de chamar fun????o mas vale a pena mencionar | `this` -> aponta para a fun????o no entorno. A arrow function n??o usa o `this` para si, ent??o o `this` se refere a fun????o no entorno (?? o `this` l??xico) |
| Event Listener            | A rea????o para um evento                                   | `this` -> aponta para o elemento DOM no qual o EventListener est?? atrelado                                                                             |
| `new, call, apply, bind`  | Mais sobre isso nas pr??ximas anota????es                    | Vem mais a??                                                                                                                                            |

**Importante notar**: `this` n??o aponta para a fun????o em si e n??o aponta para o ambiente da vari??vel. Voc?? nunca deve usar uma arrow function como m??todo (fun????o dentro de objeto). Exatamente por causa dos erros que surgem com a palavra-chave "this".

## 6. Tipos Primitidos vs. Tipos Referenciados (Objetos)

Causa muita confus??o. ?? importante entender como os tipos primitivos e os tipos referenciados s??o guardados na mem??ria porque o jeito ?? bem diferente entre eles.

Lembra do motor? Feito de duas estruturas importantes: Call Stack e o Heap.

**Tipos Primitivos s??o guardados no Call Stack**. A vari??vel aponta para um endere??o de mem??ria que, por sua vez, guarda um valor.

Quando criamos uma outra vari??vel e replicados o valor da primeira vari??vel para ela, ambas vari??veis apontam para o mesmo endere??o de mem??ria. Se a gente muda o valor de uma das duas vari??veis, ent??o esse vari??vel agora vai apontar para outro endere??o de mem??ria que guarda um novo valor. A outra vari??vel continua apontando para o endere??o de mem??ria anterior.

**Tipos Referenciados (objetos) s??o guardados no Heap**. O objeto aponta para um endere??o de mem??ria que, por sua vez, guarda um valor. _Esse valor ?? uma refer??ncia para uma localidade no Heap_ - por isso que a gente chama de Tipos "Referenciados". Viu? Tem dois passos aqui.

Quando a gente cria outro objeto replicando o objeto anterior para esse novo, ambos objetos apontam para o mesmo endere??o de mem??ria que, por sua vez, aponta para um endere??o espec??fico no Heap. Se a gente muda qualquer coisa dentro desse objeto, n??o importa por meio de qual apontador (ou nome de objeto), **a mudan??a ?? feita no Heap**. E s?? tem UM objeto no Heap, com dois apontadores que apontam o endere??o de mem??ria... que por sua vez aponta para o endere??o desse ??NICO objeto no Heap.

?? por isso que se a gente muda uma propriedade de um objeto, ele muda _aparentemente_ em ambos os objetos - mas isso n??o ?? verdade. Isso acontece porque s?? existe um ??nico objeto com dois apontadores que apontam para o endere??o de mem??ria na Call Stack. O valor guardado por esta mem??ria na Call Stack referencia, por sua vez, um endere??o no Heap _para o objeto de fato guardado na mem??ria_. O objeto em si n??o ?? replicado, ?? o mesmo objeto, s?? existe um objeto. O apontador ?? replicado. Entende a diferen??a? Leia mais uma vez.

### Como copiar um objeto

Se voc?? quiser copiar um objeto para criar um novo, voc?? deve usar a fun????o `Object.assign({}, originalObject)`.

Veja o exemplo abaixo.

```javascript
// Objeto original ?? 'john'
const john = {
  firstName: "John",
  lastName: "Smith",
  age: 35,
};

// Vamos copiar o objeto 'john'
const johnCopy = Object.assign({}, john);

// S?? AGORA a gente pode mudar o valor da propriedade lastName sem
// afetar o objeto original (lembra que seria o mesmo objeto)
johnCopy.lastName = "Jones";

console.log("John Last Name: ", john.lastName); // > Smith
console.log("JohnCopy Last Name: ", johnCopy.lastName); // > Jones
```

Mas, cuidado: **essa fun????o Object.assign apenas faz uma c??pia rasa, n??o um clone profundo**. Sendo clara: se a gente tivesse um objeto dentro do objeto (por exemplo, um array dentro do objeto 'john' -> array ?? um objeto em JS)... n??o funcionaria essa c??pia. Apenas faria uma c??pia do primeiro n??vel (o objeto de fora, 'john').

Outra forma de fazer as mesmas c??pias ?? usar o Spread Operator. Olhar nos arquivos posteriores sobre ele.