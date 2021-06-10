# EN: Loops

Loops are fundamental to every programming language. They help making repetitive tasks automatic.

## `For` Loop (counter)

It's a loop statement with a counter.

First parameter is a counter. Second parameter is a condition for when it stops. The for loop keeps running while condition is `true`. The third parameter is the **counter increasing**. It will increase so the condition becomes `false`... that is when it stops.

### Loop through an Array

Here's an example.

```javascript
for (let rep = 1; rep <= 10; rep++) {
  console.log(`Lifting weight repetition ${rep}`);
}
```

There are two things we can do:

1. Read an array
2. Fill an array

### Read an Array

```javascript
// 1. Read an Array
const jonasArray = [
  "Jonas",
  "Schmedtmann",
  2037 - 1991,
  "teacher",
  ["Michael", "Peter", "Steven"],
  true,
];

for (let i = 0; i < jonasArray.length; i++) {
  console.log(jonasArray[i], typeof jonasArray[i]);
}

// i = 0 -> It starts at array item index 0
// i < jonasArray.length -> Last array item is positioned at index length - 1
// i++ -> Increase by one each time it loops
```

### Fill an Array

Now, let's fill an array.

```javascript
// 2. Fill an Array
const jonasArray = [
  "Jonas",
  "Schmedtmann",
  2037 - 1991,
  "teacher",
  ["Michael", "Peter", "Steven"],
  true,
];

const types = [];
for (let i = 0; i < jonasArray.length; i++) {
  types[i] = typeof jonasArray[i];
}

// We could also have done:
const types = [];
for (let i = 0; i < jonasArray.length; i++) {
  types.push(typeof jonasArray[i]);
}

console.log(types);
// > ["string", "string", "number", "string", "object", "boolean"]

// types[i] -> Each item in the empty "types" array
```

### Continue vs Break

Both finish the loop, so it **won't read the next line** in the loop.

Two important keywords in the for loop: `continue` and `break`.

**CONTINUE**: cease the _current_ loop.

**BREAK**: shut down the _whole_ loop. It terminates it.

```javascript
// Continue
// PS: Consider the previous jonasArray

for (let i = 0; i < jonasArray.length; i++) {
  if (typeof jonasArray[i] !== "string") continue; // continue keyword
  console.log(jonasArray[i], typeof jonasArray[i]);
}

// Break
// PS: Also consider the previous jonasArray

for (let i = 0; i < jonasArray.length; i++) {
  if (typeof jonasArray[i] === "number") break; // break keyword
  console.log(jonasArray[i], typeof jonasArray[i]);
}
```

### Looping Backwards

```javascript
const jonasArray = [
    'Jonas',
    'Schmedtmann',
    2037 - 1991,
    'teacher',
    ['Michael', 'Peter', 'Steven'],
    true
]

for (let i = jonasArray.length - 1; i > = 0; i--) {
    console.log(i, jonasArray[i]);
}

/*
> 5 true
> 4 ["Michael", "Peter", "Steven"]
> 3 "teacher"
> 2 46
> 1 "Schmedtmann"
> 0 "Jonas"
*/
```

### Loop in Loops

```javascript
for (let exercise = 1; exercise < 4; exercise++) {
  // Loop #01
  console.log(`--- Starting Exercise ${exercise} ---`);

  for (let rep = 1; rep < 6; rep++) {
    // Loop #02
    console.log(`Exercise ${exercise}: Lifting weight repetition ${rep}`);
  }
}
```

## `While` Loop - (condition)

A while loop does not require a counter. It requires only a condition.

You should use a while loop whenever you don't know how many times to execute an specific task. Therefore, if you only depend on condition (and not condition and a counter), there are more situations to use a while loop.

_PS: feel free to use a counter for a specific problem. But the structure of the while does not depend on it. It depends only on the condition._

But just for starters, let's use a counter and get it out of the way already. Let's solve a specific problem with a counter.

The same one we were dealing with before.

```javascript
// While loops (with a counter)

let rep = 1;
while (rep <= 10) {
  console.log(`WHILE: Lifting weights repetition ${rep}`);
  rep++;
}
```

Now let's solve another problem, where counter is not needed to solve it.

It works with a dice. We don't know how many times to iterate the loop yet.

```javascript
// While loops (condition)
let dice = Math.trunc(Math.random() * 6) + 1;

while (dice !== 6) {
  console.log(`You rolled a ${dice}`);
  dice = Math.trunc(Math.random() * 6) + 1;
  if (dice === 6) console.log("Loop is about to end...");
}
```

---

# PT: Loops

Loops, em português "laço", são fundamentais para todas as linguagens de programação. Eles auxiliam a tornar tarefas repetitivas em automáticas.

## Laço `For` (contador)

É um laço com contador.

O primeiro parâmetro é o contador e onde ele inicia. O segundo parâmetro é a condição de parada. O laço for continua rodando enquanto a condição for `true`. O terceiro parâmetro é o **incremento do contador**. Ele vai incrementar até a condição se tornar `false`... que é quando ele para.

### Laçando um Array

Um exemplo abaixo.

```javascript
for (let rep = 1; rep <= 10; rep++) {
  console.log(`Repetição de levantar peso ${rep}`);
}
```

Tem duas coisas que podemos fazer com um laço for:

1. Ler um array
2. Preencher um novo array

### Ler um Array

```javascript
// 1. Ler um Array
const jonasArray = [
  "Jonas",
  "Schmedtmann",
  2037 - 1991,
  "teacher",
  ["Michael", "Peter", "Steven"],
  true,
];

for (let i = 0; i < jonasArray.length; i++) {
  console.log(jonasArray[i], typeof jonasArray[i]);
}

// i = 0 -> Começa no primeiro item do array, índice 0
// i < jonasArray.length -> último item do array está posicioonado no índice de número "tamanho do array" - 1
// i++ -> Incrementa uma unidade cada vez que roda o laço
```

### Preencher um Array

Agora, vamos preencher um array.

```javascript
// 2. Preencher um Array
const jonasArray = [
  "Jonas",
  "Schmedtmann",
  2037 - 1991,
  "teacher",
  ["Michael", "Peter", "Steven"],
  true,
];

const types = [];
for (let i = 0; i < jonasArray.length; i++) {
  types[i] = typeof jonasArray[i];
}

// Também poderíamos ter feito assim:
const types = [];
for (let i = 0; i < jonasArray.length; i++) {
  types.push(typeof jonasArray[i]);
}

console.log(types);
// > ["string", "string", "number", "string", "object", "boolean"]

// types[i] -> Cada item no array que começa vazio "types"
```

### Continue vs Break

Tanto o `continue` quanto o `break` são palavras reservadas do JS que finalizam um laço, assim **não vai ler a próxima linha do laço**.

**CONTINUE**: termina o laço _atual_.

**BREAK**: termina _todo_ o laço. Ele finaliza a operação.

```javascript
// Continue
// PS: Considere o array anterior jonasArray

for (let i = 0; i < jonasArray.length; i++) {
  if (typeof jonasArray[i] !== "string") continue; // continue keyword
  console.log(jonasArray[i], typeof jonasArray[i]);
}

// Break
// PS: Também considere o array anterior jonasArray

for (let i = 0; i < jonasArray.length; i++) {
  if (typeof jonasArray[i] === "number") break; // break keyword
  console.log(jonasArray[i], typeof jonasArray[i]);
}
```

### Fazendo um laço ao contrário (de trás pra frente)

```javascript
const jonasArray = [
    'Jonas',
    'Schmedtmann',
    2037 - 1991,
    'teacher',
    ['Michael', 'Peter', 'Steven'],
    true
]

for (let i = jonasArray.length - 1; i > = 0; i--) {
    console.log(i, jonasArray[i]);
}

/*
> 5 true
> 4 ["Michael", "Peter", "Steven"]
> 3 "teacher"
> 2 46
> 1 "Schmedtmann"
> 0 "Jonas"
*/
```

### Laço dentro de Laço

```javascript
for (let exercise = 1; exercise < 4; exercise++) {
  // Loop #01
  console.log(`--- Começo do Exercício ${exercise} ---`);

  for (let rep = 1; rep < 6; rep++) {
    // Loop #02
    console.log(`Exercício ${exercise}: Levantamento de peso ${rep}`);
  }
}
```

## Laço `While` - (condição)

Um laço while não requer um contador. Ele requer apenas uma condição.

Você deve usar um laço while sempre que não souber quantas vezes executar uma tarefa específica. Assim, você depende apenas da condição (e não da condição e mais um contador). Existem mais situações para usar um laço while do que um laço for.

_PS: Fica a vontade pra usar um contador pra resolver um problema específico. Mas a estrutura do while não depende dele. Depende apenas da condição._

Mas, só pra começar, vamos usar um contador e mostrar logo como seria pra resolver um problema específico. Vamos resolver um problema que estávamos lidando no laço for. Mesmo código mas agora escrito com um laço while.

```javascript
// Laço While (com contador)

let rep = 1;
while (rep <= 10) {
  console.log(`WHILE: Repetição ${rep} de levantar peso`);
  rep++;
}
```

Agora vamos resolver outro problema, onde o contador não é necessário para resolvê-lo. Nesse problema, usamos um dado. Não sabemos quantas vezes iterar no laço while para resolver a questão.

Se tirarmos 6 no dado, então saímos do laço.

Não tem como saber quantas vezes não iremos tirar o 6.

```javascript
// Laço While (com condição)
let dice = Math.trunc(Math.random() * 6) + 1;

while (dice !== 6) {
  console.log(`Você tirou um ${dice}`);
  dice = Math.trunc(Math.random() * 6) + 1;
  if (dice === 6) console.log("O laço vai terminar...");
}
```
