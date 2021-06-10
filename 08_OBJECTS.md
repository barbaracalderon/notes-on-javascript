# EN: Objects

As said before, arrays and **objects** are the two most important pieces in JavaScript. Much as an array, an object is also a Data Structure in JS. So it makes sense to compare both.

An array is used to store multiple related values in a variable.

We can't firstName each array item separately: the only thing we can do is access them throrgh an index. That's all.

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
  firstName: "Jonas",
  lastName: "Schmedtmann",
  age: 2037 - 1991,
  job: "teacher",
  friends: ["Michael", "Peter", "Steven"],
};
/* To access the item:
jonasObject.firstName or          jonasObject['firstName']
jonasObject.lastName or           jonasObject[.lastName']
jonasObject.age or                jonasObject['age']
jonasObject.job or                jonasObject['job']
jonasObject.friends or            jonasObject['friends']
*/
```

The `jonasObject` has 5 properties: `firstName, lastName, age, job, friends`.

The main difference is **the order of the properties DOES NOT matter at all**.

## To access: dot (`.`) or bracket (`[]`) notation?

You can access an object property in both ways - either through dot notation or through the bracket notation.

But there is a difference in between then.

To access via dot notation, **you gotta know the firstName of the variable that holds that value**. Then, all you gotta do is write that firstName after the dot.

Like this.

```javascript
// DOT NOTATION
const jonasObject = {
  firstName: "Jonas",
  lastName: "Schmedtmann",
  age: 2037 - 1991,
  job: "teacher",
  friends: ["Michael", "Peter", "Steven"],
};

console.log(jonasObject.firstName); // > Jonas
console.log(jonasObject.lastName); // > Schmedtmann
```

Now, through the bracket notation you have two options:

1. to know the variable firstName that holds the value you want
2. to know first point here and also manage an expression that will result in that variable firstName

Check it out.

```javascript
// BRACKET NOTATION
const jonasObject = {
  firstName: "Jonas",
  lastName: "Schmedtmann",
  age: 2037 - 1991,
  job: "teacher",
  friends: ["Michael", "Peter", "Steven"],
};

console.log(jonasObject["lastName"]); // > Schmedtmann

const nameKey = "firstName";

console.log(jonasObject["first" + nameKey]); // > Jonas
console.log(jonasObject["last" + nameKey]); // > Schmedtmann
// PS: nameKey holds a string value of 'firstName'
// (concatenation is used!)
```

Another example.

```javascript
// BRACKET NOTATION
const jonasObject = {
  firstName: "Jonas",
  lastName: "Schmedtmann",
  age: 2037 - 1991,
  job: "teacher",
  friends: ["Michael", "Peter", "Steven"],
};

const interestedIn = prompt(
  "What do you want to know about Jonas? Choose between firstName, lastName, age, job, friends"
);
// Let's imagine the user chose 'job': interestedIn = 'job'

console.log(jonas[interestedIn]); // > teacher
```

## Add properties to an Object

Here's how you do it.

```javascript
// BRACKET NOTATION
const jonasObject = {
  firstName: "Jonas",
  lastName: "Schmedtmann",
  age: 2037 - 1991,
  job: "teacher",
  friends: ["Michael", "Peter", "Steven"],
};

jonasObject.localization = "Portugal";
jonasObject.course = "JavaScript";

console.log(jonasObject);
// >
/*
firstName: 'Jonas',
    lastName: 'Schmedtmann',
    age: 2037 - 1991,
    job: 'teacher',
    friends: (3) ['Michael', 'Peter', 'Steven']
    localization: 'Portugal',
    course: 'JavaScript'
*/
```

## Object Methods

Methods are object functions.

Remember that **functions are values** in JS, so this means that functions can be written in value/pairs (and indeed, inside objects, they are!). So, methods are properties, it just happens that the value is a function.

`property: value;`

Read line above again. There is logic in there.

Here's an object method called `calcAge`.

```javascript
// Example
const jonasObject = {
  firstName: "Jonas",
  lastName: "Schmedtmann",
  birthYear: 1991,
  job: "teacher",
  friends: ["Michael", "Peter", "Steven"],
  hasDriversLicense: true,
  calcAge: function (birthYear) {
    // calcAge method
    return 2037 - birthYear;
  },
};

console.log(jonas.calcAge(1991)); // > 46
console.log(jonas["calcAge"](1991)); // > 46
```

But there's **another way to write the above** using the KISS principle of "Keep It Simple, Stupid": introducing `this`.

```javascript
// Using THIS: it refers to the context in which it was created
const jonasObject = {
  firstName: "Jonas",
  lastName: "Schmedtmann",
  birthYear: 1991,
  job: "teacher",
  friends: ["Michael", "Peter", "Steven"],
  hasDriversLicense: true,
  calcAge: function () {
    console.log(this); // test this!
    return 2037 - this.birthYear; // this -> refers to jonasObject
  },
};
// THIS was created inside jonasObject (context) so it refers to it
console.log(jonas.calcAge()); // > 46
```

Guess what?

There is **even a better solution to the code, considering best practices**.

Check it out.

```javascript
// Using THIS: it refers to the context in which it was created
const jonasObject = {
  firstName: "Jonas",
  lastName: "Schmedtmann",
  birthYear: 1991,
  job: "teacher",
  friends: ["Michael", "Peter", "Steven"],
  hasDriversLicense: true,
  calcAge: function () {
    this.age = 2037 - this.birthYear; // Best practice
    return this.age; // It will create this.age property for jonasObject
  },
};

console.log(jonas.age); // > 46
```

---

# PT: Objetos

Como dito antes, arrays e **objetos** são as duas peças mais importantes em JavaScript. Assim como o array, um objeto também é uma Estrutura de Dados em JS. Então faz sentido comparar os dois.

Um array é usado para guardar vários valores, relacionados entre si, dentro de uma variável. Não dá pra firstNamear cada item dentro de um array: a única coisa que podemos fazer é acessar o item por meio do índice. Só isso.

```javascript
// TRADUÇÕES: EN -> PT
jonasObject -> jonasObjeto
firstName -> primeiroNome
lastName -> ultimoNome
age -> idade
job -> profissao
friends -> amigos
localization -> localização
course -> curso
```

Dá uma olhada no exemplo abaixo.

```javascript
// ARRAY - [ ]
// Ordem importa.

const jonasArray = [
    'Jonas',
    'Schmedtmann',
    2037 - 1991;
    'teacher',
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
    firstName: 'Jonas',
.lastName: 'Schmedtmann',
    age: 2037 - 1991,
    job: 'teacher',
    friends: ['Michael', 'Peter', 'Steven']
}

/* Para acessar:
jonasObject.firstName or          jonasObject['firstName']
jonasObject.lastName or           jonasObject[.lastName']
jonasObject.age or                jonasObject['age']
jonasObject.job or                jonasObject['job']
jonasObject.friends or            jonasObject['friends']
*/
```

O `jonasObject` tem 5 propriedades: `firstName,.lastName, age, job, friends`.

A principalmente diferença para um array é que **em um objeto, a ordem das propriedades NÃO importa de nada.**

## Para acessar: notação por ponto (`.`) ou por colchetes (`[]`)?

Dá pra acessar as propriedades de um objeto de duas formas: pela notação de ponto ou pela notação de colchetes.

Mas tem uma diferença entre eles.

Para acessar via notação de ponto, **você deve saber o firstName da propriedade que guarda o valor desejado**. Aí depois, você só precisa escrever esse firstName depois do ponto.

Da seguinte forma.

```javascript
// NOTAÇÃO DE PONTO
const jonasObject = {
  firstName: "Jonas",
  lastName: "Schmedtmann",
  age: 2037 - 1991,
  job: "teacher",
  friends: ["Michael", "Peter", "Steven"],
};

console.log(jonasObject.firstName); // > Jonas
console.log(jonasObject.lastName); // > Schmedtmann
```

Agora, por meio da notação de colchetes, você tem duas opções:

1. primeiro saber o firstName da propriedade que guarda o valor desejado
2. além de saber o ponto anterior, você também precisa criar uma expressão que vai resultar no firstName dessa propriedade

Leia o segundo ponto de novo.

Agora dá uma olhada no código debaixo.

```javascript
// NOTAÇÃO POR COLCHETE
const jonasObject = {
  firstName: "Jonas",
  lastName: "Schmedtmann",
  age: 2037 - 1991,
  job: "teacher",
  friends: ["Michael", "Peter", "Steven"],
};

console.log(jonasObject["lastName"]); // > Schmedtmann

const nameKey = "firstName"; // variável "nameKey" guarda uma stirng

console.log(jonasObject["" + nameKey]); // > Jonas
console.log(jonasObject["sobre" + nameKey]); // > Schmedtmann
// PS: nameKey guarda uma string com valor 'firstName'
// (concatenação chega no resultado!)
```

Outro exemplo.

```javascript
// NOTAÇÃO POR COLCHETES
const jonasObject = {
  firstName: "Jonas",
  lastName: "Schmedtmann",
  age: 2037 - 1991,
  job: "teacher",
  friends: ["Michael", "Peter", "Steven"],
};

const interestedIn = prompt(
  "O que você quer saber sobre o Jonas: Escolha entre firstName, lastName, age, job, friends"
);
// Vamos imaginar que o usuário escolheu 'job': interestedIn = 'job'

console.log(jonas[interestedIn]); // > teacher
```

## Adicionar propriedades em um Objeto

Faz da seguinte forma.

```javascript
// NOTAÇÃO POR COLCHETES
const jonasObject = {
  firstName: "Jonas",
  lastName: "Schmedtmann",
  age: 2037 - 1991,
  job: "teacher",
  friends: ["Michael", "Peter", "Steven"],
};

jonasObject.localization = "Portugal";
jonasObject.course = "JavaScript";

console.log(jonasObject);
// Mostra todo o objeto:
/*
    firstName: 'Jonas',
    lastName: 'Schmedtmann',
    age: 2037 - 1991,
    job: 'teacher',
    friends: (3) ['Michael', 'Peter', 'Steven']
    localization: 'Portugal',
    course: 'JavaScript'
*/
```

## Métodos do Objeto

Métodos são funções de um objeto.

Lembre-se que **funções são valores** em JS, então isso significa que as funções podem ser escritas no formato par/valor (e na verdade, dentro dos objetos, elas são escritas assim). Então os métodos são propriedades, só que o seu valor é uma função.

`propriedade: valor;`

Leia o parágrafo de cima de novo. Tem lógica ali.

Aqui embaixo veja um método de objeto chamado `calcAge`.

```javascript
// Exemplo
const jonasObject = {
  firstName: "Jonas",
  lastName: "Schmedtmann",
  birthYear: 1991,
  job: "teacher",
  friends: ["Michael", "Peter", "Steven"],
  hasDriversLicense: true,
  calcAge: function (birthYear) {
    // método calcAge
    return 2037 - birthYear;
  },
};

console.log(jonas.calcAge(1991)); // > 46
console.log(jonas["calcAge"](1991)); // > 46
```

Mas tem **outro jeito de escrever o código de cima** usando o princípio KISS de "Keep It Simple, Stupid" ou _Mantenha Tudo Simples, Bobão_: apresentando o `this`.

```javascript
// Usando o THIS: ele se refere ao contexto em que foi criado
const jonasObject = {
  firstName: "Jonas",
  lastName: "Schmedtmann",
  birthYear: 1991,
  job: "teacher",
  friends: ["Michael", "Peter", "Steven"],
  hasDriversLicense: true,
  calcAge: function () {
    console.log(this); // teste isso!
    return 2037 - this.birthYear; // this -> se refere ao jonasObject
  },
};
// THIS foi criado dentro do jonasObject (contexto) então se refere a ele
console.log(jonas.calcAge()); // > 46
```

E adivinha?

Tem uma **solução ainda melhor, considerando as melhores práticas**.

Olha abaixo.

```javascript
// Usando o THIS: ele se refere ao contexto em que foi criado
const jonasObject = {
  firstName: "Jonas",
  lastName: "Schmedtmann",
  birthYear: 1991,
  job: "teacher",
  friends: ["Michael", "Peter", "Steven"],
  hasDriversLicense: true,
  calcAge: function () {
    this.age = 2037 - this.birthYear; // Best practice
    return this.age; // Vai criar uma propriedade this.age para o jonasObject
  },
};

console.log(jonas.age); // > 46
```
