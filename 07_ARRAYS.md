# EN: Arrays

The two most important things in JS: **arrays** and objects.

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

---
---

# PT: Arrays

As duas coisas mais importantes em JS são **array** e objetos. 

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