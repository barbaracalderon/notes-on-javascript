# EN: Optional Chaining `?.`

Let's say we gotta get the opening hours of our restaurant for mondays. But the value is undefined... we just don't know that.

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
// (We know it's not: it only opens at thursday, friday, saturday)
if (restaurant.openingHours.mon) console.log
(restaurant.openingHours.mon.open);     // > undefined

 

```