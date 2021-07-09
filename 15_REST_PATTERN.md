# EN: Rest Pattern

It is the inverse of the Spread Operator: the Rest Pattern **packs elements into an array**. It has the same syntax with the three dots, but it is used at the LEFT side of the equal sign.

The Rest Pattern **must always be the last element** in the destructuring method (that uses brackets). This is because JS takes all elements from that moment until the end to pack them together inside an array. The only way to know when to stop is when it reaches the last item. This is why Rest Pattern must be the last element. Also, there can **only be one Rest Pattern** in any destructuring method assignment.

Pay close attention to the code below, it's better than explaining.

```javascript
// Compare Spread Operator and Rest Pattern
// SPREAD, because on RIGHT side of =
const arr = [1, 2, ...[3, 4]];
// REST, because on LEFT side of =
const [a, b, ...others] = [1, 2, 3, 4, 5];
console.log(a, b, others)       // > 1 2 [3, 4, 5]
// BOTH sides of =
const [pizza, , risotto, ...otherFood] = [...restaurant.mainMenu, ...restaurant.starterMenu];
console.log(pizza, risotto, otherFood);         // > Pizza Risotto ['Focaccia', 'Bruschetta', 'Garlic Bread', 'Caprese Salad']

// Remember the 'restaurant' object from previous files
// (back for example purposes)
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
  },
  orderPasta: function (ing1, ing2, ing3) {
      console.log(`Here's your delicious pasta with ${ing1}, ${ing2}, ${ing3}!`)
  }
};

// Objects
const { sat, ...weekdays } = restaurant.openingHours;
console.log(weekdays)           // > {thu: {...}, fri: {...}}

// Functions ("Rest Parameters")
const addLog = function (...numbers) {
    console.log(numbers);
}
addLog(2, 3);          // > [2, 3]
addLog(5, 3, 7, 2)     // > [5, 3, 7, 2]

// Functions ("Rest Parameters)
// It can receive ANY amount of arguments with Rest Pattern
const add = function (...numbers) {
    let sum = 0
    for (let i = 0; i < numbers.length; i++) sum += numbers[i];
    console.log(sum);
}
add(2, 3)                   // > 5
add(5, 4, 7, 2)             // > 18
add(8, 2, 5, 3, 2, 1, 4)    // > 25

const x = [23, 5, 7];
add(...x)                   // > 35         Pay attention to this line!
```

---

# PT: Padrão Rest

É o inverso do Operador Spread: o Padrão Rest **empacota elementos pra dentro de um array**. Ele tem a mesma sintaxe com três pontos, mas é usado no lado ESQUERDO do sinal de igual.

O Padrão Rest **deve sempre ser o último elemento** no método desestruturante de escrita (que usa os colchetes). Isso porque o JS pega todos os elementos daquele momento até o final de tudo para empacotar tudo junto dentro de um array. A única forma de saber quando parar é quando chega no último item. Por isso o Padrão Rest precisa ser o último elemento. Além disso, **só dá pra ter um Padrão Rest** em qualquer atividade de desestructuring.

Presta atenção no código abaixo, melhor que explicar por texto.

```javascript
// Vamos comparar o operador Spread e o padrão Rest
// SPREAD, porque está do lado DIREITO do =
const arr = [1, 2, ...[3, 4]];
// REST, porque está do lado ESQUERDO do =
const [a, b, ...others] = [1, 2, 3, 4, 5];
console.log(a, b, others)       // > 1 2 [3, 4, 5]
// Em AMBOS os lados do =
const [pizza, , risotto, ...otherFood] = [...restaurant.mainMenu, ...restaurant.starterMenu];
console.log(pizza, risotto, otherFood);         // > Pizza Risotto ['Focaccia', 'Bruschetta', 'Garlic Bread', 'Caprese Salad']

// Lembra do objeto 'restaurant' dos arquivos anteriores
// (Voltou por motivos de ser usado em exemplos)
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
  },
  orderPasta: function (ing1, ing2, ing3) {
      console.log(`Here is your delicious pasta with ${ing1}, ${ing2}, ${ing3}!`)
  }
};

// Objetos
const { sat, ...weekdays } = restaurant.openingHours;
console.log(weekdays)           // > {thu: {...}, fri: {...}}

// Funções ("Parâmetros Rest")
const addLog = function (...numbers) {
    console.log(numbers);
}
addLog(2, 3);          // > [2, 3]
addLog(5, 3, 7, 2)     // > [5, 3, 7, 2]

// Funções ("Parâmetros Rest")
// Pode receber QUALQUER quantidade de argumentos com o Padrão Rest
const add = function (...numbers) {
    let sum = 0
    for (let i = 0; i < numbers.length; i++) sum += numbers[i];
    console.log(sum);
}
add(2, 3)                   // > 5
add(5, 4, 7, 2)             // > 18
add(8, 2, 5, 3, 2, 1, 4)    // > 25

const x = [23, 5, 7];
add(...x)                   // > 35         Atenção nessa linha!
```
