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