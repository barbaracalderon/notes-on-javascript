# EN: Destructuring Arrays and Objects

It's a way to unpack values stored inside Arrays or Objects into separate variables.

_PS: Technically, Arrays **are** Objects but in this case I want to separate them for better understanding because their behaviour is a bit different._

## Arrays

To destructure arrays, we use brackets [] because arrays are created with brackets.

Here's a simple example.

```javascript
const arr = [2, 3, 4];

// With no "destructuring":
const a = arr[0];
const b = arr[1];
const c = arr[2];

// With "destructuring":
const [x, y, z] = arr; // It's not an array, it's the destructuring syntax
console.log(x, y, z); // > 2 3 4
```

We can also destructure _some_ elements and **not** all of it. Pay very careful attention to the code below because it shows some other things destructuring can do. It's better to dive than to explain.

```javascript
// Object 'restaurant'
const restaurant = {
  name: "Classico Italiano",
  location: "Via Angelo Tavanti 23, Firenze, Italy",
  categories: ["Italian", "Pizzeria", "Vegetarian", "Organic"],
  starterMenu: ["Focaccia", "Bruschetta", "Garlic Bread", "Caprese Salad"],
  mainMenu: ["Pizza", "Pasta", "Risotto"],
  order: function(starterIndex, mainIndex) {
      return [this.starterMenu[starterIndex], this.mainMenu[mainIndex]]
  }
};

// Destructuring 1st and 3rd item of categories property:
let [main, , secondary] = restaurant.categories;
console.log(main, secondary); // > Italian Vegetarian

// Assume we want to exchange main and secondary categories.
// Without destructuring:
const temp = main;
main = secondary;
secondary = temp;
console.log(main, secondary)    // > Italian Vegetarian
// With destructuring:
[main, secondary] = [secondary, main]
console.log(main, secondary)    // > Vegetarian Italian

// Receive 2 return values from a function:
const [starter, mainCourse] = restaurant.order(2, 0);
console.log(starter, mainCourse)    // > Garlic Bread Pizza

// Destructuring nested arrays
const nested = [2, 4, [5, 6]];
const [i, , [j, k]] = nested;
console.log(i, j, k)/            // > 2 5 6

// Default values
const [p, q, r] = [8, 9];
console.log(p, q, r);            // > 8 9 undefined

const [m=1, n=1, o=1] = [3]
console.log(m, n, o)            // > 3 1 1
```

## Objects

To destructure objects, we use curly braces {} because objects are created with curly braces. We also need to know the **property names** we want to extract.

This is **extremely useful**, in Ecma6 edition. Specially when dealing with APIs. The data from APIs come in form of objects and destructuring is a life-saver because it speeds the extraction of information.

Again, pay careful attention to the code below because it shows some other things destructuring can do. It's better to dive in it than to explain.

```javascript
// The object 'restaurant' has object 'openingHours' now
// ...and 'openingHours' has other objects in it (thu, fri, sat)
const restaurant = {
  name: "Classico Italiano",
  location: "Via Angelo Tavanti 23, Firenze, Italy",
  categories: ["Italian", "Pizzeria", "Vegetarian", "Organic"],
  starterMenu: ["Focaccia", "Bruschetta", "Garlic Bread", "Caprese Salad"],
  mainMenu: ["Pizza", "Pasta", "Risotto"],
  order: function(starterIndex, mainIndex) {
      return [this.starterMenu[starterIndex], this.mainMenu[mainIndex]]
  }
  orderDelivery: function ( {starterIndex = 1, mainIndex = 0, time = '20:00', address}) {
      console.log(`Order received! ${this.starterMenu[starterIndex]} and ${this.mainMenu[mainIndex]} will be delivered to ${address} at ${time}`)
  },
  openingHours: {
      thu: {
          open: 12,
          close: 22,
      },
      fri: {
          open: 11,
          close: 23,
      },
      sat: {
          open: 0,  // Open 24hs
          close: 24,
      },
  }
};

// Destructuring 3 properties: name, openingHours, categories
// ps: we gotta know the property names in order to do this
const { name, openingHours, categories } = restaurant;
console.log(name, openingHours, categories);

// What if we want our variables to be called something else
// other than the property name? We change it. Here's how.
// (We still need to know the property name, though)
// const {propertyName: newVariableName} = object;
const {name: restaurantName, openingHours: hours} = restaurant;

// Default values + combining new variable names
const { menu = [], starterMenu: starters = [] } = restaurant;
console.log(menu, starters);        // > [] ['Focacia', etc etc]

// Mutating variables
let a = 111;
let b = 999;
const obj = {a: 23, b: 7, c: 14};

{a, b} = obj;       // Error! JS sees curly braces and expects an object
                    // We must fix the error by adding parentheses;
( {a, b} ) = obj;
console.log(a, b)   // > 23 7

// Nested objects
const { fri: {open, close} } = openingHours;
console.log(open, close)        // > 11 23

// Pass an object as a function argument inside the 'orderDelivery' method
restaurant.orderDelivery{
    time: '22:30',
    address: 'Via del Sole, 21',
    mainIndex: 2,
    starterIndex: 2,
}
// The above is important: we did not pass 4 arguments
// we only passed one object (curly braces) as argument.
// The order inside the object does not matter, though.

```

---

# PT: Desestruturando (Destructuring) Arrays e Objetos

A tradu????o ?? "desestruturando" mas vou utilizar o termo em ingl??s "destructuring" mesmo. ?? uma **forma de desempacotar valores guardados**, dentro de Arrays ou Objetos, em vari??veis separadas.

_PS: tecnicamente, Arrays **s??o** Objetos mas nesse caso eu quero separar os termos para um melhor entendimento porque seus comportamentos s??o um pouco distintos._

## Arrays

Para desestruturar Arrays n??s usamos os colchetes [] porque eles s??o criados com eles.

Um exemplo simples abaixo.

```javascript
const arr = [2, 3, 4];

// Sem o "destructuring":
const a = arr[0];
const b = arr[1];
const c = arr[2];

// Com o "destructuring":
const [x, y, z] = arr; // N??o ?? um array, ?? a sintaxe do destructuring
console.log(x, y, z); // > 2 3 4
```

N??s tamb??m podemos desestruturar _alguns_ elementos e **n??o** todos eles. Presta bem aten????o no c??digo abaixo porque ele mostra algumas outras coisas que o destructuring consegue fazer. ?? melhor mergulhar no c??digo do que explicar em texto.

```javascript
// Objeto 'restaurant'
const restaurant = {
  name: "Classico Italiano",
  location: "Via Angelo Tavanti 23, Firenze, Italy",
  categories: ["Italian", "Pizzeria", "Vegetarian", "Organic"],
  starterMenu: ["Focaccia", "Bruschetta", "Garlic Bread", "Caprese Salad"],
  mainMenu: ["Pizza", "Pasta", "Risotto"],
  order: function(starterIndex, mainIndex) {
      return [this.starterMenu[starterIndex], this.mainMenu[mainIndex]]
  }
};

// Desestruturando primeiro e terceiro item da propriedade 'categories':
let [main, , secondary] = restaurant.categories;
console.log(main, secondary); // > Italian Vegetarian

// Suponha que queremos trocar main (principal) e secondary (secund??ria)
// nas categorias.
// SEM destructuring:
const temp = main;
main = secondary;
secondary = temp;
console.log(main, secondary)    // > Italian Vegetarian
// COM destructuring:
[main, secondary] = [secondary, main]
console.log(main, secondary)    // > Vegetarian Italian

// Recebe 2 valores de retorno de uma fun????o:
const [starter, mainCourse] = restaurant.order(2, 0);
console.log(starter, mainCourse)    // > Garlic Bread Pizza

// Desestruturando arrays aninhados
const nested = [2, 4, [5, 6]];
const [i, , [j, k]] = nested;
console.log(i, j, k)/            // > 2 5 6

// Valores padr??es
const [p, q, r] = [8, 9];
console.log(p, q, r);            // > 8 9 undefined

const [m=1, n=1, o=1] = [3]
console.log(m, n, o)            // > 3 1 1
```

## Objetos

Para desestruturar objetos, n??s usamos as chaves {} porque os objetos s??o criados com elas. Tamb??m precisamos **saber o nome das propriedades** que queremos extrair/desempacotar.

Desestruturar objetos **?? muito ??til**, a partir da edi????o do JS de 2020. Principalmente quando precisamos lidar com APIs, ele mostra sua utilidade. Os dados que v??m das APIs chegam pra gente na forma de objetos e o destructuring ?? uma m??o-na-roda porque acelera a extra????o das informa????es.

De novo, presta bem aten????o no c??digo abaixo porque ele mostra algumas outras coisas que o destructuring consegue fazer com objetos. Melhor mergulhar no c??digo do que escrever texto corrido explicando.

```javascript
// O objeto 'restaurant' tem o objeto 'openingHours' agora como
// propriedade... e o 'openingHours' tem outro objeto dentro de si
// que ?? o thu, fri, sat
const restaurant = {
  name: "Classico Italiano",
  location: "Via Angelo Tavanti 23, Firenze, Italy",
  categories: ["Italian", "Pizzeria", "Vegetarian", "Organic"],
  starterMenu: ["Focaccia", "Bruschetta", "Garlic Bread", "Caprese Salad"],
  mainMenu: ["Pizza", "Pasta", "Risotto"],
  order: function(starterIndex, mainIndex) {
      return [this.starterMenu[starterIndex], this.mainMenu[mainIndex]]
  }
  orderDelivery: function ( {starterIndex = 1, mainIndex = 0, time = '20:00', address}) {
      console.log(`Order received! ${this.starterMenu[starterIndex]} and ${this.mainMenu[mainIndex]} will be delivered to ${address} at ${time}`)
  },
  openingHours: {
      thu: {
          open: 12,
          close: 22,
      },
      fri: {
          open: 11,
          close: 23,
      },
      sat: {
          open: 0,  // Open 24hs
          close: 24,
      },
  }
};

// Desestruturando em 3 propriedades: name, openingHours, categories
// ps: a gente precisa saber o nome das propriedades pra conseguir fazer isso
const { name, openingHours, categories } = restaurant;
console.log(name, openingHours, categories);

// E se a gente quisesse que as vari??veis que guardam a informa????o
// extra??da tivesse outro nome, e n??o o nome da pr??pria proriedade?
// D?? pra mudar. Aqui abaixo como fazer isso (mas ainda precisamos)
// saber o nome da propriedade pra fazer isso)
// const {nomeDaPropriedade: novoNomeDaVariavel} = objeto;
const {name: restaurantName, openingHours: hours} = restaurant;

// Valores padr??es + combinar com novos nomes de vari??veis
const { menu = [], starterMenu: starters = [] } = restaurant;
console.log(menu, starters);        // > [] ['Focacia', etc etc]

// Vari??veis que mutacionam
let a = 111;
let b = 999;
const obj = {a: 23, b: 7, c: 14};

{a, b} = obj;       // Erro! JS v?? as chaves e espera um objeto
                    // Precisa consertar esse erro adicionando par??nteses
( {a, b} ) = obj;
console.log(a, b)   // > 23 7

// Objetos aninhados
const { fri: {open, close} } = openingHours;
console.log(open, close)        // > 11 23

// Passar um objeto como argumento de fun????o dentro do m??todo 'orderDelivery'
restaurant.orderDelivery{
    time: '22:30',
    address: 'Via del Sole, 21',
    mainIndex: 2,
    starterIndex: 2,
}
// Acima ?? importante: a gente n??o passou 4 argumentos, a gente
// apenas passou 1 objeto (chaves) como argumento. A ordem dentro
// de um objeto n??o importa
```
