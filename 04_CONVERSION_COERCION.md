# EN: Conversion

## Template String

```javascript
const userName = "Jonas";
const job = "Teacher";

console.log(`Hello, I'm ${userName} the ${job}.`);
// > Hello, I'm Jonas the Teacher.
```

## String to Number `Number()`

```javascript
const inputYear = "1991";
console.log(Number(inputYear)); // string -> number
// > 1991
```

We cannot convert names to numbers.

```javascript
const inputYear = "Jonas";
console.log(Number(inputYear)); // Error: invalid number
// > NaN
```

## Number to String `String()`

```javascript
console.log(String(23)); // number -> string
// > '23'
```

# Coercion

## Type Coercion

JS forces a coercion to "adjust" things. So, some things happen automatically behind the scenes. In the cases below, it forces string -> number.

Except the **plus sign**.

```javascript
console.log("I am " + 23 + "years old.");
// > 23 (String)
// Done automatically, no Errors triggered

console.log("23" - "10" - 3);
// > 10 (Number)
// Minus (-) forces coercion to number

console.log("23" + "10" + 3);
// > 23103 (String)

console.log("23" * "2");
// > 46 (Number)

console.log("23" / "2");
// 11.5 (Number)
```

## Falsy Values

They are not yet false values but they will become false if we try to convert them into a boolean. Everything else is a truthy value.

Falsy values are: `0, '', undefined, null, NaN`

```javascript
console.log(Boolean(0)); // > false
console.log(Boolean("")); // > false
console.log(Boolean(undefined)); // > false
console.log(Boolean(null)); // > false
console.log(Boolean(NaN)); // > false
```

---

# PT: Conversão

## Template String

Usar variáveis dentro de strings.

```javascript
const userName = "Jonas";
const profissao = "Professor";

console.log(`Oi, eu sou ${userName} o ${profissao}.`);
// > Oi, eu sou Jonas o Professor.
```

## String para Number `Number()`

```javascript
const inputYear = "1991";
console.log(Number(inputYear)); // string -> number
// > 1991
```

Não vale para nomes na string.

```javascript
const inputYear = "Jonas";
console.log(Number(inputYear)); // Error: número invalido (NaN)
// > NaN
```

## Number para String `String()`

```javascript
console.log(String(23)); // number -> string
// > '23'
```

# Coerção ("forçar")

## Coerção de Tipagem

JS força a coerção para "ajustar" as coisas. Então, em alguns casos é feito de modo automático. Nos casos abaixo, ele força string -> number.

Exceto com o sinal de **adição**.

```javascript
console.log("Eu tenho" + 23 + "anos.");
// > 23 (String)
// Feito automaticamente, nenhum Erro é apontado

console.log("23" - "10" - 3);
// > 10 (Number)
// O Menos (-) força a coerção para número

console.log("23" + "10" + 3);
// > 23103 (String)

console.log("23" * "2");
// > 46 (Number)

console.log("23" / "2");
// 11.5 (Number)
```

## Valores Falsos

Ainda não são valores falsos mas se tornam falsos quando a gente tenta convertê-los para um booleano. Todo o resto, que não são esses, são valores verdadeiros (truthy values).

Falsy values são: `0, '', undefined, null, NaN`

```javascript
console.log(Boolean(0)); // > false
console.log(Boolean("")); // > false
console.log(Boolean(undefined)); // > false
console.log(Boolean(null)); // > false
console.log(Boolean(NaN)); // > false
```
