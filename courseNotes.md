

#Automating in the Browser Using Javascript 

Link: https://testautomationu.applitools.com/automating-in-the-browser-using-javascript/



Web utilizada- todo vanilla javascript:  http://todomvc.com/examples/vanillajs


document.querySelectorAll() -- selecciona todos los que encuentre
document.querySelector() -- selecciona el primero que encuentre
document.getElementbyId() - se puede usar si tenemos un selector con ID
document.getElementsByClassName() - se puede usar cuando tenemos un selector con nombre de clase .clase

Selecciona y clickea el boton de Mostrar todos los to dos
document.querySelector("#toggle-all").click()


Para ir a los filtros

Puedo hacer: 

document.querySelector ("ul.filters li:nth-child(3) > a").click()
Esto es localizar el botón y hacerle click, es un link por eso el a

esto está con un hashchange (lo veo en el event listener)
entonces puedo hacer 
location.hash y me dice en cual estoy

si hago location.hash = "/active" me va a mostrar solo las activas, es lo mismo que clickear en el botón de activas. 

Con esto agrego un nuevo todo
document.querySelector("input.new-todo").value="New automated todo";
document.querySelector("input.new-todo").dispatchEvent(new Event('change', {"bubbles":true}));

Hago doble click sobre un todo para cambiarlo
document.querySelector("ul.todo-list > li:nth-child(1) > div > label").dispatchEvent(new Event('dblclick', {'bubbles':true}))
document.querySelector("ul.todo-list > li:nth-child(1) .edit").value="Todo modificado2";
document.querySelector("ul.todo-list > li:nth-child(1) .edit").dispatchEvent(new Event('blur'))


----Practicar la lección de For loops. Definir Gherkins para Todomvc.

## Chapter 5 - For Loops
Cómo hacer para seleccionar todos los items de la lista de forma automática: 
Un for loop nos sirve para eso. Básicamente lo que hace es, se establece una variable como contador, y mientras se compla la condición hace algo que le indiquemos. 

Importantísimo la estructura y no olvidar de incrementar el valor del contador con el ++. 

Ejemplo: Esto nos escribe en la consola Hola1, Hola2, hasta 20.

for (counter=1; counter <=20, counter++){
	console.log("hola"+counter)
}


Entonces por ejemplo si tengo este selector .todo-list .toggle, en la página TODOMVC, este selector nos selecciona todos los toogles de marcar/desmarcar como completo.

Para seleccionarlos todos con js hago esto: 
document.querySelectorAll(".todo-list .toggle")
Me devuelve un array con los 6 toggles correspondientes a los items que tengo en la lista.

¿Cómo lo puedo aplicar dentro del for?

Guardo ese query en una variable:

var toggles = document.querySelectorAll(".todo-list .toggle")

Si hago un toggles.length me devuelve la cantidad de valores del array, en este caso 6.
Entonces el for me queda, que arranca en el primer toggle (posicion 0) y lo sigue haciendo hasta que la posisición sea el largo o sea 6. Y para cada uno de esos, me va a hacer click en el toggle. 

for (togglepos=0; togglepos<toggles.length; togglepos++){
	toggles[togglepos].click();
}