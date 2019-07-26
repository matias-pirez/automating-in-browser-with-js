

Automating in the browser with javascript 


todo vanilla javascript:  http://todomvc.com/examples/vanillajs


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
-Ir plasmando las cosas en un git. 

