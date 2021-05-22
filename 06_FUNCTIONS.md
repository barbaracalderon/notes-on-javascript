
# EN: Activate "strict mode" in JS

To activate, write this **first thing in your code**.

```javascript
'use strict';
```
It lets you secure your code. It creates visible errors.  Strict mode does not let us do some things.

# EN: Functions

Functions allow us to write more maintainable code. This is the core of a basic principle in programming: DRY Code.

- **D**: Don't
- **R**: Repeat
- **Y**: Your
- Code.

In JS, functions are values.

You can ```call``` a function, ```run``` it or ```invoke``` it. They all mean the same thing.

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

console.log(age1)           // > 46
```

## Function Expression

```javascript
const calcAge2 = function (birthyear) {
    return 2037 - birthyear;
}

const age2 = calcAge2(1991);   
// You can call it now because you defined it earlier
// You cannot call it before the expression itself: it's an error

console.log(age2)           // > 46
```

## Arrow Function

Another shorter way to write Declaration Function.

First, you write the function name, then the arrow ```=>```, then what you want to ```return```. Be sure to store it inside a variable.


```javascript
// Arrow Function below 
// ('return' keyword and '{}' not necessary if it's one line)
const calcAge3 = birthYear => 2037 - birthYear;

const age3 = calcAge3(1991);
console.log(age3)       // > 46
```

Another example.

```javascript
// Arrow Function below
// ('return' keyword and '{}' necessary because of multiple lines)
const yearsUntilRetirement = birthYear => {
    const age = 2037 - birthYear;
    const retirement = 65 - age;
    return retirement
}

console.log(yearsUntilRetirement(1991));    // > 19
```

Same as before but... with two parameters: birthyear and first name.

```javascript
// Arrow Function below
// (two parameters: '()' are necessary)
const yearsUntilRetirement = (birthYear, firstName) => {
    const age = 2037 - birthYear;
    const retirement = 65 - age;
    return `${firstName} retires in ${retirement} years.`
}

console.log(yearsUntilRetirement(1991, 'Jonas'));
// > Jonas retires in 19 years.
```

## Functions calling other Functions

It's a function inside a function!

```javascript

// Function #01
function cutFruitPieces(fruit) {
    return fruit * 4
}

// Function #02
function fruitProcessor(apples, oranges) {
    const applePieces = cutFruitPieces(apples);
    const orangePieces = cutFruitPieces(oranges)
    const juice = `Juice with ${applePieces} pieces of apple and ${orangePieces} pieces of orange.`

    return juice
}

// The results

console.log(fruitProcessor(2, 3));
// > Juice with 8 pieces of apple and 12 pieces of orange.
```

---
---

# PT: Ative o modo "stric mode" no JS

Para ativar, digite "stric mode" na primeira linha do código.

```javascript
'use strict';
```

Isso deixa o código mais seguro: cria erros visíveis no código. O "strict mode" não deixa que a gente faça algumas coisas.

# PT: Funções

As funções permitem que se escrevam códigos sustentáveis, principal pilar da programação: DRY Code. Traduzido: "Não repita seu código". 

Em JS, **funções são valores**.

Você pode chamar uma função ou invocá-la, é a mesma coisa.

Exemplo de função.

```javascript
function fruitProcessor(numMacas, numLaranjas) {
    const suco = `Suco com ${numMacas}  maçãs e ${numLaranjas} laranjas.`}
    return suco
}

const sucoMaca = fruitProcessor(5, 0)
console.log(sucoMaca)       // > Suco com 5 maçãs e 0 laranjas.

const sucoLaranja = fruitProcessor(0, 6)
console.log(sucoLaranja)      // > Suco com 0 maçãs e 6 laranjas.

const sucoMacaLaranja = fruitProcessor(2, 4)
console.log(sucoMacaLaranja) // > Suco com 2 maçãs e 4 laranjas.

// PS: Nome da função é em camelCase: fruitProcessor
```

## Função Declarativa

```javascript
function calcIdade1(anoNascimento) {
    return 2037 - anoNascimento;
}

const idade1 = calcIdade1(1991);
// Você pode chamar a função agora, ou poderia chamar antes da própria função em si

console.log(idade1)           // > 46
```

## Função Expressiva

```javascript
const calcIdade2 = function (anoNascimento) {
    return 2037 - anoNascimento;
}

const idade2 = calcIdade2(1991);
// Você pode chamar a função agora porque você a definiu antes
// Você não pode chamá-la antes de defini-la: dá um erro

console.log(idade2)           // > 46
```

## Arrow Function

É um jeito mais curto de escrever Funções Declarativas.

Primeiro, tem que escrever o nome da função, depois a setinha ```=>```, depois o que você quer retornar (```return```). Coloque esse resultado dentro de uma variável.

```javascript
// Arrow Function abaixo
// ('return' e '{}' não são necessários se é só uma linha)
const calcIdade3 = anoNascimento => 2037 - anoNascimento;

const idade3 = calcIdade3(1991);
console.log(idade3)     // > 46
```
Outro exemplo.

```javascript
// Arrow Function abaixo
// ('return' e '{}' obrigatórios porque tem múltiplas linhas)

const anosAteAposentar = anoNascimento => {
    const idade = 2037 - anoNascimento;
    const aposentadoria = 65 - idade;
    return aposentadoria
}

console.log(anosAteAposentar(1991));        // > 19
```

O próximo código é o mesmo que o anterior... mas com dois parâmetros: ano de nascimento e primeiro nome.

*PS: Parâmetro é o espaço reservado para colocar o valor. Argumento é o valor que o usuário escolhe para colocar como parâmetro da função.*

```javascript
// Arrow Function abaixo
// (dois parâmetros: '()' é obrigatório)

const anosAteAposentar = (anoNascimento, primeiroNome) => {
    const idade = 2037 - anoNascimento;
    const aposentadoria = 65 - idade;
    return `${primeiroNome} se aposenta em ${aposentadoria} anos.`
}

console.log(anosAteAposentar(1991, 'Jonas'));
// > Jonas se aposenta em 19 anos.
```
## Função chamando outra Função

É uma função dentro de outra função.

```javascript

// Função #01
function cortarFrutaPedacos(fruta) {
    return fruta * 4
}

// Function #02
function fruitProcessor(macas, laranjas) {
    const pedacosMaca = cortarFrutaPedacos(macas);
    const pedacosLaranja = cortarFrutaPedacos(laranjas)
    const suco = `Suco com ${pedacosMaca} pedaços de maçã e ${pedacosLaranja} pedaços de laranja.`
    
    return suco
}

// O resultado

console.log(fruitProcessor(2, 3));
// > Suco com 8 pedaços de maçã e 12 pedaços de laranja.
```