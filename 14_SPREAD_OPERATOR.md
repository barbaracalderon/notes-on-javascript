# EN: The Spread Operator ...

The Spread Operator is simbolized with three dots.

It's a bit like destructuring because it extracts values from **iterables AND objects** (as you know, the object is not iterable). The possibility to work it with objects is quite recent!

**ITERABLES: arrays, strings, maps, sets.**

The main difference between destructuring and the spread operator is the latter takes **all the elements** from inside the iterable and **does not store them into new variables**.

It's specially useful when copying an array and adding something extra to it. It can also be passed as a function parameter.

Beware: must be only used in places where we want the values separated by commas, not the whole array with brackets.

```javascript
// Old way to copy an Array and add something extra
const arr = [7, 8, 9];
const badNewArr = [1, 2, arr[0], arr[1], arr[2]];

// Spread Operator does the same thing but better practice
const newGoodArr = [1, 2, ...arr];

// (The object 'restaurant'is back for example purporses)
const restaurant = {
  name: "Classico Italiano",
  location: "Via Angelo Tavanti 23, Firenze, Italy",
  categories: ["Italian", "Pizzeria", "Vegetarian", "Organic"],
  starterMenu: ["Focaccia", "Bruschetta", "Garlic Bread", "Caprese Salad"],
  mainMenu: ["Pizza", "Pasta", "Risotto"],
  order: function(starterIndex, mainIndex) {
      return [this.starterMenu[starterIndex], this.mainMenu[mainIndex]]
  },
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
  },
  orderPasta: function (ing1, ing2, ing3) {
      console.log(`Here's your delicious pasta with ${ing1}, ${ing2}, ${ing3}!`)
  }
};

// Let's copy an array
const mainMenuCopy = [...restaurant.mainMenu];

// Join 2 arrays
const menu = [...restaurant.starterMenu, ...restaurant.mainMenu];

// Iterables: arrays, string, maps, sets
const str = 'Jonas';
const letters = [...str];
console.log(letters)            // > ['J', 'o', 'n', 'a', 's']
console.log(...str)             // > J o n a s

// The object restaurant has a new method: orderPasta that
// takes 3 arguments as ingredients
// Let's get the ingredients from a prompt window
const ingredients = [           // This is an array
    prompt("Let's make pasta! Ingredient 1?"),
    prompt("Ingredient 2? "),
    prompt("Ingredient 3? ")
]

// Spread operator passed as a function paramether
// It writes the ingredients separated by commas (3 arguments)
restaurant.orderPasta(...ingredients);

// Objects
// Let's copy the 'restaurant' object and add something extra
const newRestaurant = { foundedIn: 1998, ...restaurant, founder: 'Giuseppe'};
console.log(newRestaurant);

// It makes shallow copies
const restaurantCopy = {...restaurant};
restaurantCopy.name = 'Ristorante Roma';
console.log(restaurantCopy.name);       // > Ristorante Roma
console.log(restaurant.name);           // > Classico Italiano

```

---

# PT: O Operador "Spread" ...

O Operador Spread é simbolizado com três pontos.

É um pouco como o destructuring porque ele extrai valores de **iteráveis E objetos** (como você sabe, o objeto não é iterável). A possibilidade de trabalhar com objetos é bem recente.

**ITERÁVEIS: arrays, strings, maps, sets.**

A principal diferença entre o destructuring e o operador spread é que esse último extrai **todos os elementos** de dentro de um iterável e **não guarda eles em novas variáveis**.

É útil para copiar arrays e adicionar alguma coisa extra. Também pode ser passado como parâmetro de uma função.

Cuidado: só deve ser usado em locais em que a gente quer os valores separados por vírgulas, não o array todo com as chaves.

```javascript
// Jeito antigo de copiar um Array e adicionar algo extra:
const arr = [7, 8, 9];
const badNewArr = [1, 2, arr[0], arr[1], arr[2]];

// Operador Spread faz a mesma coisa mas com prática melhor:
const newGoodArr = [1, 2, ...arr];

// (O objeto 'restaurant' tá de volta pra servir de exemplos. Tava no arquivo passado)
const restaurant = {
  name: "Classico Italiano",
  location: "Via Angelo Tavanti 23, Firenze, Italy",
  categories: ["Italian", "Pizzeria", "Vegetarian", "Organic"],
  starterMenu: ["Focaccia", "Bruschetta", "Garlic Bread", "Caprese Salad"],
  mainMenu: ["Pizza", "Pasta", "Risotto"],
  order: function(starterIndex, mainIndex) {
      return [this.starterMenu[starterIndex], this.mainMenu[mainIndex]]
  },
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
  },
  orderPasta: function (ing1, ing2, ing3) {
      console.log(`Here's your delicious pasta with ${ing1}, ${ing2}, ${ing3}!`)
  }
};

// Vamos copiar um array
const mainMenuCopy = [...restaurant.mainMenu];

// Juntar 2 arrays
const menu = [...restaurant.starterMenu, ...restaurant.mainMenu];

// Iteráveis: arrays, string, maps, sets
const str = 'Jonas';
const letters = [...str];
console.log(letters)            // > ['J', 'o', 'n', 'a', 's']
console.log(...str)             // > J o n a s

// O objeto 'restaurant' tem um novo método: order Pasta que recebe
// 3 argumentos como ingredientes. Vamos pegar os ingredientes de uma
// janela prompt com o usuário
const ingredients = [           // É um array bem aqui
    prompt("Let's make pasta! Ingredient 1?"),
    prompt("Ingredient 2? "),
    prompt("Ingredient 3? ")
]

// Operador Spread passado como um parâmetro de função
// Ele escreve os ingredientes separados por vírgulas (3 argumentos)
restaurant.orderPasta(...ingredients);

// Objetos
// Vamos copiar o objeto 'restaurant' e adicionar algo extra
const newRestaurant = { foundedIn: 1998, ...restaurant, founder: 'Giuseppe'};
console.log(newRestaurant);

// Ele faz cópias rasas (vimos algo sobre isso no arquivo 11)
const restaurantCopy = {...restaurant};
restaurantCopy.name = 'Ristorante Roma';
console.log(restaurantCopy.name);       // > Ristorante Roma
console.log(restaurant.name);           // > Classico Italiano

```
