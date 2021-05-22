# EN: Javascript Operators

They are divided into five categories.

The order of precedence is:

1. Math
2. Relational
3. Logical

## Math operators

Operators | About
:-------- | :-----
```+``` | Sum and concatenation
```-``` | Subtraction
```*``` | Multiply
```/``` | Divide
```%``` | Module
```**``` | Exponential

## Assignment operators

Operators | About
:-------- | :-----
```=``` | Assigment
```+=``` | x = x + something
```-=``` | x = x - something
```*=``` | x = x * something
```++``` | Add one (increase by 1)
```--``` | Subtract one (decrease by 1)

## Comparison operators

Operators | About
:-------- | :-----
```>``` | Greater than
```<``` | Lesser than
```>=``` | Greater or equal than
```<=``` | Lesser or equal than
```==``` | Equal in value
```===``` | Equal in value and in type
```!=``` | Not equal in value
```!==``` | Not equal in value nor type

## Logical operators

Operators | About
:-------- | :-----
```!``` | Denial
```<``` | ```and```
```>=``` | ```or```

## Ternary operators

They are used in one single line. Like this:

```javascript
let profit = 1000;
let bonus = profit * (profit > 1000 ? 0.10 : 0.15)

/*The above line reads as follow:
If profit is greater than 1000, then multiply
it by 0.10; else multiply it by 0.15
Then, store the result inside variable 'bonus'*/
```

Another example.

```javascript
const drink = age >= 18 ? 'wine' : 'water';
// the result is stored in 'drink'
```

Operators | About
:-------- | :-----
```?``` | To make a decision
```:``` | Separate ```then``` (first section) from ```else``` (second section)

---
---
# PT: Operadores Básicos do JavaScript

São divididos em cinco categorias.

A ordem de precedência é:

1. Matemáticos
2. Relacionais
3. Lógicos

## Operadores matemáticos

Operadores| Sobre
:-------- | :-----
```+``` | Soma e concatenação
```-``` | Subtração
```*``` | Multiplicação
```/``` | Divisão
```%``` | Módulo (resto da divisão)
```**``` | Exponenciação

## Operadores de atribuição

Operadores | Sobre
:-------- | :-----
```=``` | Atribuição
```+=``` | x = x + algo
```-=``` | x = x - algo
```*=``` | x = x * algo
```++``` | Soma uma unidade (incrementa 1)
```--``` | Diminui uma unidade (decrementa 1)

## Operadores relacionais

Operadores | Sobre
:-------- | :-----
```>``` | Maior que
```<``` | Menor que
```>=``` | Maior ou igual que
```<=``` | Menor ou igual que
```==``` | Igual em valor
```===``` | Igual em valor e tipagem
```!=``` | Não é igual em valor
```!==``` | Não é igual em valor nem tipagem


## Operadores lógicos

Operadores | Sobre
:-------- | :-----
```!``` | Negação
```<``` | ```e```
```>=``` | ```ou```

## Operadores ternários

São usados em uma única linha. Tipo assim:

```javascript
let lucro = 1000;
let bonus = lucro * (lucro > 1000 ? 0.10 : 0.15)

/*A linha de cima é lida assim:
Se o lucro é maior que 1000, então multiplique
ele por 0.10; senão, multiplique ele por 0.15
Depois, guarde o resultado na variável 'bonus'*/
```

Outro exemplo.

```javascript
const drink = idade >= 18 ? 'vinho' : 'água';
// O resultado é guardado em 'drink'
```

Operadores | Sobre
:-------- | :-----
```?``` | Tomada de decisão
```:``` | Separa o ```então``` (primeira parte) do ```senão``` (segunda parte)

