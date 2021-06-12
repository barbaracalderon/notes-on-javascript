# EN: Enhanced Object Literals

Fresh new.

Three improved ways to treat object literals:

1. Object inside an object;
2. Writing methods;
3. Property name comes from an array;

Check below.

```javascript
// 1. Object inside object (example openingHours)
const openingHours = {
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
};

const restaurant = {                // Shortened version
    openingHours: openingHours     // BEFORE
};

const restaurantNew = {             // Still shortened version
    openingHours                   // NOW
}

// 2. Writing methods
// BEFORE: function keyword was written
const restaurant = {
    orderPasta: function (ing1, ing2, ing3) {
        console.log(`Here's your delicious pasta with ${ing1}, ${ing2}, ${ing3}!`)
  },
    order: function(starterIndex, mainIndex) {
      return [this.starterMenu[starterIndex], this.mainMenu[mainIndex]]
  },
    orderDelivery: function ( {starterIndex = 1, mainIndex = 0, time = '20:00', address}) {
      console.log(`Order received! ${this.starterMenu[starterIndex]} and ${this.mainMenu[mainIndex]} will be delivered to ${address} at ${time}`)
  },
};

// NOW: removed function keyword and ':'
const restaurantNew = {
    orderPasta(ing1, ing2, ing3) {
        console.log(`Here's your delicious pasta with ${ing1}, ${ing2}, ${ing3}!`)
  },
    order(starterIndex, mainIndex) {
      return [this.starterMenu[starterIndex], this.mainMenu[mainIndex]]
  },
    orderDelivery( {starterIndex = 1, mainIndex = 0, time = '20:00', address}) {
      console.log(`Order received! ${this.starterMenu[starterIndex]} and ${this.mainMenu[mainIndex]} will be delivered to ${address} at ${time}`)
  },
};

// 3. Property name comes from an array
const weekdays = ['mon', 'tue', 'wed', 'thu', 'fri', 'sat', 'sun'];
const openingHours = {
    [weekdays[0]]: {
        open: 12;
        close: 22;
    },
    [weekdays[4]]: {
        open: 19;
        close: 23h;
    }
};
```

---

# PT: Melhorias em Object Literals

Saiu do forno.

Três melhorias no tratamento de object literals:

1. Objeto dentro de objeto;
2. Escrita de métodos;
3. Nome da propriedade vem de um array;

Olhadinha abaixo.

```javascript
// 1. Objeto dentro de objeto (exemplo com 'openingHours')
const openingHours = {
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
};

const restaurant = {
    openingHours: openingHours     // ANTES
};

const restaurantNew = {
    openingHours                   // AGORA
}

// 2. Escrita de métodos
// ANTES: palavra-chave 'function' presente e dois pontos ':'
const restaurant = {
    orderPasta: function (ing1, ing2, ing3) {
        console.log(`Here's your delicious pasta with ${ing1}, ${ing2}, ${ing3}!`)
  },
    order: function(starterIndex, mainIndex) {
      return [this.starterMenu[starterIndex], this.mainMenu[mainIndex]]
  },
    orderDelivery: function ( {starterIndex = 1, mainIndex = 0, time = '20:00', address}) {
      console.log(`Order received! ${this.starterMenu[starterIndex]} and ${this.mainMenu[mainIndex]} will be delivered to ${address} at ${time}`)
  },
};

// AGORA: palavra-chave 'function' removida junto com os dois pontos ':'
const restaurantNew = {
    orderPasta(ing1, ing2, ing3) {
        console.log(`Here's your delicious pasta with ${ing1}, ${ing2}, ${ing3}!`)
  },
    order(starterIndex, mainIndex) {
      return [this.starterMenu[starterIndex], this.mainMenu[mainIndex]]
  },
    orderDelivery( {starterIndex = 1, mainIndex = 0, time = '20:00', address}) {
      console.log(`Order received! ${this.starterMenu[starterIndex]} and ${this.mainMenu[mainIndex]} will be delivered to ${address} at ${time}`)
  },
};

// 3. Nome da propriedade vem de um array
const weekdays = ['mon', 'tue', 'wed', 'thu', 'fri', 'sat', 'sun'];
const openingHours = {
    [weekdays[0]]: {
        open: 12;
        close: 22;
    },
    [weekdays[4]]: {
        open: 19;
        close: 23h;
    }
};
```
