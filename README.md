# EN: Notes on JavaScript

These are my general notes on JavaScript from "The Completete Javascript Course" by Jonas Schmedtmann. It's like a notepad to come back and review.

 *It's under construction.*

**THIS REPOSITORY'S TABLE OF CONTENTS**

 FILES | CONTENTS
:-------- | :----------
01_CONNECTJS.md | Connect your JS file to your HTML
02_DATA_TYPES.md | ```number, string, boolean, undefined, null, symbol, bigInt```
03_OPERATORS.md | Math operators, assignment operators, comparison operators, logic operators, ternary operators
04_CONVERSION_COERCION.md | Template string; string to number; number to string; type coercion; falsy values; truthy values
05_SWITCH.md | A switch structure
06_FUNCTIONS.md | Activate the ```stric mode``` in JS; function declaration; function expression; Arrow Function; function inside function
07_ARRAYS.md | Creating an array; array methods
08_OBJECTS.md | What are Objects in JS; value/pair; dot notation (```.```) and bracket notation (```[]```); to add properties to an object; object methods; introducing ```this```
09_LOOPS.md | ```for``` loop counter; loop through an array; read an array; fill an array; continue vs. break; looping backwards; loop in loops; ```while``` loop condition
10_DOM.md | introduction; import PS notes; [guess-my-number-game](https://github.com/barbaracalderon/guess-my-number-game) project; ```addEventListener```; handling click events; events of what kind; reaction (function); DOM not always reliable to grab state variables; manipulating CSS styles; [modal-project-example](https://github.com/barbaracalderon/notes-on-javascript/tree/main/project-modal-example); manipulate classes with JS; global events; press 'ESC'; ```querySelector``` and ```querySelectorAll```; the toggle method; Init function; code organization
11_JS_OVERVIEW.md | JavaScript definition; high-level; garbage-collected; interpreted or just-in-time compiled; multi-paradigm; prototype-based object oriented; first-class functions; dynamic; single-threaded
12_JS_BEHIND_THE_SCENES.md | how Javascript works behind the scenes; the javascript engine and runtime; compilation vs. interpretation; how the Engine executes JS: the four steps (parse -> compile -> execute -> optimize); runtime in the browser; execution context (EC) and the call stack; scoping and scope in JS: global scope, function scope, block scope; the scope chain; variable environment: hoisting and Temporal Dead Zone (TDZ); the "this" keyword; primitive types vs. reference types (objects); how to copy an object (shallow copy, not deep clone)
13_DESTRUCTURING.md | Destructuring Arrays and Objects
14_SPREAD_OPERATOR.md | `...`, join arrays, spread operator passed as a function parameter, objects
15_REST_PATTERN.md | What is rest pattern; compare Spread Operator and Rest Pattern; objects; functions
16_SHORT_CIRCUITING.md | `and` operator; `or` operator; the Nullish Coalescing Operator
17_FOR_OF_LOOP.md | new way to loop through an array; unite menus; loop thru all menus; unpack menus
18_ENHANCED_OBJECT_LITERALS.md | object inside object; writing methods; property name comes from an array
19_OPTIONAL_CHAINGING.md | ...
To be continued... | ...

 ---
 # PT: Anota????es sobre JavaScript

 Essas s??o as minhas anota????es gerais sobre JavaScript do curso "The Complete Javascript Course", Jonas Schmedtmann. Como um caderno para manter um registro das informa????es e voltar mais tarde para revisar.

 *Sob constru????o.*

**TABELA DE CONTE??DOS DO REPOSIT??RIO**

ARQUIVOS | CONTE??DOS
:-------- | :----------
01_CONNECTJS.md | Conectar seu arquivo JS ao HTML
02_DATA_TYPES.md | ```number, string, boolean, undefined, null, symbol, bigInt```
03_OPERATORS.md | **Operadores**: matem??ticos, de atribui????o, relacionais, l??gicos, tern??rios
04_CONVERSION_COERCION.md | Template string; string para n??mero; n??mero para string; tipagem for??ada; valores falsy e truthy
05_SWITCH.md | Estrutura de um switch
06_FUNCTIONS.md | Ativar ```stric mode``` em JS; fun????es declarativas; fun????es expressivas; arrow functions; Fun????o chamando Fun????o
07_ARRAYS.md | Criando Arrays; M??todos do Array
08_OBJECTS.md | O que s??o Objetos em JS; par/valor; nota????o por ponto (```.```) e nota????o por colchete (```[]```); adicionar propriedades em um objeto; m??todos do objeto; apresentando o ```this```;
09_LOOPS.md | la??o ```for``` (contador); la??ando um array; ler um array; preencher um array; continue vs. break; fazendo um la??o ao contr??rio (de tr??s pra frente); la??o dentro de la??o; la??o ```while``` (condi????o))
10_DOM.md | introdu????o; notas importantes PS; projeto [guess-my-number-game](https://github.com/barbaracalderon/guess-my-number-game); ```addEventListener```; lidando com eventos de clique; eventos de que tipo; rea????o (event handler) - uma fun????o; nem sempre d?? pra depender do DOM pra pegar vari??veis de estado; vari??veis de estado; manipulando CSS styles; projeto [modal-project-example](https://github.com/barbaracalderon/notes-on-javascript/tree/main/project-modal-example); manipulando classes com JS; evento global; pressionar a tecla 'ESC'; o ```querySelector``` e o ```querySelectorAll```; m??todo toggle; fun????o init; organiza????o de c??digo
11_JS_OVERVIEW.md | Defini????o de JavaScript; alto-n??vel; coleta-de-lixo; interpretada ou rapidamente compilada; multi-paradigm??tica; orientado-a-objetos baseada em prot??tipos; fun????es de primeira classe; din??mica; de fio-??nico
12_JS_BEHIND_THE_SCENES | como Javascript funciona por baixo dos panos; o motor javascript e o tempo de execu????o; compila????o vs. interpreta????o; como o Motor executa JS: os quatro passos (analisar -> compilar -> executar -> otimizar); tempo de execu????o no navegador; contexto de execu????o (CE) e a call stack; scoping e escopo em JS: escopo global, escopo da fun????o, escopo de bloco; a cadeia de escopos; ambiente da vari??vel: hoisting e a Zona da Morte Temporal (ZMT); a palavra-chave "this"; tipos primitivo vs. tipos referenciais (objetos); como copiar um objeto (c??pia rasa, n??o uma clonagem profunda)
13_DESTRUCTURING.md | Arrays; Objetos
14_SPREAD_OPERATOR.md | O Operador Spreadd `...`; juntar dois arrays; copiar um array; iter??veis; operador spread sendo passado como par??metro de uma fun????o; copiar um objeto; c??pias rasas
15_REST_PATTERN.md | o inverso do Operador Spread; REST na esquerda do sinal =; SPREAD ?? direita do sinal =; ambos os lados; objetos; fun????es do tipo "rest parameters"
16_SHORT_CIRCUITING_(AND_OR).md | operadores l??gicos `\|\|` e `&&`; o operador "nullish coalescent" `??`
17_FOR_OF_LOOP.md | novo jeito de la??ar um array; unir os menus; la??ar por todos os menus; desempacotar menus
18_ENHANCED_OBJECT_LITERALS.md | oobjeto dentro de objeto; m??todos de escrita; nome da propriedade vem de um array
19_OPTIONAL_CHAINGING.md | ...
Continua... | ...
