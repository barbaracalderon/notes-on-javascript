# EN: Document Object Model (DOM)

Very famous. Fundamental JavaScript Concept.

## Introduction 

The DOM is a structured representation of HTML documents. 

It **allows the JavaScript to access HTML elements and styles** to *manipulate* them. This means you can change the text, HTML attributes, CSS styles **via JS**. The possibilities are endless: this is the power of JS and Internet.

The DOM is the **connection point** from HTML and CSS **to** JS. 

The DOM is created automatically by the browser whenever an HTML document is loaded as a tree structure. This is a reference point to Data Structures.

The entry point to the DOM is a special object called *document*. The document uses a method, called ```.querySelector()``` to select the HTML element. This is usually the first "child-element" of the "parent-element" document.

Each parent-element can have as many child-element the web developer inserts in the HTML document. In the end, we have nested elements which represents a tree structure.

## Important PS notes

Few things to remember.

1. The DOM methods and properties for DOM manipulation **are not a part** of JS.
2. The DOM methods and properties for DOM manipulation **are a part of the Web APIs** (*Application Programming Interface). The Web APIs are like automatic libraries available for use and it's all done behind the curtains, we don't need to import anything. These Web APIs can interact with JS. This is what **truly** happens. So, your browser is a Web API made for visual navigation of the web. Other Web APIs include timers and fetch.

## Guess-My-Number-Game Project

*PS: My [guess-my-number-game](https://github.com/barbaracalderon/guess-my-number-game) project used these concepts.*

These are the notes from the above repository. 

Check out the repository to see the whole code in all its integrity.

### addEventListener

Our code will react to something that happens in the application. But how will it know when something happens? By *listening to an event* through the ```addEventListener``` method. 

An ```event``` is something that happens in the page, like a mouse click, a mouse hover, a key press, and more. 

With the Event Listener, the code will be waiting for the event to happen, watchful and "listening" to whatever action happens (metaphor intended). When the expected event happens, our code will react to it. 

How to do this?

### Handling Click Events

How to make it work? Two simple steps.

1. Locate on which HTML you want to place your EventListener on
2. Choose a reaction (usually a function) to this event happening

### addEventListener - on which HTML element
First, we should be able to locate **where** to place an EventListener. On which HTML element should we place our EventListener?

Let's use a buttom tag as an example.

Imagine this buttom tag has a class called "check". For the EventListener, that class is how it located this specific HTML element: ```(".check")```. 

### Events - what kind? A click
Now, what should it listen to? A *click*. 

That's the event in our case. But there's a whole list on types of events that could take place on DOM. Be sure to check it out: [the MDN Events categories](https://developer.mozilla.org/pt-BR/docs/Web/Events)

### Reaction - a function

And what should it do after hearing the click? What is its reaction? 

This is called the Event Handler.  How should it handle the click event?

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

document.querySelector('.check').addEventListener('click', function() {
    console.log(document.querySelector('.guess').value) // > '5'
})

// String -> Number:
document.querySelector('.check').addEventListener('click', function () {
    const guess = Number(document.querySelector('.guess').value);
    console.log(guess, typeof guess);       // > 5 "number"
})

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
document.querySelector('body').style.backgroundColor = '#60b347';

// ".style" is a DOM property
```

You can also select other HTML elements to change the CSS property.

```javascript
document.querySelector('.number').style.width = '30rem';

// Here, we selected the ".number" HTML element and accessed
// the style DOM property to "grab" the CSS "width" property.
```
*IMPORTANT: Remember to use the DOM style property to specify the CSS properties to change. The CSS property is called using camelCase and it's always a string.*

## Modal Project

*PS: These notes are a reference to the Modal Project inside this repository. Check out the [modal-project-example](https://github.com/barbaracalderon/notes-on-javascript/tree/main/project-modal-example) folder here.*

First, we gotta select every HTML element that we're doing to interact with. Then, we store them inside variables to make things easier. 

Check the HTML document and see which classes are the ones through which we will select our HTML element.

The hidden class will be the main class we'll deal with: it's that big box we're dealing with.

The classes are: ```modal, overlay, hidden, show modal```.

*The overlay class is the blurred part of the page.*

Let's grab them and store them inside variables.

Like this.

```javascript
const modal = document.querySelector('.modal');
const overlay = document.querySelector('.overlay');
const btnCloseModal = document.querySelector('.close-modal');
```

And now we got three buttons from the same class "show-modal". If we try to do the same thing as before.

```javascript
// It will only grab the first box:
const btnsOpenModal = document.querySelector('.show-modal');
```
It won't work because it will only select the first one. Not the three modal boxes. 

So how do we grab all three modal boxes? 

We use the querySelectorAll instead of querySelector.

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

Here is what we're gonna do: there are three buttons in the page. We gotta click each of these buttons and it will pop up a window. We can click the X to exit the window, click outside the window box or press ESC.

This is what we're going to do. How do we do it?

First, let's manipulate the previous Open Modal Buttons.

The box that should pop up already exists but it is **hidden** in CSS, using the display none property/value. It's already there but we cannot see it. 

To make the window pop up, we're going to click on either Open Modal Button and the reaction will be to remove the "hidden" class from the classList property of the DOM.

*PS: It seems the DOM creates a list of all classes available to manipulate. When we remove the "hidden" class, it means it becomes visible because that "hidden" class (and also CSS state) is no longer reachable.*

Now the window appears.

How do we do to close it? We **add** the "hidden" class back to the DOM classList.

That's what we're going to do.

See below.

```javascript
const modal = document.querySelector('.modal');
const overlay = document.querySelector('.overlay');
const btnCloseModal = document.querySelector('.close-modal');
const btnsOpenModal = document.querySelectorAll('.show-modal');

for (let i = 0; i < btnsOpenModal.length; i++)
    btnsOpenModal[i].addEventListener('click', function () {
        modal.classList.remove('hidden');
        overlay.classList.remove('hidden');
    });

btnCloseModal.addEventListener('click', function () {
    modal.classList.add('hidden');
    overlay.classList.add('hidden');
});

overlay.addEventListener('click', function () {
    modal.classList.add('hidden');
    overlay.classList.add('hidden');
});
```

Too many repetitive codes.

We gotta do better.

```javascript
const modal = document.querySelector('.modal');
const overlay = document.querySelector('.overlay');
const btnCloseModal = document.querySelector('.close-modal');
const btnsOpenModal = document.querySelectorAll('.show-modal');

const openModal = function () {
    modal.classList.remove('hidden');
    overlay.classList.remove('hidden');
}
const closeModal = function () {
    modal.classList.add('hidden');
    overlay.classList.add('hidden');
}

for (let i = 0; i < btnsOpenModal.length; i++)
    btnsOpenModal[i].addEventListener('click', openModal);
btnCloseModal.addEventListener('click', closeModal);
overlay.addEventListener('click', closeModal);
```

The lesson to learn is... **whenever your code repeats itself, you the DRY principle**. Especially if the same reaction is used in different occasions - like the open modal or to close it. **Store that function inside a variable and use the variable**.

### Global Event - press 'ESC' key

Key press events are called global events because it does not happen in an specific HTML element.

So, how to respond to keyboard events? We still need to use Event Listener.

That are 3 events for keyboards. 

They are described below.

Event | What it does
------ | ---------
**keydown** | it fires the reaction as soon as we press the key
**keypress** | it fires the reaction continuously as long as your finger is pressing the key
**keyup** | only happens when you lift off your finger from the key

We handle them the following way.

```javascript
// Console will print the message when ANY key is pressed
document.addEventListener('keydown', function () {
    console.log('A key was pressed.')
})
```
But we don't want this. We want to fire a reaction, which is to close Modal, only when we press the ESC key.

```javascript
document.addEventListener('keydown', function (e) {
    console.log(e);
    if (e.key === 'Escape') {
        if (!modal.classList.contains('hidden')) {
            closeModal();
        }
    }
});
```
Remember 'ESC' is for "Escape".

Which can be better written as below (whole code).

```javascript
// Selecting the elements
const modal = document.querySelector('.modal');
const overlay = document.querySelector('.overlay');
const btnCloseModal = document.querySelector('.close-modal');
const btnsOpenModal = document.querySelectorAll('.show-modal');

// Open the modal box
const openModal = function () {
    modal.classList.remove('hidden');
    overlay.classList.remove('hidden');
}

// Close the modal box
const closeModal = function () {
    modal.classList.add('hidden');
    overlay.classList.add('hidden');
}

// Select all the Modal buttons
for (let i = 0; i < btnsOpenModal.length; i++)
    btnsOpenModal[i].addEventListener('click', openModal);
btnCloseModal.addEventListener('click', closeModal);
overlay.addEventListener('click', closeModal);

document.addEventListener('keydown', function (e) {
    console.log(e);
    if (e.key === 'Escape' && !modal.classList.contains('hidden')) {
        closeModal();  // Check out this function being used all the time!
    }
});

```

### The querySelector and querySelectorAll

It's how you grab an HTML element. 

Type | Code
---- | -------
Classes | ```document.querySelector('.class')```
Id | ```document.querySelector('#id')```

Remember to select more of the same element through ```document.querySelectorAll('#id')```


### The Toggle Method

```element.classList.toggle("example")```

This might come in handy!

Toggle between adding and removing a class name from an element with JS.

1. If the class is in the class list, it will remove it.
2. If the class name is not in the class list, it will add it.

Additionally, you can manually add or remove a class from the classList with the methods: ```element.classList.add(".example")``` or ```element.classList.remove(".example")```

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

A tradução mais perto do sentido que encontrei foi "Modelo de Objeto Documento".

## Introdução

O DOM é uma representação estruturada de documentos HTML.

Ele **permite que o JavaScript tenha acesso aos elementos HTML e seus estilos** para *manipulá-los*. Isso significa que você consegue mudar o texto, atributos do HTML, estilos do CSS **via JS**. As possibilidades são infinitas:  esse é o poder do JS e a web. 

O DOM é o **ponto de conexão** do HTML e do CSS **para** o JS.

O DOM é criado automaticamente pelo navegador toda vez que um documento HTML é carregado. E é criado em forma de estrutura de árvore. Esse é um ponto de referência com a área de Estrutura de Dados.

O ponto de entrada no DOM é por meio de um objeto especial chamado *document*. O document usa um método, chamado ```.querySelector()``` para selecionar elementos HTML. Normalmente, esse é o primeiro "elemento-filho" do "elemento-pai" document. 

*PS: Em uma estrutura de árvore, temos a raiz, que inicia no topo. Uma raiz pode ter elementos-filhos que, por sua vez, podem ter elementos-filhos. A relação elemento-filho e elemento-pai trata-se sobre a hierarquia: o elemento-pai está numa hierarquia maior, mais próximo da raiz no topo, e o elemento-filho está ligado ao elemento-pai em uma posição mais abaixo na hierarquia.*

Cada elemento-pai pode ter quantos elementos-filho o desenvolvedor colocar no documento HTML. No final das contas, podem ter vários elementos aninhados que representam uma estrutura de árvore. 

## Notas Importantes PS

Coisinhas pra lembrar.

1. Os métodos e propriedades do DOM para sua manipulação **não são parte** do JS.
2. Os métodos e propriedades do dom para sua manipulação **são uma parte das Web APIs** (*Application Programming Interface*, ou Aplicação de Interface de Programação). As Web APIs são como bibliotecas automáticas disponíveis para uso e são usadas, neste caso, por baixo dos panos - não tem necessidade de importar nada. Essas Web APIs podem interagir com JS. É isso que de verdade acontece. Então, o seu navegador é um Web API feito para navegação visual de conteúdos da web. Outras Web APIs incluem timers e fetch.

## Guess-My-Number-Game Project

*PS: Meu projeto [guess-my-number-game](https://github.com/barbaracalderon/guess-my-number-game) usou os conceitos descritos aqui.*

Essas anotações são referentes ao repositório acima. 

Veja esse repositório para estudar todo o código de modo integral.

### addEventListener

Nosso código vai reagir a alguma coisa que acontece na aplicação. Mas como vai saber quando algo acontece? *Escutando (listening) um evento* por meio do método DOM ```addEventListener``

Um ```evento``` é algo que acontece na página, como um clique do mouse, um passeio do ponteiro sobre algo (hover), apertar uma tecla, e mais. 

Com o Event Listener ("Escutador de Eventos"), o código vai esperar o evento acontecer, bem atento e "escutando" qualquer ação que aconteça (é uma metáfora esse "escutando"). Quando o evento esperado acontece, nosso código vai reagir a ele. 

Como fazer isso?

### Lidando com os Eventos de Clique

Como fazer funcionar? Dois passos simples.

1. Localize em qual elemento HTML você deseja colocar o seu EventListener
2. Escolha uma reação (normalmente uma função que a gente cria) para este evento acontecendo

### addEventListener - em qual elemento HTML

Primeiro, devemos conseguir localizar **onde** colocar o nosso EventListener. Em qual elemento HTML devemos atrelar o EventListener?

Vamos usar uma tag de button como exemplo.

Imagine que essa button tag tem uma classe chamada "check". Para o EventListener, essa classe é como ele localiza esse elemento HTML específico: ```(".check")```

### Eventos - de que tipo? Um clique

Agora, o que ele deveria escutar? Um *clique*. 

Esse é o nosso evento, do nosso exemplo aqui. Mas tem toda uma lista de tipos de eventos que podem acontecer no DOM. Dá uma olhada em [the MDN Events categories](https://developer.mozilla.org/pt-BR/docs/Web/Events)

### Reação (Event Handler) - uma função

E o que deveria fazer depois que escutar o clique? Qual vai ser a reação?

Isso é o que chamamos de Event Handler ("Lidador/Cuidador de Eventos"). Como ele deve cuidar do evento clique?

Ele deve cuidar por meio de uma função. Lembre-se que em JS, **funções são valores**. Então, o Event Listener tem dois valores como parâmetros: o que ele espera (Event), o que ele faz (Event Handler). O segundo parâmetro é uma função. 

```javascript
// EventListener(dois, parâmetros)
// .addEventListener('event', function())

document.querySelector('.check').addEventListener('click', function () {
    console.log(document.querySelector('.guess').value)
}

// PS: Value é um atributo do DOM. Nós podemos acessá-lo por meio do ".value"
```

Nossa função é simples: ele printa o valor no console.

Vamos converter o input do usuário (que é uma string) para um number. 

```javascript

// Lembra que toda vez que um usuário deixa um input, 
// esse input vem pra gente como uma string. Então, se a gente
// tá lidando com números, devemos converter essa string
// para número por meio do método Number(). 

document.querySelector('.check').addEventListener('click', function() {
    console.log(document.querySelector('.guess').value) // > '5'
})

// String -> Number:
document.querySelector('.check').addEventListener('click', function () {
    const guess = Number(document.querySelector('.guess').value);
    console.log(guess, typeof guess);       // > 5 "number"
})

// PS: O CONTEÚDO DE TEXTO dos nossos elementos HTML também são atributos. 
// Dá pra acessá-los por meio do ".textContent" (assim como fizemos com ".value")
```

### Nem sempre dá pra depender do DOM
Algumas vezes você não vai conseguir pegar as informações no DOM, então é tranquilo colocar algumas variáveis dentro do seu código em vez de "pegá-las" do DOM. 

### Variáveis de Estado
Algumas variáveis podem ser chamadas de "state variables" (variáveis de estado) porque elas são uma parte do estado do DOM, que basicamente **são todos os dados que são relevantes para a aplicação**. 

## Manipulando CSS Styles
Dá pra mudar o CSS pelo DOM. 

Por exemplo, dá pra mudar toda a cor do background da página. 

Pra fazer isso, você deve selecionar o elemento HTML 'body' do document. Aí depois, você acessa a propriedade style, que na realidade é um atributo do DOM neste caso. Daí depois você consegue acessar os atributos CSS. 

Tipo assim. 

```javascript
document.querySelector('body').style.backgroundColor = '#60b347';

// ".style" é um atributo do DOM
```

Você também pode selecionar outros elementos HTML para mudar as propriedades do CSS. 

```javascript
document.querySelector('.number').style.width = '30rem';

// Aqui, a gente selecionou o elemento HTML ".number" e
// acessou o atributo "style" do DOM para "pegar" a propriedade
// "width" do CSS. 
```

*IMPORTANTE: Lembre-se de usar a propriedade style do DOM para especificar as propriedades CSS que deseja mudar. A propriedade CSS é chamada usando a notação em camelCase e sempre é uma string.*

## Projeto Modal 

*PS: As anotações dessa seção são referentes ao Modal Project que está nesse repositório. Veja na pasta [modal-project-example](https://github.com/barbaracalderon/notes-on-javascript/tree/main/project-modal-example) aqui.*

Primeiro, temos que selecionar cada elemento HTML com o qual vamos interagir. Depois, guardar esses valores em variáveis para tornar tudo mais simples. 

Observe o HTML document e veja quais classes são aquelas que vamos selecionar como elementos HTML para interagir.

A classe "hidden" vai ser a classe principal com a qual vamos lidar: é essa caixa grande que vamos lidar no navegador. 

As classes são: ```modal, overlay, hidden, show modal```.

*O overlay é a parte "blur" ou sem foco da página.*

Vamos selecionar essas classes e guardá-las em variáveis.

Assim.

```javascript
const modal = document.querySelector('.modal');
const overlay = document.querySelector('.overlay');
const btnCloseModal = document.querySelector('.close-modal');
```

E agora nós temos três botões com a mesma classe "show-modal". Se a gente tentar fazer a mesma coisa que a caixa de código anterior mostra... 

```javascript
// Só vai selecionar a primeira caixa
const btnsOpenModal = document.querySelector('.show-modal');
```

Não vai funcionar porque vai apenas selecionar a primeira caixa e não as três caixas modal.

Então como selecionar todas as três caixas?

Vamos usaar ```querySelectorAll``` em vez de apenas ```querySelector```. Assim, todos os botões agora estão dentro de uma lista e podemos iterar esta lista para manipular cada item dentro dela (no caso, três itens).

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

Eis o que vamos fazer: existem três botões na página. Nós vamos clicar em cada um desses botões e vai aparecer uma janela. Para fechar essa pequena janela (chamaremos de caixa), nós podemos clicar no X, clicar em algum local fora dessa caixa ou ainda apertar o ESC do teclado.

Perceba que são três formas diferentes de fechar a caixa.

Como fazer isso?

Primeiro, vamos manipular os botões "Open Modal" mostrados anteriormente. 

A caixa que deve abrir já existe... mas está **escondida** (*hidden*) pelo CSS. Isso porque no CSS, o display está como none (propriedade/valor). Ou seja, a caixa já está lá... nós é que não vemos. 

Para fazer a caixa aparecer, nós vamos clicar em qualquer um dos botões Open Modal e a reação vai ser remover a classe "hidden" da propriedade classList (propriedade do DOM). 

*PS: Parece que o DOM cria uma lista de todas as classes disponíveis para manipular. Quando a gente remove a classe "hidden", significa que ela se torna visível porque a classe "hidden" (e o estado CSS) não está mais alcançável.*

Agora a caixa aparece. Mas como vamos fechá-la? 

A gente adiciona (*add*) a classe "hidden" de volta para a classList do DOM. 

É o que vamos fazer. Olhe abaixo.

```javascript
const modal = document.querySelector('.modal');
const overlay = document.querySelector('.overlay');
const btnCloseModal = document.querySelector('.close-modal');
const btnsOpenModal = document.querySelectorAll('.show-modal');

for (let i = 0; i < btnsOpenModal.length; i++)
    btnsOpenModal[i].addEventListener('click', function () {
        modal.classList.remove('hidden');
        overlay.classList.remove('hidden');
    });

btnCloseModal.addEventListener('click', function () {
    modal.classList.add('hidden');
    overlay.classList.add('hidden');
});

overlay.addEventListener('click', function () {
    modal.classList.add('hidden');
    overlay.classList.add('hidden');
});
```

Perceba que tem muito código repetido.

Podemos fazer melhor. 

```javascript
const modal = document.querySelector('.modal');
const overlay = document.querySelector('.overlay');
const btnCloseModal = document.querySelector('.close-modal');
const btnsOpenModal = document.querySelectorAll('.show-modal');

const openModal = function () {
    modal.classList.remove('hidden');
    overlay.classList.remove('hidden');
}
const closeModal = function () {
    modal.classList.add('hidden');
    overlay.classList.add('hidden');
}

for (let i = 0; i < btnsOpenModal.length; i++)
    btnsOpenModal[i].addEventListener('click', openModal);
btnCloseModal.addEventListener('click', closeModal);
overlay.addEventListener('click', closeModal);
```

A lição pra aprender aqui é... **quando o seu código se repetir demais, você deve aplicar o princípio DRY**. Especialmente, se a mesma reação é usada em diferentes momentos - como abrir o modal (a caixa) ou fechá-lo. **Guarde essa função em uma variável (funções são valores em JS) e use essa variável para chamar essa função quando precisar.**

### Evento Global - pressionar a tecla 'ESC'

Apertar uma tecla é um evento global porque não acontece em algum elemento específico. Então, como reagir a eventos de teclado? 

Ainda precisamos usar o Event Listener.

Existem três eventos para teclados. Eles estão descritos abaixo.

Evento | O que faz
------ | ---------
**keydown** | ele aciona a reação assim que a gente aperta a tecla
**keypress** | ele aciona a reação continuamente enquanto o nosso dedo estiver apertando a tecla
**keyup** | só aciona a reação quando você **levanta** o dedo da tecla

Nós lidamos com esses eventos da seguinte forma. 

```javascript
// O console vai printar a mensagem quando QUALQUER tecla é apertada
document.addEventListener('keydown', function () {
    console.log('A key was pressed.')
})
```

Mas a gente não quer isso. A gente quer acionar uma reação, que é fechar o Modal (a caixa), só quando a gente pressionar a tecla 'ESC'.

```javascript
document.addEventListener('keydown', function (e) {
    console.log(e);
    if (e.key === 'Escape') {
        if (!modal.classList.contains('hidden')) {
            closeModal();
        }
    }
});
```

'ESC' é a mesma coisa que "Escape".

Podemos escrever melhor abaixo (código todo). 

```javascript
// Selecionando os elementos
const modal = document.querySelector('.modal');
const overlay = document.querySelector('.overlay');
const btnCloseModal = document.querySelector('.close-modal');
const btnsOpenModal = document.querySelectorAll('.show-modal');

// Abrir a caixa (Modal)
const openModal = function () {
    modal.classList.remove('hidden');
    overlay.classList.remove('hidden');
}

// Fechar a caixa (Modal)
const closeModal = function () {
    modal.classList.add('hidden');
    overlay.classList.add('hidden');
}

// Selecionar os três botões do Modal
for (let i = 0; i < btnsOpenModal.length; i++)
    btnsOpenModal[i].addEventListener('click', openModal);
btnCloseModal.addEventListener('click', closeModal);
overlay.addEventListener('click', closeModal);

document.addEventListener('keydown', function (e) {
    console.log(e);
    if (e.key === 'Escape' && !modal.classList.contains('hidden')) {
        closeModal();  // Olha essa função sendo usada mais vezes no código
    }
});

```

### O querySelector e o querySelectorAll

É como você seleciona um elemento HTML.

Tipo | Código
---- | ------
Classes | ```document.querySelector('.class')```
Id | ```document.querySelector('#id')```

Lembrando que pra selecionar mais de um mesmo elemento é por meio do ```querySelectorAll```

### Método Toggle

```element.classList.toggle("example")```

Esse pode ser útil!

Mude entre adicionar e remover um nome de class de um elemento com o JS. 

1. Se a classe tiver na classList, ele remove de lá. 
2. Se a classe não tiver na classList, ele inclui lá.

Além disso, você pode manualmente adicionar ou remover o nome de uma classe da classList por meio dos métodos de adicionar ("add") e remover ("remove): ```element.classList.add(".example")``` ou ```element.classList.remove(".example")```

### Função Init

Pode ser uma boa ideia criar sua própria função init.

Init vem de "initialization" que significa "inicialização". 

Isso pode funcionar bem em um projeto que tem condições de início que podem ser "resetados" pelo usuário dependendo de sua escolha. 

### Organização

Você tá começando agora. É uma boa prática organizar o seu código para não se perder nele mesmo. Ninguém gosta de código "spaghetti". 

Algumas ideias aqui. Comece com:

1. Selecionar os elementos
2. Selecionar os botões
3. Condições de início
4. Funções criadas para uso
5. O restante da lógica
6. Comentários para referência futura
7. Outros

