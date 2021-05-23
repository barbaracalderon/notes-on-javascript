# EN: Objects

As said before, arrays and **objects** are the two most important pieces in JavaScript. Much as an array, an object is also a Data Structure in JS. So it makes sense to compare both.

An array is used to store multiple related values in a variable. 

We can't name each array item separately: the only thing we can do is access them throrgh an index. That's all.

Check the following example.

```javascript
// ARRAY - [ ]
// Order matters.

const jonasArray = [
    'Jonas',
    'Schmedtmann',
    2037 - 1991;
    'professor',
    ['Michael', 'Peter', 'Steven']
]

/* To access the item:
jonasArray[0]
JonasArray[1]
jonasArray[2]
jonasArray[3]
jonasArray[4]
*/
```

Now, compare it to the following object.

```javascript
// OBJECT - { }
// Order does NOT matter.

const jonasObjeto = {
    nome: 'Jonas',
    sobrenome: 'Schmedtmann',
    idade: 2037 - 1991,
    profissao: 'professor',
    amigos: ['Michael', 'Peter', 'Steven']
}
/* To access the item:
jonasObjeto.nome or          jonasObjeto['nome']
jonasObjeto.sobrenome or           jonasObjeto[.sobrenome']
jonasObjeto.idade or                jonasObjeto['idade']
jonasObjeto.profissao or                jonasObjeto['profissao']
jonasObjeto.amigos or            jonasObjeto['amigos']
*/
```

The ```jonasObjeto``` has 5 properties: ```nome, sobrenome, idade, profissao, amigos```. 

The main difference is **the order of the properties DOES NOT matter at all**.

## To access: dot (```.```) or bracket (```[]```) notation?

You can access an object property in both ways - either through dot notation or through the bracket notation.

But there is a difference in between then.

To access via dot notation, **you gotta know the name of the variable that holds that value**. Then, all you gotta do is write that name after the dot. 

Like this.

```javascript
// DOT NOTATION
const jonasObjeto = {
    nome: 'Jonas',
    sobrenome: 'Schmedtmann',
    idade: 2037 - 1991,
    profissao: 'professor',
    amigos: ['Michael', 'Peter', 'Steven']
}

console.log(jonasObjeto.nome)   // > Jonas
console.log(jonasObjeto.sobrenome)    // > Schmedtmann
```

Now, through the bracket notation you have two options: 

1. to know the variable name that holds the value you want
2. to know first point here and also manidade an expression that will result in that variable name

Check it out.

```javascript
// BRACKET NOTATION
const jonasObjeto = {
    nome: 'Jonas',
    sobrenome: 'Schmedtmann',
    idade: 2037 - 1991,
    profissao: 'professor',
    amigos: ['Michael', 'Peter', 'Steven']
}

console.log(jonasObjeto['sobrenome'])  // > Schmedtmann

const nameKey = 'Name';

console.log(jonasObjeto['first' + nameKey]);    // > Jonas
console.log(jonasObjeto['last' + nameKey]);     // > Schmedtmann
// PS: nameKey holds a string value of 'Name'
// (concatenation is used!)
```

Another example.

```javascript
// BRACKET NOTATION
const jonasObjeto = {
    nome: 'Jonas',
    sobrenome: 'Schmedtmann',
    idade: 2037 - 1991,
    profissao: 'professor',
    amigos: ['Michael', 'Peter', 'Steven']
}

const interestedIn = prompt('What do you want to know about Jonas? Choose between nome, sobrenome, idade, profissao, amigos');
// Let's imagine the user chose 'profissao': interestedIn = 'profissao'

console.log(jonas[interestedIn])    // > professor
```

## Add properties to an Object

Here's how you do it.

```javascript
// BRACKET NOTATION
const jonasObjeto = {
    nome: 'Jonas',
    sobrenome: 'Schmedtmann',
    idade: 2037 - 1991,
    profissao: 'professor',
    amigos: ['Michael', 'Peter', 'Steven']
}

jonasObjeto.local = 'Portugal'
jonasObjeto.curso = 'JavaScript'

console.log(jonasObjeto)
// >
/*
nome: 'Jonas',
    sobrenome: 'Schmedtmann',
    idade: 2037 - 1991,
    profissao: 'professor',
    amigos: (3) ['Michael', 'Peter', 'Steven']
    local: 'Portugal',
    curso: 'JavaScript'
*/
```
---
---

# PT: Objetos

Como dito antes, arrays e **objetos** são as duas peças mais importantes em JavaScript. Assim como o array, um objeto também é uma Estrutura de Dados em JS. Então faz sentido comparar os dois.

Um array é usado para guardar vários valores, relacionados entre si, dentro de uma variável. Não dá pra nomear cada item dentro de um array: a única coisa que podemos fazer é acessar o item por meio do índice. Só isso. 

Dá uma olhada no exemplo abaixo.

```javascript
// ARRAY - [ ]
// Ordem importa.

const jonasArray = [
    'Jonas',
    'Schmedtmann',
    2037 - 1991;
    'professor',
    ['Michael', 'Peter', 'Steven']
]

/* Para acessar:
jonasArray[0]
jonasArray[1]
jonasArray[2]
jonasArray[3]
jonasArray[4]
*/
```
Agora, compara com o próximo objeto.

```javascript
// OBJECT - { }
// Ordem NÃO importa.

const jonasObjeto = {
    nome: 'Jonas',
.sobrenome: 'Schmedtmann',
    idade: 2037 - 1991,
    profissao: 'professor',
    amigos: ['Michael', 'Peter', 'Steven'] 
}

/* Para acessar:
jonasObjeto.nome or          jonasObjeto['nome']
jonasObjeto.sobrenome or     jonasObjeto[.sobrenome']
jonasObjeto.idade or         jonasObjeto['idade']
jonasObjeto.profissao or     jonasObjeto['profissao']
jonasObjeto.amigos or        jonasObjeto['amigos']
*/
```
O ```jonasObjeto``` tem 5 propriedades: ```nome,.sobrenome, idade, profissao, amigos```. 

A principalmente diferença para um array é que **em um objeto, a ordem das propriedades NÃO importa de nada.**

## Para acessar: notação por ponto (```.```) ou por colchetes (```[]```)?

Dá pra acessar as propriedades de um objeto de duas formas: pela notação de ponto ou pela notação de colchetes. 

Mas tem uma diferença entre eles.

Para acessar via notação de ponto, **você deve saber o nome da propriedade que guarda o valor desejado**. Aí depois, você só precisa escrever esse nome depois do ponto. 

Da seguinte forma.

```javascript
// NOTAÇÃO DE PONTO
const jonasObjeto = {
    nome: 'Jonas',
    sobrenome: 'Schmedtmann',
    idade: 2037 - 1991,
    profissao: 'professor',
    amigos: ['Michael', 'Peter', 'Steven']
}

console.log(jonasObjeto.nome)   // > Jonas
console.log(jonasObjeto.sobrenome)    // > Schmedtmann
```
Agora, por meio da notação de colchetes, você tem duas opções:

1. primeiro saber o nome da propriedade que guarda o valor desejado
2. além de saber o ponto anterior, você também precisa criar uma expressão que vai resultar no nome dessa propriedade

Leia o segundo ponto de novo.

Agora dá uma olhada no código debaixo.

```javascript
// NOTAÇÃO POR COLCHETE
const jonasObjeto = {
    nome: 'Jonas',
    sobrenome: 'Schmedtmann',
    idade: 2037 - 1991,
    profissao: 'professor',
    amigos: ['Michael', 'Peter', 'Steven']
}

console.log(jonasObjeto['sobrenome'])  // > Schmedtmann

const nameKey = 'nome';    // variável "nameKey" guarda uma stirng

console.log(jonasObjeto['' + nameKey]);    // > Jonas
console.log(jonasObjeto['sobre' + nameKey]);     // > Schmedtmann
// PS: nameKey guarda uma string com valor 'nome'
// (concatenação chega no resultado!)
```
Outro exemplo.
```javascript
// NOTAÇÃO POR COLCHETES
const jonasObjeto = {
    nome: 'Jonas',
    sobrenome: 'Schmedtmann',
    idade: 2037 - 1991,
    profissao: 'professor',
    amigos: ['Michael', 'Peter', 'Steven']
}

const interessadoEm = prompt('O que você quer saber sobre o Jonas: Escolha entre nome, sobrenome, idade, profissao, amigos');
// Vamos imaginar que o usuário escolheu 'profissao': interessadoEm = 'profissao'

console.log(jonas[interessadoEm])    // > professor
```
## Adicionar propriedades em um Objeto

Faz da seguinte forma.

```javascript
// NOTAÇÃO POR COLCHETES
const jonasObjeto = {
    nome: 'Jonas',
    sobrenome: 'Schmedtmann',
    idade: 2037 - 1991,
    profissao: 'professor',
    amigos: ['Michael', 'Peter', 'Steven']
}

jonasObjeto.local = 'Portugal'
jonasObjeto.curso = 'JavaScript'

console.log(jonasObjeto)
// Mostra todo o objeto:
/*
    nome: 'Jonas',
    sobrenome: 'Schmedtmann',
    idade: 2037 - 1991,
    profissao: 'professor',
    amigos: (3) ['Michael', 'Peter', 'Steven']
    local: 'Portugal',
    curso: 'JavaScript'
*/
```