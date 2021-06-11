# Short Circuiting

The logic operators `&&` and `||` can produce other values besides boolean values of true/false. This is called Short Circuiting. It can be useful to shortcut if/else statements.

There are three properties with these operators:

1. You can use ANY data type with them
2. You can return ANY data type with them
3. Short-circuiting

## `||` (or)

It returns **the first truthy value it gets**, and disconsiders the rest.

```javascript
console.log(3 || "Jonas"); // > 3
console.log("" || "Jonas"); // > Jonas
console.log(true || 0); // > true
console.log(undefined || null); // > null
console.log(undefined || 0 || "" || "Hello" || 23 || null); // > Hello

// Check if it's there (uses object 'restaurant' from previous file)
const guests1 = restaurant.numGuests ? restaurant.numGuests : 10;
console.log(guests1); // > 10
// ps: we can do better with short-circuiting. Check below:
const guests2 = restaurant.numGuests || 10;
console.log(guests2); // > 10
// It's considered an easier method to set default values
// (better than using if/else statements)
// BIG PS: it won't work if we state restaurant.numGuests = 0;
// It does not work with zero
```

## `&&` (or)

It is the opposite of what we saw. The and operator returns **the first falsy value it gets**.

```javascript
console.log(0 && "Jonas"); // > 0
console.log(7 && "Jonas"); // > Jonas
console.log("Hello" && 23 && null && "Jonas"); // > null

// Check if it's not there (uses object 'restaurant' from previous file)
if (restaurant.orderPizza) {
  restaurant.orderPizza("mushrooms", "spinach");
}
// It writes the previous code better, same result:
restaurant.orderPizza && restaurant.orderPizza("mushrooms", "spinach");
```
