# EN: Arrays

The two most important things in JS: **arrays** and objects.

Most important thing about an array: order matters.

Basic material.

```javascript
// Create Array #01
const friends = ['Michael', 'Steven', 'Peter'];
console.log(friends); // > ['Michael', 'Steven', 'Peter']

// Create Array #02 - (new Array())
let anos = new Array(1991, 1984, 2008, 2020);

// Size of array - .lenght
console.log(friends.length);

// Get the last item - [.length - 1]
console.log(friends[friends.length - 1]);

// Extract value from inside an array
const calcIdade = function (birthYeah) {
  return 2037 - birthYeah;
}

anos = [1990, 1967, 2002, 2010, 2018];

const age1 = calcIdade(anos[0]);
const age2 = calcIdade(anos[1]);
const age3 = calcIdade(anos[anos.length - 1]);
console.log(age1, age2, age3);      // > 47, 70, 19

// Store the age inside a new array
const ages = [calcIdade(anos[0]), calcIdade(anos[1]), calcIdade(anos[anos.length - 1])];
console.log(ages);                  // > [47, 70, 19]
```

## Array Methods

We can think of methods as array operations. 

Here are some **basic** array methods that are very useful. 

Method | What | Meaning
:------ | :---- | :-------
```push()``` | ADDS AN ITEM AND RETURNS LENGTH | It adds an item at the **end of the array**. It returns a value - the length of the new array. It can be useful to store this value somewhere.
```unshift()``` | ADDS AN ITEM AND RETURNS LENGTH | It adds an item at the **start of the array**. It returns a value - the length of the new array.
```pop()``` | REMOVES AN ITEM AND RETURNS IT | It'she opposite of push - it REMOVES the **last item of the array**. It returns a value - the very item that was removed.
```shift()``` | REMOVES AN ITEM AND RETURNS IT |  the opposite of unshift - it REMOVES the **first item of the array**. IT returns a value - the very item it removes.
```indexOf()``` | RETURNS THE INDEX | It returns a value - the index of the item you're searching. If the item is not in the array, it returns -1.
```includes()``` | RETURNS BOOLEAN | It returns a boolean value. ```true``` if the item is in the array and ```false``` if the item is not in the array. It works with strict values (===). No type coercion allowed.


---
---

# PT: Arrays

As duas coisas mais importantes em JS são **array** e objetos. 

Coisa mais importante do array: **ordem importa**.

Material básico abaixo.

```javascript
// Criar Array #01
const amigos = ['Michael', 'Steven', 'Peter'];
console.log(amigos); // > ['Michael', 'Steven', 'Peter']

// Criar Array #02 - (new Array())
let anos = new Array(1991, 1984, 2008, 2020);

// Tamanho do array - .lenght
console.log(amigos.length);        // não tem ()

// Pegar último item - [.length - 1]
console.log(amigos[amigos.length - 1]);

// Extrair um valor de dentro do array
const calcIdade = function (anoNascimento) {
  return 2037 - anoNascimento;
}

anos = [1990, 1967, 2002, 2010, 2018];

const idade1 = calcIdade(anos[0]);
const idade2 = calcIdade(anos[1]);
const idade3 = calcIdade(anos[anos.length - 1]);
console.log(ano1, ano2, ano3);      // > 47, 70, 19

// Guardar idades dentro de um novo array
const anos = [calcIdade(anos[0]), calcIdade(anos[1]), calcIdade(anos[anos.length - 1])];
console.log(anos);                  // > [47, 70, 19]
```

## Métodos do Array

Dá pra pensar em métodos como operações de array.

Aqui uma tabela de métodos de array **básicos** que pode ser útil e servir de lembrete.

Método | O que | Significado
:------ | :---- | :-------
```push()``` | ADICIONA UM ITEM E DEVOLVE TAMANHO (LENGTH) | Ele adiciona um item **no final do array** e retorna um valor - o tamanho do novo array. Pode ser útil guardar esse tamanho em alguma variável.
```unshift()``` | ADICIONA UM ITEM E RETORNA TAMANHO (LENGTH) | Ele adiciona um item **no começo do array** e retorna um valor - o tamanho do novo array. 
```pop()``` | REMOVE UM ITEM E RETORNA ELE PRÓPRIO | É o contrário do push - ele remove **o último item do array** e devolve esse item como um valor. ```shift()``` | REMOVE UM ITEM E RETORNA ELE PRÓPRIO | É o contrário do unshift - ele remove **o primeiro item do array** e devolve esse item como um valor. 
```indexOf()``` | RETORNA O ÍNDICE DO ITEM | Ele retorna um valor - o índice do item que está buscando. Se o item não estiver no array, ele devolve -1. 
```includes()``` | RETORNA UM BOOLEAN | Ele retorna um valor booleano: ```true``` se esse item estiver no array e ```false``` se o item não estiver no array. Trabalha apenas com valores e tipagem iguais (===). 
