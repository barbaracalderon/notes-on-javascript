# EN: Javascript Operators

They are divided into five categories.

The order of precedence is:

1. Math
2. Relational
3. Logical

## Math operators

| Operators | About                 |
| :-------- | :-------------------- |
| `+`       | Sum and concatenation |
| `-`       | Subtraction           |
| `*`       | Multiply              |
| `/`       | Divide                |
| `%`       | Module                |
| `**`      | Exponential           |

## Assignment operators

| Operators | About                        |
| :-------- | :--------------------------- |
| `=`       | Assigment                    |
| `+=`      | x = x + something            |
| `-=`      | x = x - something            |
| `*=`      | x = x \* something           |
| `++`      | Add one (increase by 1)      |
| `--`      | Subtract one (decrease by 1) |

## Comparison operators

| Operators | About                       |
| :-------- | :-------------------------- |
| `>`       | Greater than                |
| `<`       | Lesser than                 |
| `>=`      | Greater or equal than       |
| `<=`      | Lesser or equal than        |
| `==`      | Equal in value              |
| `===`     | Equal in value and in type  |
| `!=`      | Not equal in value          |
| `!==`     | Not equal in value nor type |

## Logical operators

| Operators | About  |
| :-------- | :----- |
| `!`       | Denial |
| `&&`      | `and`  |
| `\|\|`    | `or`   |

## Ternary operators

They are used in one single line. Like this:

```javascript
let profit = 1000;
let bonus = profit * (profit > 1000 ? 0.1 : 0.15);

/*The above line reads as follow:
If profit is greater than 1000, then multiply
it by 0.10; else multiply it by 0.15
Then, store the result inside variable 'bonus'*/
```

Another example.

```javascript
const drink = age >= 18 ? "wine" : "water";
// the result is stored in 'drink'
```

| Operators | About                                                        |
| :-------- | :----------------------------------------------------------- |
| `?`       | To make a decision                                           |
| `:`       | Separate `then` (first section) from `else` (second section) |

---

# PT: Operadores B??sicos do JavaScript

S??o divididos em cinco categorias.

A ordem de preced??ncia ??:

1. Matem??ticos
2. Relacionais
3. L??gicos

## Operadores matem??ticos

| Operadores | Sobre                     |
| :--------- | :------------------------ |
| `+`        | Soma e concatena????o       |
| `-`        | Subtra????o                 |
| `*`        | Multiplica????o             |
| `/`        | Divis??o                   |
| `%`        | M??dulo (resto da divis??o) |
| `**`       | Exponencia????o             |

## Operadores de atribui????o

| Operadores | Sobre                              |
| :--------- | :--------------------------------- |
| `=`        | Atribui????o                         |
| `+=`       | x = x + algo                       |
| `-=`       | x = x - algo                       |
| `*=`       | x = x \* algo                      |
| `++`       | Soma uma unidade (incrementa 1)    |
| `--`       | Diminui uma unidade (decrementa 1) |

## Operadores relacionais

| Operadores | Sobre                            |
| :--------- | :------------------------------- |
| `>`        | Maior que                        |
| `<`        | Menor que                        |
| `>=`       | Maior ou igual que               |
| `<=`       | Menor ou igual que               |
| `==`       | Igual em valor                   |
| `===`      | Igual em valor e tipagem         |
| `!=`       | N??o ?? igual em valor             |
| `!==`      | N??o ?? igual em valor nem tipagem |

## Operadores l??gicos

| Operadores | Sobre   |
| :--------- | :------ |
| `!`        | Nega????o |
| `&&`       | `e`     |
| `\|\|`     | `ou`    |

## Operadores tern??rios

S??o usados em uma ??nica linha. Tipo assim:

```javascript
let lucro = 1000;
let bonus = lucro * (lucro > 1000 ? 0.1 : 0.15);

/*A linha de cima ?? lida assim:
Se o lucro ?? maior que 1000, ent??o multiplique
ele por 0.10; sen??o, multiplique ele por 0.15
Depois, guarde o resultado na vari??vel 'bonus'*/
```

Outro exemplo.

```javascript
const drink = idade >= 18 ? "vinho" : "??gua";
// O resultado ?? guardado em 'drink'
```

| Operadores | Sobre                                                        |
| :--------- | :----------------------------------------------------------- |
| `?`        | Tomada de decis??o                                            |
| `:`        | Separa o `ent??o` (primeira parte) do `sen??o` (segunda parte) |
