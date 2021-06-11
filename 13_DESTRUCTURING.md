# Destructuring Arrays and Objects

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
console.log(name, openingHours, categories);     // >

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
