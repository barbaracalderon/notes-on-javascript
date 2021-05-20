# EN: Data Types in JavaScript

## camelCase
Variables are written in ```camelCase```.

You should consider some time to think about variable names. 

## The 7 Primitive Data Types

Data Type | About | Typeof
:--------- | :----- | :-------
Number | Float pointing numbers. Used for decimals and integers | ```number```
String | Sequence of characters. Used for text | ```string```
Boolean | ```True``` or ```false```. Used for taking decision | ```boolean```
Undefined | Value taken by a variable that is not yet defined (empty value) | ```undefined```
Null | Also means empty value | ```object```*
Symbol | Value that is unique and cannot be changed | ```symbol```
BigInt | Larger integers than the Number type can hold. To create a BigInt, simply append ```n``` to the end of the integer. Or use the ```BigInt()``` constructor | ```bigint```
```*```| this is considered a bug in JS

**REMEMBER**

JavaScript has *dynamic typing*. It automatically determines the data type of a value stored in a variable.

PS: Values have data types. Variables don't.

## Typeof

This is a reserved keyword that returns the type of a value stored in a variable when you call it.

---
---

# PT: Tipos de Dados em JavaScript

## camelCase
As variáveis são escritas no estilo ```camelCase```.

Importante considerar um tempo para pensar no nome das variáveis. 

## Os 7 Tipos Primitivos de Dados

Tipo de Dado | Sobre | Typeof
:----------- | :---- | :----------
Number | Números de ponto flutuante. Usado para decimais e inteiros | ```number```
String | Sequência de caracteres. Usado para texto | ```string```
Boolean | ```True``` ou ```false```. Usado para tomada de decisão | ```boolean```
Undefined | Valor tomado por uma variável que ainda não foi definida (valor vazio) | ```undefined```
Null | Também significa valor vazio | ```object```*
Symbol | Valor que é único e não pode ser alterado | ```symbol```
BigInt | Inteiros maiores que os suportados pelo ```number```. Pra criar um valor do tipo BigInt, deve adicionar no final do número um ```n```. Ou usar o construtor ```BigInt()``` | ```bigint```
```*```| é considerado um bug em JS

**LEMBRETE**

JavaScript tem **tipagem dinâmica**. Ele automaticamente determina o tipo do dado de um valor contida em uma variável.

PS: Valores tem tipagem de dado. Variáveis não.

## Typeof

Palavra reservada que retorna o tipo de um valor armazenado em uma variável quando você a chama.