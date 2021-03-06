# EN: Document Object Model (DOM)

Very famous. Fundamental JavaScript Concept.

## Introduction

The DOM is a structured representation of HTML documents.

It **allows the JavaScript to access HTML elements and styles** to _manipulate_ them. This means you can change the text, HTML attributes, CSS styles **via JS**. The possibilities are endless: this is the power of JS and Internet.

The DOM is the **connection point** from HTML and CSS **to** JS.

The DOM is created automatically by the browser whenever an HTML document is loaded as a tree structure. This is a reference point to Data Structures.

The entry point to the DOM is a special object called _document_. The document uses a method, called `.querySelector()` to select the HTML element. This is usually the first "child-element" of the "parent-element" document.

Each parent-element can have as many child-element the web developer inserts in the HTML document. In the end, we have nested elements which represents a tree structure.

## Important PS notes

Few things to remember.

1. The DOM methods and properties for DOM manipulation **are not a part** of JS.
2. The DOM methods and properties for DOM manipulation **are a part of the Web APIs** (\*Application Programming Interface). The Web APIs are like automatic libraries available for use and it's all done behind the curtains, we don't need to import anything. These Web APIs can interact with JS. This is what **truly** happens. So, your browser is a Web API made for visual navigation of the web. Other Web APIs include timers and fetch.

## Guess-My-Number-Game Project

_PS: My [guess-my-number-game](https://github.com/barbaracalderon/guess-my-number-game) project used these concepts._

These are the notes from the above repository.

Check out the repository to see the whole code in all its integrity.

### addEventListener

Our code will react to something that happens in the application. But how will it know when something happens? By _listening to an event_ through the `addEventListener` method.

An `event` is something that happens in the page, like a mouse click, a mouse hover, a key press, and more.

With the Event Listener, the code will be waiting for the event to happen, watchful and "listening" to whatever action happens (metaphor intended). When the expected event happens, our code will react to it.

How to do this?

### Handling Click Events

How to make it work? Two simple steps.

1. Locate on which HTML you want to place your EventListener on
2. Choose a reaction (usually a function) to this event happening

### addEventListener - on which HTML element

First, we should be able to locate **where** to place an EventListener. On which HTML element should we place our EventListener?

Let's use a buttom tag as an example.

Imagine this buttom tag has a class called "check". For the EventListener, that class is how it located this specific HTML element: `(".check")`.

### Events - what kind? A click

Now, what should it listen to? A _click_.

That's the event in our case. But there's a whole list on types of events that could take place on DOM. Be sure to check it out: [the MDN Events categories](https://developer.mozilla.org/pt-BR/docs/Web/Events)

### Reaction - a function

And what should it do after hearing the click? What is its reaction?

This is called the Event Handler. How should it handle the click event?

It should handle through a function. Remember that in JS, **functions are values**. So, the Event Listener has two parameters: what it waits for (Event), what it does (Event Handler). The second parameter is usually a function.

```javascript
// EventListener(two, parameters)
// .addEventListener('event', function())

document.querySelector('.check').addEventListener('click', function () {
    console.log(document.querySelector('.guess').value)
}

// PS: Value is an attribute. We can access it through ".value"
```

Our function is simple: it prints the value to the console.

Let's convert the input (string) to a number.

```javascript
// Remember, whenever we get the user input,
// it comes to us as a string. So if we're dealing with numbers,
// we must convert it to number with the Number() method.

document.querySelector(".check").addEventListener("click", function () {
  console.log(document.querySelector(".guess").value); // > '5'
});

// String -> Number:
document.querySelector(".check").addEventListener("click", function () {
  const guess = Number(document.querySelector(".guess").value);
  console.log(guess, typeof guess); // > 5 "number"
});

// PS: The TEXT CONTENT on our HTML elements are aso attributes.
// We can access it through ".textContent"
// (just like we did with ".value")
```

### DOM not always reliable

Sometimes you will not be able to rely on the DOM, so it's safe to place some variables inside your code instead of catching it through the DOM.

### State Variables

Some variables can be called state variables because they are a part of the DOM state, which basically is **all the data that is relevant to the application**.

## Manipulating CSS Styles

We can change CSS through the DOM.

For example, we can change the entire page background color.

In order to do this, you gotta select the body of the HTML document to change the background. Then, the style - it's actually a property in DOM. Then, you can access the CSS attributes themselves.

Like this.

```javascript
document.querySelector("body").style.backgroundColor = "#60b347";

// ".style" is a DOM property
```

You can also select other HTML elements to change the CSS property.

```javascript
document.querySelector(".number").style.width = "30rem";

// Here, we selected the ".number" HTML element and accessed
// the style DOM property to "grab" the CSS "width" property.
```

_IMPORTANT: Remember to use the DOM style property to specify the CSS properties to change. The CSS property is called using camelCase and it's always a string._

## Modal Project

### Introduction

_PS: These notes are a reference to the Modal Project inside this repository. Check out the [modal-project-example](https://github.com/barbaracalderon/notes-on-javascript/tree/main/project-modal-example) folder here._

Go to the repository mentioned above and click on the index.html file. It will show you a page with three buttons. If you click on either button, it displays a large box in the center of the screen with a message. The large box blurs everything not in the box. It also has an X, and if you click on it, it closes. Also, you can close it by hitting the 'ESC' key.

How do we make all these interactions? With JavaScript.

In this section, we describe how. These are the notes about the Modal Project Example, with key points to JavaScript that are **worth reminding yourself once in a while**.

### Check the Index.html file

First, we gotta select every HTML element that we're doing to interact with. Then, we store them inside variables to make things easier.

Check the HTML document and see which classes are the ones through which we will select our HTML elements. If you take a closer look, you will notice that the hidden class is the main class we'll deal with: the hidden class is a reference to the big box we're going to deal with.

The classes are: `modal, overlay, hidden, show modal`.

_The overlay class is the blurred part of the page._

Let's grab them and store them inside variables.

Like this.

```javascript
const modal = document.querySelector(".modal");
const overlay = document.querySelector(".overlay");
const btnCloseModal = document.querySelector(".close-modal");
```

And now we got three buttons from the same class "show-modal". If we try to do the same thing as before with the show-modal class...

```javascript
// It will only grab the first box:
const btnsOpenModal = document.querySelector(".show-modal");
```

... it won't work because it only selects the first one. Not the three modal boxes.

So how do we grab all three modal boxes?

We use the `querySelectorAll` instead of `querySelector`.

All our buttons are now inside a list, so we can iterate the list to manipulate each item.

```javascript
const btnsOpenModal = document.querySelectorAll('.show-modal');

for (let i = 0; i < btnsModalOpen.length; i++) {
    console.log(btnsOpenModal[i].textContent;)
}
// > modal button 1
// > modal button 2
// > modal button 3
```

### Manipulate Classes with JS

Remember what we have to do: we gotta click each of these buttons in order to make the large box show up on the screen.

How do we do it?

First, let's manipulate the previous Open Modal Buttons.

The box that should pop up already exists but it is **hidden** in CSS, because its display property value is set to none. It's already there but we cannot see it.

To make the window pop up, we're going to click on either Open Modal Button and the reaction must be to remove the "hidden" class from the classList property of the DOM.

_PS: It seems the DOM creates a list of all classes available to manipulate. When we remove the "hidden" class, it means it becomes visible because that "hidden" class (and also CSS state) is no longer reachable._

Now the window appears.

How do we do to close it?

We **add** the "hidden" class back to the DOM classList.

That's what we're going to do.

See below.

```javascript
const modal = document.querySelector(".modal");
const overlay = document.querySelector(".overlay");
const btnCloseModal = document.querySelector(".close-modal");
const btnsOpenModal = document.querySelectorAll(".show-modal");

for (let i = 0; i < btnsOpenModal.length; i++)
  btnsOpenModal[i].addEventListener("click", function () {
    modal.classList.remove("hidden");
    overlay.classList.remove("hidden");
  });

btnCloseModal.addEventListener("click", function () {
  modal.classList.add("hidden");
  overlay.classList.add("hidden");
});

overlay.addEventListener("click", function () {
  modal.classList.add("hidden");
  overlay.classList.add("hidden");
});
```

Too many repetitive codes.

We gotta do better.

```javascript
const modal = document.querySelector(".modal");
const overlay = document.querySelector(".overlay");
const btnCloseModal = document.querySelector(".close-modal");
const btnsOpenModal = document.querySelectorAll(".show-modal");

const openModal = function () {
  modal.classList.remove("hidden");
  overlay.classList.remove("hidden");
};
const closeModal = function () {
  modal.classList.add("hidden");
  overlay.classList.add("hidden");
};

for (let i = 0; i < btnsOpenModal.length; i++)
  btnsOpenModal[i].addEventListener("click", openModal);
btnCloseModal.addEventListener("click", closeModal);
overlay.addEventListener("click", closeModal);
```

The lesson to learn is... **whenever your code repeats itself, you gotta use the DRY principle**. Especially if the same reaction is used in different occasions - like, to open the modal buttom or to close it. So, **store that function inside a variable (remember functions are values in JS) and use the variable**.

### Global Event - press 'ESC' key

Key press events are called global events because it does not happen on an specific HTML element.

So, how to respond to keyboard events? We still need to use Event Listener.

That are 3 events for keyboards.

They are described below.

| Event        | What it does                                                                  |
| :----------- | :---------------------------------------------------------------------------- |
| **keydown**  | it fires the reaction as soon as we press the key                             |
| **keypress** | it fires the reaction continuously as long as your finger is pressing the key |
| **keyup**    | only happens when you lift off your finger from the key                       |

We handle them the following way.

```javascript
// Console will print the message when ANY key is pressed
document.addEventListener("keydown", function () {
  console.log("A key was pressed.");
});
```

But we don't want this. We want to fire a reaction only when we press the ESC key. The reaction is to close it.

```javascript
document.addEventListener("keydown", function (e) {
  console.log(e);
  if (e.key === "Escape") {
    if (!modal.classList.contains("hidden")) {
      closeModal();
    }
  }
});
```

Remember 'ESC' is for "Escape".

Which can be better written as below (whole code).

```javascript
// Selecting the elements
const modal = document.querySelector(".modal");
const overlay = document.querySelector(".overlay");
const btnCloseModal = document.querySelector(".close-modal");
const btnsOpenModal = document.querySelectorAll(".show-modal");

// Open the modal box
const openModal = function () {
  modal.classList.remove("hidden");
  overlay.classList.remove("hidden");
};

// Close the modal box
const closeModal = function () {
  modal.classList.add("hidden");
  overlay.classList.add("hidden");
};

// Select all the Modal buttons
for (let i = 0; i < btnsOpenModal.length; i++)
  btnsOpenModal[i].addEventListener("click", openModal);
btnCloseModal.addEventListener("click", closeModal);
overlay.addEventListener("click", closeModal);

document.addEventListener("keydown", function (e) {
  console.log(e);
  if (e.key === "Escape" && !modal.classList.contains("hidden")) {
    closeModal(); // Check out this function being used all the time!
  }
});
```

### The querySelector and querySelectorAll

It's how you grab an HTML element.

| Type    | Code                               |
| :------ | :--------------------------------- |
| Classes | `document.querySelector('.class')` |
| Id      | `document.querySelector('#id')`    |

Remember to select more of the same element through `document.querySelectorAll('#id')`

### The Toggle Method

This might come in handy!

`element.classList.toggle("example")`

Toggle between adding and removing a class name from an element with JS.

1. If the class is in the class list, it will remove it.
2. If the class name is not in the class list, it will add it.

Additionally, you can manually add or remove a class from the classList with the methods: `element.classList.add(".example")` or `element.classList.remove(".example")`

### Init Function

It might be a good idea to create your own init function.

This could work well if your project has starting conditions that can be reset according to a user choice.

### Organization

You are starting out now. It's good practice to organize your code so you will not get lost in it. Nobody likes spaghetti code.

Here are some ideas. Start out with:

1. Selecting elements
2. Selecting buttons
3. Starting conditions
4. Functions created for use
5. Rest of the logic
6. Comments for future reference
7. Others

---

# PT: Document Object Model (DOM)

Muito famoso. Conceito em JavaScript fundamental.

A tradu????o mais perto do sentido que encontrei foi "Modelo de Objeto Documento".

## Introdu????o

O DOM ?? uma representa????o estruturada de documentos HTML.

Ele **permite que o JavaScript tenha acesso aos elementos HTML e seus estilos** para _manipul??-los_. Isso significa que voc?? consegue mudar o texto, atributos do HTML, estilos do CSS **via JS**. As possibilidades s??o infinitas: esse ?? o poder do JS e a web.

O DOM ?? o **ponto de conex??o** do HTML e do CSS **para** o JS.

O DOM ?? criado automaticamente pelo navegador toda vez que um documento HTML ?? carregado. E ?? criado em forma de estrutura de ??rvore. Esse ?? um ponto de refer??ncia com a ??rea de Estrutura de Dados.

O ponto de entrada no DOM ?? por meio de um objeto especial chamado _document_. O document usa um m??todo, chamado `.querySelector()` para selecionar elementos HTML. Normalmente, esse ?? o primeiro "elemento-filho" do "elemento-pai" document.

_PS: Em uma estrutura de ??rvore, temos a raiz, que inicia no topo. Uma raiz pode ter elementos-filhos que, por sua vez, podem ter elementos-filhos. A rela????o elemento-filho e elemento-pai trata-se sobre a hierarquia: o elemento-pai est?? numa hierarquia maior, mais pr??ximo da raiz no topo, e o elemento-filho est?? ligado ao elemento-pai em uma posi????o mais abaixo na hierarquia._

Cada elemento-pai pode ter quantos elementos-filho o desenvolvedor colocar no documento HTML. No final das contas, podem ter v??rios elementos aninhados que representam uma estrutura de ??rvore.

## Notas Importantes PS

Coisinhas pra lembrar.

1. Os m??todos e propriedades do DOM para sua manipula????o **n??o s??o parte** do JS.
2. Os m??todos e propriedades do dom para sua manipula????o **s??o uma parte das Web APIs** (_Application Programming Interface_, ou Aplica????o de Interface de Programa????o). As Web APIs s??o como bibliotecas autom??ticas dispon??veis para uso e s??o usadas, neste caso, por baixo dos panos - n??o tem necessidade de importar nada. Essas Web APIs podem interagir com JS. ?? isso que de verdade acontece. Ent??o, o seu navegador ?? um Web API feito para navega????o visual de conte??dos da web. Outras Web APIs incluem timers e fetch.

## Guess-My-Number-Game Project

_PS: Meu projeto [guess-my-number-game](https://github.com/barbaracalderon/guess-my-number-game) usou os conceitos descritos aqui._

Essas anota????es s??o referentes ao reposit??rio acima.

Veja esse reposit??rio para estudar todo o c??digo de modo integral.

### addEventListener

Nosso c??digo vai reagir a alguma coisa que acontece na aplica????o. Mas como vai saber quando algo acontece? _Escutando (listening) um evento_ por meio do m??todo DOM ``addEventListener`

Um `evento` ?? algo que acontece na p??gina, como um clique do mouse, um passeio do ponteiro sobre algo (hover), apertar uma tecla, e mais.

Com o Event Listener ("Escutador de Eventos"), o c??digo vai esperar o evento acontecer, bem atento e "escutando" qualquer a????o que aconte??a (?? uma met??fora esse "escutando"). Quando o evento esperado acontece, nosso c??digo vai reagir a ele.

Como fazer isso?

### Lidando com os Eventos de Clique

Como fazer funcionar? Dois passos simples.

1. Localize em qual elemento HTML voc?? deseja colocar o seu EventListener
2. Escolha uma rea????o (normalmente uma fun????o que a gente cria) para este evento acontecendo

### addEventListener - em qual elemento HTML

Primeiro, devemos conseguir localizar **onde** colocar o nosso EventListener. Em qual elemento HTML devemos atrelar o EventListener?

Vamos usar uma tag de button como exemplo.

Imagine que essa button tag tem uma classe chamada "check". Para o EventListener, essa classe ?? como ele localiza esse elemento HTML espec??fico: `(".check")`

### Eventos - de que tipo? Um clique

Agora, o que ele deveria escutar? Um _clique_.

Esse ?? o nosso evento, do nosso exemplo aqui. Mas tem toda uma lista de tipos de eventos que podem acontecer no DOM. D?? uma olhada em [the MDN Events categories](https://developer.mozilla.org/pt-BR/docs/Web/Events)

### Rea????o (Event Handler) - uma fun????o

E o que deveria fazer depois que escutar o clique? Qual vai ser a rea????o?

Isso ?? o que chamamos de Event Handler ("Lidador/Cuidador de Eventos"). Como ele deve cuidar do evento clique?

Ele deve cuidar por meio de uma fun????o. Lembre-se que em JS, **fun????es s??o valores**. Ent??o, o Event Listener tem dois valores como par??metros: o que ele espera (Event), o que ele faz (Event Handler). O segundo par??metro ?? uma fun????o.

```javascript
// EventListener(dois, par??metros)
// .addEventListener('event', function())

document.querySelector('.check').addEventListener('click', function () {
    console.log(document.querySelector('.guess').value)
}

// PS: Value ?? um atributo do DOM. N??s podemos acess??-lo por meio do ".value"
```

Nossa fun????o ?? simples: ele printa o valor no console.

Vamos converter o input do usu??rio (que ?? uma string) para um number.

```javascript
// Lembra que toda vez que um usu??rio deixa um input,
// esse input vem pra gente como uma string. Ent??o, se a gente
// t?? lidando com n??meros, devemos converter essa string
// para n??mero por meio do m??todo Number().

document.querySelector(".check").addEventListener("click", function () {
  console.log(document.querySelector(".guess").value); // > '5'
});

// String -> Number:
document.querySelector(".check").addEventListener("click", function () {
  const guess = Number(document.querySelector(".guess").value);
  console.log(guess, typeof guess); // > 5 "number"
});

// PS: O CONTE??DO DE TEXTO dos nossos elementos HTML tamb??m s??o atributos.
// D?? pra acess??-los por meio do ".textContent" (assim como fizemos com ".value")
```

### Nem sempre d?? pra depender do DOM

Algumas vezes voc?? n??o vai conseguir pegar as informa????es no DOM, ent??o ?? tranquilo colocar algumas vari??veis dentro do seu c??digo em vez de "peg??-las" do DOM.

### Vari??veis de Estado

Algumas vari??veis podem ser chamadas de "state variables" (vari??veis de estado) porque elas s??o uma parte do estado do DOM, que basicamente **s??o todos os dados que s??o relevantes para a aplica????o**.

## Manipulando CSS Styles

D?? pra mudar o CSS pelo DOM.

Por exemplo, d?? pra mudar toda a cor do background da p??gina.

Pra fazer isso, voc?? deve selecionar o elemento HTML 'body' do document. A?? depois, voc?? acessa a propriedade style, que na realidade ?? um atributo do DOM neste caso. Da?? depois voc?? consegue acessar os atributos CSS.

Tipo assim.

```javascript
document.querySelector("body").style.backgroundColor = "#60b347";

// ".style" ?? um atributo do DOM
```

Voc?? tamb??m pode selecionar outros elementos HTML para mudar as propriedades do CSS.

```javascript
document.querySelector(".number").style.width = "30rem";

// Aqui, a gente selecionou o elemento HTML ".number" e
// acessou o atributo "style" do DOM para "pegar" a propriedade
// "width" do CSS.
```

_IMPORTANTE: Lembre-se de usar a propriedade style do DOM para especificar as propriedades CSS que deseja mudar. A propriedade CSS ?? chamada usando a nota????o em camelCase e sempre ?? uma string._

## Projeto Modal

### Introdu????o

_PS: As anota????es dessa se????o s??o referentes ao Modal Project que est?? nesse reposit??rio. Veja na pasta [modal-project-example](https://github.com/barbaracalderon/notes-on-javascript/tree/main/project-modal-example) aqui._

V?? para o reposit??rio mencionado acima e clique no arquivo index.html. Ele vai te mostrar uma p??gina com tr??s bot??es. Se voc?? clicar em qualquer um destes bot??es, uma caixa grande com conte??do vai aparecer no meio da p??gina. Essa caixa grande deixa tudo "emba??ado" que esteja fora dela. Nessa caixa, tamb??m existe um X que, caso voc?? clique em cima, faz a caixa fechar. Al??m disso, voc?? pode fechar a caixa apertando a tecla 'ESC'.

Como a gente faz essas intera????es? Com JavaScript.

Nesta se????o, a gente descreve como. Essas s??o as minhas anota????es sobre o Modal Project Example, com pontos bem importantes sobre JavaScript que considero que **vale a pena se lembrar de vez em quando, voltar aqui**.

### Abra o arquivo index.html

Primeiro, temos que selecionar cada elemento HTML com o qual vamos interagir. Depois, guardar esses valores em vari??veis para tornar tudo mais simples.

Observe o HTML document e veja quais classes s??o aquelas que vamos selecionar como elementos HTML para interagir. Se voc?? olhar bem, vai notar que a classe "hidden" ?? a classe principal com a qual vamos lidar: ?? essa caixa grande que vamos lidar no navegador.

As classes s??o: `modal, overlay, hidden, show modal`.

_O overlay ?? a parte "blur" ou sem foco da p??gina._

Vamos selecionar essas classes e guard??-las em vari??veis.

Assim.

```javascript
const modal = document.querySelector(".modal");
const overlay = document.querySelector(".overlay");
const btnCloseModal = document.querySelector(".close-modal");
```

E agora n??s temos tr??s bot??es com a mesma classe "show-modal". Se a gente tentar fazer a mesma coisa com a classe "show-modal", a mesma coisa que a caixa de c??digo anterior mostra...

```javascript
// S?? vai selecionar a primeira caixa
const btnsOpenModal = document.querySelector(".show-modal");
```

...n??o vai funcionar porque vai apenas selecionar a primeira caixa, e n??o as tr??s caixas modal.

Ent??o como selecionar todas as tr??s caixas?

Vamos usaar `querySelectorAll` em vez de apenas `querySelector`. Assim, todos os bot??es agora est??o dentro de uma lista e podemos iterar esta lista para manipular cada item dentro dela (no caso, tr??s itens).

```javascript
const btnsOpenModal = document.querySelectorAll('.show-modal');

for (let i = 0; i < btnsModalOpen.length; i++) {
    console.log(btnsOpenModal[i].textContent;)
}
// > modal button 1
// > modal button 2
// > modal button 3
```

### Manipular Classes com JS

Lembre-se do que temos que fazer: temos que clicar em qualquer um desses bot??es para fazer com que a caixa grande apare??a na tela. Para fechar essa pequena janela (chamaremos de caixa), n??s podemos clicar no X, clicar em algum local fora dessa caixa ou ainda apertar o ESC do teclado.

Perceba que s??o tr??s formas diferentes de fechar a caixa.

Como fazer isso?

Primeiro, vamos manipular os bot??es "Open Modal" mostrados anteriormente.

A caixa que deve abrir j?? existe... mas est?? **escondida** (_hidden_) pelo CSS. Isso porque no CSS, o display est?? como none (propriedade/valor). Ou seja, a caixa j?? est?? l??... n??s ?? que n??o vemos.

Para fazer a caixa aparecer, n??s vamos clicar em qualquer um dos bot??es Open Modal e a rea????o vai ser remover a classe "hidden" da propriedade classList (propriedade do DOM).

_PS: Parece que o DOM cria uma lista de todas as classes dispon??veis para manipular. Quando a gente remove a classe "hidden", significa que ela se torna vis??vel porque a classe "hidden" (e o estado CSS) n??o est?? mais alcan????vel._

Agora a caixa aparece.

Mas como vamos fech??-la?

A gente adiciona (_add_) a classe "hidden" de volta para a classList do DOM.

?? o que vamos fazer. Olhe abaixo.

```javascript
const modal = document.querySelector(".modal");
const overlay = document.querySelector(".overlay");
const btnCloseModal = document.querySelector(".close-modal");
const btnsOpenModal = document.querySelectorAll(".show-modal");

for (let i = 0; i < btnsOpenModal.length; i++)
  btnsOpenModal[i].addEventListener("click", function () {
    modal.classList.remove("hidden");
    overlay.classList.remove("hidden");
  });

btnCloseModal.addEventListener("click", function () {
  modal.classList.add("hidden");
  overlay.classList.add("hidden");
});

overlay.addEventListener("click", function () {
  modal.classList.add("hidden");
  overlay.classList.add("hidden");
});
```

Perceba que tem muito c??digo repetido.

Podemos fazer melhor.

```javascript
const modal = document.querySelector(".modal");
const overlay = document.querySelector(".overlay");
const btnCloseModal = document.querySelector(".close-modal");
const btnsOpenModal = document.querySelectorAll(".show-modal");

const openModal = function () {
  modal.classList.remove("hidden");
  overlay.classList.remove("hidden");
};
const closeModal = function () {
  modal.classList.add("hidden");
  overlay.classList.add("hidden");
};

for (let i = 0; i < btnsOpenModal.length; i++)
  btnsOpenModal[i].addEventListener("click", openModal);
btnCloseModal.addEventListener("click", closeModal);
overlay.addEventListener("click", closeModal);
```

A li????o pra aprender aqui ??... **quando o seu c??digo se repetir demais, voc?? deve aplicar o princ??pio DRY**. Especialmente, se a mesma rea????o ?? usada em diferentes momentos - como abrir o modal (a caixa) ou fech??-lo. **Guarde essa fun????o em uma vari??vel (fun????es s??o valores em JS) e use essa vari??vel para chamar essa fun????o quando precisar.**

### Evento Global - pressionar a tecla 'ESC'

Apertar uma tecla ?? um evento global porque n??o acontece em algum elemento espec??fico. Ent??o, como reagir a eventos de teclado?

Ainda precisamos usar o Event Listener.

Existem tr??s eventos para teclados. Eles est??o descritos abaixo.

| Evento       | O que faz                                                                         |
| :----------- | :-------------------------------------------------------------------------------- |
| **keydown**  | ele aciona a rea????o assim que a gente aperta a tecla                              |
| **keypress** | ele aciona a rea????o continuamente enquanto o nosso dedo estiver apertando a tecla |
| **keyup**    | s?? aciona a rea????o quando voc?? **levanta** o dedo da tecla                        |

N??s lidamos com esses eventos da seguinte forma.

```javascript
// O console vai printar a mensagem quando QUALQUER tecla ?? apertada
document.addEventListener("keydown", function () {
  console.log("A key was pressed.");
});
```

Mas a gente n??o quer isso. A gente quer acionar uma rea????o, que ?? fechar o Modal (a caixa), s?? quando a gente pressionar a tecla 'ESC'.

```javascript
document.addEventListener("keydown", function (e) {
  console.log(e);
  if (e.key === "Escape") {
    if (!modal.classList.contains("hidden")) {
      closeModal();
    }
  }
});
```

'ESC' ?? a mesma coisa que "Escape".

Podemos escrever melhor abaixo (c??digo todo).

```javascript
// Selecionando os elementos
const modal = document.querySelector(".modal");
const overlay = document.querySelector(".overlay");
const btnCloseModal = document.querySelector(".close-modal");
const btnsOpenModal = document.querySelectorAll(".show-modal");

// Abrir a caixa (Modal)
const openModal = function () {
  modal.classList.remove("hidden");
  overlay.classList.remove("hidden");
};

// Fechar a caixa (Modal)
const closeModal = function () {
  modal.classList.add("hidden");
  overlay.classList.add("hidden");
};

// Selecionar os tr??s bot??es do Modal
for (let i = 0; i < btnsOpenModal.length; i++)
  btnsOpenModal[i].addEventListener("click", openModal);
btnCloseModal.addEventListener("click", closeModal);
overlay.addEventListener("click", closeModal);

document.addEventListener("keydown", function (e) {
  console.log(e);
  if (e.key === "Escape" && !modal.classList.contains("hidden")) {
    closeModal(); // Olha essa fun????o sendo usada mais vezes no c??digo
  }
});
```

### O querySelector e o querySelectorAll

?? como voc?? seleciona um elemento HTML.

| Tipo    | C??digo                             |
| :------ | :--------------------------------- |
| Classes | `document.querySelector('.class')` |
| Id      | `document.querySelector('#id')`    |

Lembrando que pra selecionar mais de um mesmo elemento ?? por meio do `querySelectorAll`

### M??todo Toggle

`element.classList.toggle("example")`

Esse pode ser ??til!

Mude entre adicionar e remover um nome de class de um elemento com o JS.

1. Se a classe tiver na classList, ele remove de l??.
2. Se a classe n??o tiver na classList, ele inclui l??.

Al??m disso, voc?? pode manualmente adicionar ou remover o nome de uma classe da classList por meio dos m??todos de adicionar ("add") e remover ("remove): `element.classList.add(".example")` ou `element.classList.remove(".example")`

### Fun????o Init

Pode ser uma boa ideia criar sua pr??pria fun????o init.

Init vem de "initialization" que significa "inicializa????o".

Isso pode funcionar bem em um projeto que tem condi????es de in??cio que podem ser "resetados" pelo usu??rio dependendo de sua escolha.

### Organiza????o

Voc?? t?? come??ando agora. ?? uma boa pr??tica organizar o seu c??digo para n??o se perder nele mesmo. Ningu??m gosta de c??digo "spaghetti".

Algumas ideias aqui. Comece com:

1. Selecionar os elementos
2. Selecionar os bot??es
3. Condi????es de in??cio
4. Fun????es criadas para uso
5. O restante da l??gica
6. Coment??rios para refer??ncia futura
7. Outros
