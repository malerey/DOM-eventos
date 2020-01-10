# DOM: eventos


#### Eventos
* Manejo de eventos del DOM
* Prevenir eventos por defecto
* Interacción con el mouse
* Interacción teclado

* El browser dispara eventos cuando pasa algo con el documento o el browser
* Por ejemplo podemos saber cuando se terminó de cargar un documento, se presiona una tecla o se mueve el mouse
* Un evento consta de las siguientes partes:
  * **Tipo de Evento:** es el nombre del evento que ocurre
  * **Target del evento:** es el objeto al cual le ocurre el evento o que está asociado a dicho evento
  * **Manejador de evento:** es una función (callback) que maneja o responde a un evento (Se lo conoce también como listener)
  * **Objeto del evento:** es un objecto asociado con un evento en particular que contiene detalles sobre el evento. Este objeto es pasado como parámetro de la función que maneja el evento. Las propiedades de este objeto cambian según el tipo de evento que sea. Ejemplo: puedo saber que tecla se presiona o posición del mouse dependiendo del tipo de evento que maneje.
* Existen 2 formas básicas de registrar un manejador de eventos
* Establecer una propiedad en el objeto o document
**Ejemplo:**
```js
var button = document.querySelector('button');
button.onclick = function() {
  // código para manejar que se hace al hacer click en el botón
}
```

* La otra opción es registr un evento con `addEventListener`
* Este método puede ser aplicado en cualquier objeto, eso incluye window, document y en todos los elementos.
* Este método soporta 2 parámetros:
  * **Tipo de evento:** es un string con el nombre del tipo de evento
  * **Manejador de evento:** es una función que se invoca cuando suceda evento
**Ejemplo:**
```js
var button = document.querySelector('button');
button.addEventListener('click', function() {
  // código que maneja el click del botón
});
```
* Dentro de la función que maneja el evento podemos utilizar la palabra reservada `this` que en ese contexto hace referencia al objeto que ejecutó el evento
**Ejemplo:**
```js
function clickHandler() {
	console.log(this)		// this en este caso apunta al elemento que ejecutó el evento
}

var button = document.querySelector('button');
button.addEventListener('click', clickHandler);
```

* Podemos capturar algunos eventos del mouse, entre los más conocidos se encuentran: `click, dblclick, mouseover, mouseout y mousemove`
* El objeto evento asociado al mouse tiene atributos que nos permite saber la posición donde se encuentra con clientX y clientY

**Ejemplo:**
```js
var body = document.querySelector('body');
body.addEventListener('click', function(evento) {
  evento.clientX;
  evento.clientY;
});
```

* También podemos controlar los eventos que se disparan cuando se presionan las teclas por medio de los eventos `keypress, keydown y keyup`
* El objeto del evento tiene propiedades como `charCode` que nos retorna el número de tecla que fué presionado
* Con el método `String.fromCharCode` podemos saber que letra es

**Ejemplo:**
```js
var body = document.querySelector('body');
body.addEventListener('keypress', function(evento) {
  evento.charCode;
  String.fromCharCode(evento.charCode);
});
```

#### Lista de eventos que se pueden utilizar:
* Existen muchos eventos que podemos utilizar para crear UI interactivas:
  * onchange
  * onclick / ondblclick / onmousedown / onmousedown
  * onmouseover / onmouseout
  * onkeydown / onkeypress / onkeyup
  * onload
  * onresize
  * onscroll
  * oninput
  * onfocus / onblur
