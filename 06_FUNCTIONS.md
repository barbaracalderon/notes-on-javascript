# EN: Activate "strict mode" in JS

To activate, write this **first thing in your code**.

```javascript
"use strict";
```

It lets you secure your code. It creates visible errors. Strict mode does not let us do some things.

# EN: Functions

Functions allow us to write more maintainable code. This is the core of a basic principle in programming: DRY Code.

- **D**: Don't
- **R**: Repeat
- **Y**: Your
- Code.

In JS, functions are values.

You can `call` a function, `run` it or `invoke` it. They all mean the same thing.

Here's a function example.

```javascript
function fruitProcessor(numApples, numOranges) {
    const juice = `Juice with ${numApples}  apples and ${numOranges} oranges.`}
    return juice
}

const appleJuice = fruitProcessor(5, 0)
console.log(appleJuice)       // > Juice with 5 apples and 0 oranges.

const orangeJuice = fruitProcessor(0, 6)
console.log(orangeJuice)      // > Juice with 0 apples and 6 oranges.

const appleOrangeJuice = fruitProcessor(2, 4)
console.log(appleOrangeJuice) // > Juice with 2 apples and 4 oranges.

// PS: Name of function is in camelCase: fruitProcessor
```

## Function Declaration

```javascript
function calcAge1(birthyear) {
  return 2037 - birthyear;
}

const age1 = calcAge1(1991);
// You can call it now, or you can call it before the actual function

console.log(age1); // > 46
```

## Function Expression

```javascript
const calcAge2 = function (birthyear) {
  return 2037 - birthyear;
};

const age2 = calcAge2(1991);
// You can call it now because you defined it earlier
// You cannot call it before the expression itself: it's an error

console.log(age2); // > 46
```

## Arrow Function

Another shorter way to write Declaration Function.

First, you write the function name, then the arrow `=>`, then what you want to `return`. Be sure to store it inside a variable.

```javascript
// Arrow Function below
// ('return' keyword and '{}' not necessary if it's one line)
const calcAge3 = (birthYear) => 2037 - birthYear;

const age3 = calcAge3(1991);
console.log(age3); // > 46
```

Another example.

```javascript
// Arrow Function below
// ('return' keyword and '{}' necessary because of multiple lines)
const yearsUntilRetirement = (birthYear) => {
  const age = 2037 - birthYear;
  const retirement = 65 - age;
  return retirement;
};

console.log(yearsUntilRetirement(1991)); // > 19
```

Same as before but... with two parameters: birthyear and first name.

```javascript
// Arrow Function below
// (two parameters: '()' are necessary)
const yearsUntilRetirement = (birthYear, firstName) => {
  const age = 2037 - birthYear;
  const retirement = 65 - age;
  return `${firstName} retires in ${retirement} years.`;
};

console.log(yearsUntilRetirement(1991, "Jonas"));
// > Jonas retires in 19 years.
```

## Functions calling other Functions

It's a function inside a function!

```javascript
// Function #01
function cutFruitPieces(fruit) {
  return fruit * 4;
}

// Function #02
function fruitProcessor(apples, oranges) {
  const applePieces = cutFruitPieces(apples);
  const orangePieces = cutFruitPieces(oranges);
  const juice = `Juice with ${applePieces} pieces of apple and ${orangePieces} pieces of orange.`;

  return juice;
}

// The results

console.log(fruitProcessor(2, 3));
// > Juice with 8 pieces of apple and 12 pieces of orange.
```

---

# PT: Ative o modo "stric mode" no JS

Para ativar, digite "stric mode" na primeira linha do c??digo.

```javascript
"use strict";
```

Isso deixa o c??digo mais seguro: cria erros vis??veis no c??digo. O "strict mode" n??o deixa que a gente fa??a algumas coisas.

# PT: Fun????es

As fun????es permitem que se escrevam c??digos sustent??veis, principal pilar da programa????o: DRY Code. Traduzido: "N??o repita seu c??digo".

Em JS, **fun????es s??o valores**.

Voc?? pode chamar uma fun????o ou invoc??-la, ?? a mesma coisa.

Exemplo de fun????o.

```javascript
function fruitProcessor(numMacas, numLaranjas) {
    const suco = `Suco com ${numMacas}  ma????s e ${numLaranjas} laranjas.`}
    return suco
}

const sucoMaca = fruitProcessor(5, 0)
console.log(sucoMaca)       // > Suco com 5 ma????s e 0 laranjas.

const sucoLaranja = fruitProcessor(0, 6)
console.log(sucoLaranja)      // > Suco com 0 ma????s e 6 laranjas.

const sucoMacaLaranja = fruitProcessor(2, 4)
console.log(sucoMacaLaranja) // > Suco com 2 ma????s e 4 laranjas.

// PS: Nome da fun????o ?? em camelCase: fruitProcessor
```

## Fun????o Declarativa

```javascript
function calcIdade1(anoNascimento) {
  return 2037 - anoNascimento;
}

const idade1 = calcIdade1(1991);
// Voc?? pode chamar a fun????o agora, ou poderia chamar antes da pr??pria fun????o em si

console.log(idade1); // > 46
```

## Fun????o Expressiva

```javascript
const calcIdade2 = function (anoNascimento) {
  return 2037 - anoNascimento;
};

const idade2 = calcIdade2(1991);
// Voc?? pode chamar a fun????o agora porque voc?? a definiu antes
// Voc?? n??o pode cham??-la antes de defini-la: d?? um erro

console.log(idade2); // > 46
```

## Arrow Function

?? um jeito mais curto de escrever Fun????es Declarativas.

Primeiro, tem que escrever o nome da fun????o, depois a setinha `=>`, depois o que voc?? quer retornar (`return`). Coloque esse resultado dentro de uma vari??vel.

```javascript
// Arrow Function abaixo
// ('return' e '{}' n??o s??o necess??rios se ?? s?? uma linha)
const calcIdade3 = (anoNascimento) => 2037 - anoNascimento;

const idade3 = calcIdade3(1991);
console.log(idade3); // > 46
```

Outro exemplo.

```javascript
// Arrow Function abaixo
// ('return' e '{}' obrigat??rios porque tem m??ltiplas linhas)

const anosAteAposentar = (anoNascimento) => {
  const idade = 2037 - anoNascimento;
  const aposentadoria = 65 - idade;
  return aposentadoria;
};

console.log(anosAteAposentar(1991)); // > 19
```

O pr??ximo c??digo ?? o mesmo que o anterior... mas com dois par??metros: ano de nascimento e primeiro nome.

_PS: Par??metro ?? o espa??o reservado para colocar o valor. Argumento ?? o valor que o usu??rio escolhe para colocar como par??metro da fun????o._

```javascript
// Arrow Function abaixo
// (dois par??metros: '()' ?? obrigat??rio)

const anosAteAposentar = (anoNascimento, primeiroNome) => {
  const idade = 2037 - anoNascimento;
  const aposentadoria = 65 - idade;
  return `${primeiroNome} se aposenta em ${aposentadoria} anos.`;
};

console.log(anosAteAposentar(1991, "Jonas"));
// > Jonas se aposenta em 19 anos.
```

## Fun????o chamando outra Fun????o

?? uma fun????o dentro de outra fun????o.

```javascript
// Fun????o #01
function cortarFrutaPedacos(fruta) {
  return fruta * 4;
}

// Function #02
function fruitProcessor(macas, laranjas) {
  const pedacosMaca = cortarFrutaPedacos(macas);
  const pedacosLaranja = cortarFrutaPedacos(laranjas);
  const suco = `Suco com ${pedacosMaca} peda??os de ma???? e ${pedacosLaranja} peda??os de laranja.`;

  return suco;
}

// O resultado

console.log(fruitProcessor(2, 3));
// > Suco com 8 peda??os de ma???? e 12 peda??os de laranja.
```
