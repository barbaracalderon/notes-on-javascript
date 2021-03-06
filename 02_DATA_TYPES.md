# EN: Data Types in JavaScript

## camelCase

Variables are written in `camelCase`.

You should consider some time to think about variable names.

## The 7 Primitive Data Types

| Data Type | About                                                                                                                                             | Typeof      |
| :-------- | :------------------------------------------------------------------------------------------------------------------------------------------------ | :---------- |
| Number    | Float pointing numbers. Used for decimals and integers                                                                                            | `number`    |
| String    | Sequence of characters. Used for text                                                                                                             | `string`    |
| Boolean   | `True` or `false`. Used for taking decision                                                                                                       | `boolean`   |
| Undefined | Value taken by a variable that is not yet defined (empty value)                                                                                   | `undefined` |
| Null      | Also means empty value                                                                                                                            | `object`\*  |
| Symbol    | Value that is unique and cannot be changed                                                                                                        | `symbol`    |
| BigInt    | Larger integers than the Number type can hold. To create a BigInt, simply append `n` to the end of the integer. Or use the `BigInt()` constructor | `bigint`    |
| `*`       | this is considered a bug in JS                                                                                                                    |

**REMEMBER**

JavaScript has _dynamic typing_. It automatically determines the data type of a value stored in a variable.

PS: Values have data types. Variables don't.

## Typeof

This is a reserved keyword that returns the type of a value stored in a variable when you call it.

---

# PT: Tipos de Dados em JavaScript

## camelCase

As vari??veis s??o escritas no estilo `camelCase`.

Importante considerar um tempo para pensar no nome das vari??veis.

## Os 7 Tipos Primitivos de Dados

| Tipo de Dado | Sobre                                                                                                                                                          | Typeof      |
| :----------- | :------------------------------------------------------------------------------------------------------------------------------------------------------------- | :---------- |
| Number       | N??meros de ponto flutuante. Usado para decimais e inteiros                                                                                                     | `number`    |
| String       | Sequ??ncia de caracteres. Usado para texto                                                                                                                      | `string`    |
| Boolean      | `True` ou `false`. Usado para tomada de decis??o                                                                                                                | `boolean`   |
| Undefined    | Valor tomado por uma vari??vel que ainda n??o foi definida (valor vazio)                                                                                         | `undefined` |
| Null         | Tamb??m significa valor vazio                                                                                                                                   | `object`\*  |
| Symbol       | Valor que ?? ??nico e n??o pode ser alterado                                                                                                                      | `symbol`    |
| BigInt       | Inteiros maiores que os suportados pelo `number`. Pra criar um valor do tipo BigInt, deve adicionar no final do n??mero um `n`. Ou usar o construtor `BigInt()` | `bigint`    |
| `*`          | ?? considerado um bug em JS                                                                                                                                     |

**LEMBRETE**

JavaScript tem **tipagem din??mica**. Ele automaticamente determina o tipo do dado de um valor contida em uma vari??vel.

PS: Valores tem tipagem de dado. Vari??veis n??o.

## Typeof

Palavra reservada que retorna o tipo de um valor armazenado em uma vari??vel quando voc?? a chama.
