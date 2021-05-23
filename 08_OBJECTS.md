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
    'teacher',
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

const jonasObject = {
    firstName: 'Jonas',
    lastName: 'Schmedtmann',
    age: 2037 - 1991,
    job: 'teacher',
    friends: ['Michael', 'Peter', 'Steven']
}
/* To access the item:
jonasObject.firstName or          jonasObject['firstName']
jonasObject.lastName or           jonasObject[.lastName']
jonasObject.age or                jonasObject['age']
jonasObject.job or                jonasObject['job']
jonasObject.friends or            jonasObject['friends']
*/
```

The ```jonasObject``` has 5 properties: ```firstName, lastName, age, job, friends```. The main difference is **the order of the properties DOES NOT matter at all**.

## To access: dot (```.```) or bracket (```[]```) notation

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

const jonasObject = {
    nome: 'Jonas',
.lastName: 'Schmedtmann',
    age: 2037 - 1991,
    job: 'teacher',
    friends: ['Michael', 'Peter', 'Steven'] 
}

/* Para acessar:
jonasObject.nome or          jonasObject['nome']
jonasObject.lastName or     jonasObject[.lastName']
jonasObject.age or         jonasObject['age']
jonasObject.job or     jonasObject['job']
jonasObject.friends or        jonasObject['friends']
*/
```
O ```jonasObject``` tem 5 propriedades: ```nome,.lastName, age, job, friends```. A principalmente diferença para um array é que **em um objeto, a ordem das propriedades NÃO importa de nada.**
