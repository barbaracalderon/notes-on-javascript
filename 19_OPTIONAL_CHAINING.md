# EN: Optional Chaining `?.`

Let's say we gotta get the opening hours of our restaurant for mondays. But the value is undefined... we just don't know that. We don't know if the restaurant opens on mondays.

_PS: This is based on previous restaurant code in the previous files._
```javascript
// Object openingHours
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

// Object restaurant with object openingHours in it
const restaurant = {
    openingHours
}

// Old way of checking if the restaurant is open on mondays
// (We know it's not open: it only opens at thursday, friday, saturday)
if (restaurant.openingHours.mon) console.log
(restaurant.openingHours.mon.open);     // > undefined
                                        // This is what it shows "undefined"

// But... how do we know if the restaurant has opening hours?
// We don't know that. We assume it does and we're checking if it opens on mondays
// What if we ALSO check if it's got opening hours?
// This is the old way of checking both (openingHours and mon):
if (restaurant.openingHours && restaurant.openingHours.mon)
 console.log(restaurant.openingHours.mon.open)
// If both are true, console log will show when open
```

But there's a much better solution. This was recently introduced to JS, in 2020: **Optional Chaining** `?.`

### Only if the property before ?. then the "open" property will be read.

How could we check both (openingHours and monday.open)?

```javascript
// WITH Optional Chaining:
console.log(restaurant.openingHours.mon?.open);
// Only if the property before ?. then the open property will be read.
// If not, the undefined property will be read.

// Below, we'll check both properties (similar to using &&):
console.log(restaurant.openingHours?.mon?.open);
// We're checking openingHours and if it exists, we're checking mon
```

We can loop through an array and check the opening hours for each week day. 

Here's how we do it.

```javascript
const days = ['mon', 'tue', 'wed', 'thu', 'fri', 'sat', 'sun'];
for (const day of days) {             // Use of "For Of" Loop
    const open = restaurant.openingHours[day]?.open;
    console.log(`On ${day}, we open at ${open}`);
}
// What console.log shows:
// > On mon, we open at undefined
// > On tue, we open at undefined
// > On wed, we open at undefined
// > On thu, we open at 12
// > On fri, we open at 11
// > On sat, we open at 0
// > On sun, we open at undefined
```