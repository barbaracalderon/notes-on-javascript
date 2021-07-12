# EN: Notes on JavaScript

 These are my general notes on JavaScript. 
 
 It's like a notepad: useful to keep track of information and come back later to review and refresh my memory.

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
 # PT: Anotações sobre JavaScript

 Essas são as minhas anotações gerais sobre JavaScript.

 É como um caderno: útil para manter um registro das informações e voltar mais tarde para revisar e lembrar.

 *Sob construção.*

**TABELA DE CONTEÚDOS DO REPOSITÓRIO**

ARQUIVOS | CONTEÚDOS
:-------- | :----------
01_CONNECTJS.md | Conectar seu arquivo JS ao HTML
02_DATA_TYPES.md | ```number, string, boolean, undefined, null, symbol, bigInt```
03_OPERATORS.md | **Operadores**: matemáticos, de atribuição, relacionais, lógicos, ternários
04_CONVERSION_COERCION.md | Template string; string para número; número para string; tipagem forçada; valores falsy e truthy
05_SWITCH.md | Estrutura de um switch
06_FUNCTIONS.md | Ativar ```stric mode``` em JS; funções declarativas; funções expressivas; arrow functions; Função chamando Função
07_ARRAYS.md | Criando Arrays; Métodos do Array
08_OBJECTS.md | O que são Objetos em JS; par/valor; notação por ponto (```.```) e notação por colchete (```[]```); adicionar propriedades em um objeto; métodos do objeto; apresentando o ```this```;
09_LOOPS.md | laço ```for``` (contador); laçando um array; ler um array; preencher um array; continue vs. break; fazendo um laço ao contrário (de trás pra frente); laço dentro de laço; laço ```while``` (condição))
10_DOM.md | introdução; notas importantes PS; projeto [guess-my-number-game](https://github.com/barbaracalderon/guess-my-number-game); ```addEventListener```; lidando com eventos de clique; eventos de que tipo; reação (event handler) - uma função; nem sempre dá pra depender do DOM pra pegar variáveis de estado; variáveis de estado; manipulando CSS styles; projeto [modal-project-example](https://github.com/barbaracalderon/notes-on-javascript/tree/main/project-modal-example); manipulando classes com JS; evento global; pressionar a tecla 'ESC'; o ```querySelector``` e o ```querySelectorAll```; método toggle; função init; organização de código
11_JS_OVERVIEW.md | Definição de JavaScript; alto-nível; coleta-de-lixo; interpretada ou rapidamente compilada; multi-paradigmática; orientado-a-objetos baseada em protótipos; funções de primeira classe; dinâmica; de fio-único
12_JS_BEHIND_THE_SCENES | como Javascript funciona por baixo dos panos; o motor javascript e o tempo de execução; compilação vs. interpretação; como o Motor executa JS: os quatro passos (analisar -> compilar -> executar -> otimizar); tempo de execução no navegador; contexto de execução (CE) e a call stack; scoping e escopo em JS: escopo global, escopo da função, escopo de bloco; a cadeia de escopos; ambiente da variável: hoisting e a Zona da Morte Temporal (ZMT); a palavra-chave "this"; tipos primitivo vs. tipos referenciais (objetos); como copiar um objeto (cópia rasa, não uma clonagem profunda)
13_DESTRUCTURING.md | Arrays; Objetos
14_SPREAD_OPERATOR.md | O Operador Spreadd `...`; juntar dois arrays; copiar um array; iteráveis; operador spread sendo passado como parâmetro de uma função; copiar um objeto; cópias rasas
15_REST_PATTERN.md | o inverso do Operador Spread; REST na esquerda do sinal =; SPREAD à direita do sinal =; ambos os lados; objetos; funções do tipo "rest parameters"
16_SHORT_CIRCUITING_(AND_OR).md | operadores lógicos `\|\|` e `&&`; o operador "nullish coalescent" `??`
17_FOR_OF_LOOP.md | novo jeito de laçar um array; unir os menus; laçar por todos os menus; desempacotar menus
18_ENHANCED_OBJECT_LITERALS.md | oobjeto dentro de objeto; métodos de escrita; nome da propriedade vem de um array
19_OPTIONAL_CHAINGING.md | ...
Continua... | ...