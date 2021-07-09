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

## `&&` (and)

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

## `??` (The Nullish Coalescing Operator)

It 'corrects' a default mistake when we set a variable to zero (falsy value).

It returns its right operator when its left operator is null or undefined. If it's not null or undefined, then it returns the left operator.

```javascript
// Original set default value using or (||)
restaurant.numGuests = 0;
const guests = restaurant.numGuests || 10;
console.log(guests); // > 10

// Nullish Coalescing Operator
restaurant.numGuests = 0;
const guestsCorrect = restaurant.numGuests ?? 10;
console.log(guestsCorrect); // > 0
// Only when restaurant.numGuests is not a nullish value that it will
// take it. In this case, 0 (because we set it to zero).
// When restaurant.numGuests is nullish value, it would take 10.
```

---

# PT: Circuito Curto (Short Circuiting)

Tradução livre aqui.

Os operadores lógicos `&&` e `||` podem produzir outros valores além dos booleanos de true/false. Isso é chamado de Short Circuiting. Pode ser útil como atalho para blocos do tipo if/else.

Existem três propriedades com esses operadores:

1. Você pode usar QUALQUER tipo de dado com eles
2. Você pode retornar QUALQUER tipo de dado com eles
3. Short-circuiting

## `||` (ou)

Ele retorna **o primeiro valor truthy que encontra** e desconsidera todo o resto.

```javascript
console.log(3 || "Jonas"); // > 3
console.log("" || "Jonas"); // > Jonas
console.log(true || 0); // > true
console.log(undefined || null); // > null
console.log(undefined || 0 || "" || "Hello" || 23 || null); // > Hello

// Verifica se tá lá (usamos o objeto 'restaurant' do arquivo anterior)
const guests1 = restaurant.numGuests ? restaurant.numGuests : 10;
console.log(guests1); // > 10
// ps: Dá pra fazer melhor com short-circuiting. Vamos usar:
const guests2 = restaurant.numGuests || 10;
console.log(guests2); // > 10
// É considerado um método mais fácil pra setar (definir) valores padrões
// (melhor que usar blocos do tipo if/else)
// GRANDE PS: não vai funcionar se a gente coloca restaurant.numGuests = 0;
// Não funciona com zero
```

## `&&` (e)

É o oposto do que vimos. O operador E retorna **o primeiro valor falsy que encontra**.

```javascript
console.log(0 && "Jonas"); // > 0
console.log(7 && "Jonas"); // > Jonas
console.log("Hello" && 23 && null && "Jonas"); // > null

// Verifica se não tá lá (objeto 'restaurant' vista antes)
if (restaurant.orderPizza) {
  restaurant.orderPizza("mushrooms", "spinach");
}
// Ele escreve o código das linhas acima de forma melhor, mesmo resultado:
restaurant.orderPizza && restaurant.orderPizza("mushrooms", "spinach");
```

## `??` (O Operador Nullish Coalescing)

Nullish é de nulo. Coalescing é de fundir. Operador de Coalescência Nula.

Esse operador "corrige" um erro padrão que é quando defininimos a variável pra zero (valor falsy).

Ele retorna o operando do lado direito quando o seu operador do lado esquerdo é null ou undefined. Caso contrário, ele retorna o seu operador do lado esquerdo.

```javascript
// Original - definindo valor papdrão usando "ou" (||)
restaurant.numGuests = 0;
const guests = restaurant.numGuests || 10;
console.log(guests); // > 10

// Operador de Coalescência Nula
restaurant.numGuests = 0;
const guestsCorrect = restaurant.numGuests ?? 10;
console.log(guestsCorrect); // > 0
// Só quando o restaurant.numGuests não é valor nulo que ele vai aceitar.
// Nesse caso, 0 (porque definimos como zero). Quando
// restaurant.numGuests é um valor nulo, ele recebe o 10.
```
