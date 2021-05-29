# EN: Document Object Model (DOM)

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

## addEventListener

Our code will react to something that happens in the application. But how will it know when something happens? By *listening to an event* through the ```addEventListener``` method. 

An ```event``` is something that happens in the page, like a mouse click, a mouse hover, a key press, and more. 

With the Event Listener, the code will be waiting for the event to happen, watchful and "listening" to whatever action happens (metaphor intended). When the expected event happens, our code will react to it. 

How to do this?

## Handling Click Events

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

### Reaction - usually a function
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


---

# PT: Document Object Model (DOM)

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


## addEventListener

Nosso código vai reagir a alguma coisa que acontece na aplicação. Mas como vai saber quando algo acontece? *Escutando (listening) um evento* por meio do método DOM ```addEventListener``


Um ```evento``` é algo que acontece na página, como um clique do mouse, um passeio do ponteiro sobre algo (hover), apertar uma tecla, e mais. 

Com o Event Listener ("Escutador de Eventos"), o código vai esperar o evento acontecer, bem atento e "escutando" qualquer ação que aconteça (é uma metáfora esse "escutando"). Quando o evento esperado acontece, nosso código vai reagir a ele. 

Como fazer isso?

## Lidando com os Eventos de Clique

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
