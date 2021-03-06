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

Como dito antes, arrays e **objetos** s??o as duas pe??as mais importantes em JavaScript. Assim como o array, um objeto tamb??m ?? uma Estrutura de Dados em JS. Ent??o faz sentido comparar os dois.

Um array ?? usado para guardar v??rios valores, relacionados entre si, dentro de uma vari??vel. N??o d?? pra firstNamear cada item dentro de um array: a ??nica coisa que podemos fazer ?? acessar o item por meio do ??ndice. S?? isso.

```javascript
// TRADU????ES: EN -> PT
jonasObject -> jonasObjeto
firstName -> primeiroNome
lastName -> ultimoNome
age -> idade
job -> profissao
friends -> amigos
localization -> localiza????o
course -> curso
```

D?? uma olhada no exemplo abaixo.

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

Agora, compara com o pr??ximo objeto.

```javascript
// OBJECT - { }
// Ordem N??O importa.

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

A principalmente diferen??a para um array ?? que **em um objeto, a ordem das propriedades N??O importa de nada.**

## Para acessar: nota????o por ponto (`.`) ou por colchetes (`[]`)?

D?? pra acessar as propriedades de um objeto de duas formas: pela nota????o de ponto ou pela nota????o de colchetes.

Mas tem uma diferen??a entre eles.

Para acessar via nota????o de ponto, **voc?? deve saber o firstName da propriedade que guarda o valor desejado**. A?? depois, voc?? s?? precisa escrever esse firstName depois do ponto.

Da seguinte forma.

```javascript
// NOTA????O DE PONTO
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

Agora, por meio da nota????o de colchetes, voc?? tem duas op????es:

1. primeiro saber o firstName da propriedade que guarda o valor desejado
2. al??m de saber o ponto anterior, voc?? tamb??m precisa criar uma express??o que vai resultar no firstName dessa propriedade

Leia o segundo ponto de novo.

Agora d?? uma olhada no c??digo debaixo.

```javascript
// NOTA????O POR COLCHETE
const jonasObject = {
  firstName: "Jonas",
  lastName: "Schmedtmann",
  age: 2037 - 1991,
  job: "teacher",
  friends: ["Michael", "Peter", "Steven"],
};

console.log(jonasObject["lastName"]); // > Schmedtmann

const nameKey = "firstName"; // vari??vel "nameKey" guarda uma stirng

console.log(jonasObject["" + nameKey]); // > Jonas
console.log(jonasObject["sobre" + nameKey]); // > Schmedtmann
// PS: nameKey guarda uma string com valor 'firstName'
// (concatena????o chega no resultado!)
```

Outro exemplo.

```javascript
// NOTA????O POR COLCHETES
const jonasObject = {
  firstName: "Jonas",
  lastName: "Schmedtmann",
  age: 2037 - 1991,
  job: "teacher",
  friends: ["Michael", "Peter", "Steven"],
};

const interestedIn = prompt(
  "O que voc?? quer saber sobre o Jonas: Escolha entre firstName, lastName, age, job, friends"
);
// Vamos imaginar que o usu??rio escolheu 'job': interestedIn = 'job'

console.log(jonas[interestedIn]); // > teacher
```

## Adicionar propriedades em um Objeto

Faz da seguinte forma.

```javascript
// NOTA????O POR COLCHETES
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

## M??todos do Objeto

M??todos s??o fun????es de um objeto.

Lembre-se que **fun????es s??o valores** em JS, ent??o isso significa que as fun????es podem ser escritas no formato par/valor (e na verdade, dentro dos objetos, elas s??o escritas assim). Ent??o os m??todos s??o propriedades, s?? que o seu valor ?? uma fun????o.

`propriedade: valor;`

Leia o par??grafo de cima de novo. Tem l??gica ali.

Aqui embaixo veja um m??todo de objeto chamado `calcAge`.

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
    // m??todo calcAge
    return 2037 - birthYear;
  },
};

console.log(jonas.calcAge(1991)); // > 46
console.log(jonas["calcAge"](1991)); // > 46
```

Mas tem **outro jeito de escrever o c??digo de cima** usando o princ??pio KISS de "Keep It Simple, Stupid" ou _Mantenha Tudo Simples, Bob??o_: apresentando o `this`.

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
// THIS foi criado dentro do jonasObject (contexto) ent??o se refere a ele
console.log(jonas.calcAge()); // > 46
```

E adivinha?

Tem uma **solu????o ainda melhor, considerando as melhores pr??ticas**.

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
