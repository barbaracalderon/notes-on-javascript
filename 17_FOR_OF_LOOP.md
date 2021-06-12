# EN: The "For Of" Loop

This is brand new, from 2020. It's a new way to loop through an array.

```javascript
// Object 'restaurant'
const restaurant = {
  name: "Classico Italiano",
  location: "Via Angelo Tavanti 23, Firenze, Italy",
  categories: ["Italian", "Pizzeria", "Vegetarian", "Organic"],
  starterMenu: ["Focaccia", "Bruschetta", "Garlic Bread", "Caprese Salad"],
  mainMenu: ["Pizza", "Pasta", "Risotto"],
};

// Let's unite all menus:
const menu = [...restaurant.starterMenu, ...restaurant.mainMenu];

// Let's loop through all the items in menu:
for (const item of menu) console.log(item);
// > Foccacia
// > Bruschetta
// > Garlic Bread
// > Caprese Salad
// > Pizza
// > Pasta
// > Risotto

// Let's loop through all the items and their index in menu (.entries()):
for (const item of menu.entries()) {
  console.log(item);
}
// > [0, 'Foccacia']
// > [1, 'Bruschetta']
// > [2, 'Garlic Bread']
// > [3, 'Caprese Salad']
// > [4, 'Pizza']
// > [5, 'Pasta']
// > [6, 'Risotto']

// ...However, we can also unpack it with the spread operator:
for (const [i, elemen] of menu.entries()) {
  console.log(`${i}: ${elemen}`);
}
// > 0: Foccacia
// > 1: Bruschetta
// > 2: Garlic Bread
// > 3: Caprese Salad
// > 4: Pizza
// > 5: Pasta
// > 6: Risotto
```

---

# EN: O Laço "For Of"

É recente, de 2020. É um novo jeito de percorrer um array.

```javascript
// Objeto 'restaurant'
const restaurant = {
  name: "Classico Italiano",
  location: "Via Angelo Tavanti 23, Firenze, Italy",
  categories: ["Italian", "Pizzeria", "Vegetarian", "Organic"],
  starterMenu: ["Focaccia", "Bruschetta", "Garlic Bread", "Caprese Salad"],
  mainMenu: ["Pizza", "Pasta", "Risotto"],
};

// Vamos unir todos os menus:
const menu = [...restaurant.starterMenu, ...restaurant.mainMenu];

// Vamos iterar por todos os itens do menu:
for (const item of menu) console.log(item);
// > Foccacia
// > Bruschetta
// > Garlic Bread
// > Caprese Salad
// > Pizza
// > Pasta
// > Risotto

// Vamos iterar por todos os itens e seus respectivos índices (.entries()):
for (const item of menu.entries()) {
  console.log(item);
}
// > [0, 'Foccacia']
// > [1, 'Bruschetta']
// > [2, 'Garlic Bread']
// > [3, 'Caprese Salad']
// > [4, 'Pizza']
// > [5, 'Pasta']
// > [6, 'Risotto']

// ...Mas também dá pra desempacotar os itens com o operador Spread:
for (const [i, elemen] of menu.entries()) {
  console.log(`${i}: ${elemen}`);
}
// > 0: Foccacia
// > 1: Bruschetta
// > 2: Garlic Bread
// > 3: Caprese Salad
// > 4: Pizza
// > 5: Pasta
// > 6: Risotto
```
