

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


## If statements

Aca combinamos el for anterior con un if. 

for (togglepos=0; togglepos<toggles.length; togglepos++){
	if (togglepos%2==1){
		toggles[togglepos].click();
	}

}

Esto se fija que si el modulo de la posicion es igual a 1, o sea 0%2 para la primera, es igual a 0, entonces no lo clickea porque es false. Estaria clickeando las posiciones pares 2, 4. Se pone igual a 1, poruqe la primera posicion es 0 y no 1. 

Se podria hacer sin el if, incrementando en el for en 2 en vez de uno // togglepos+=2

Tambien se podria hacer incrementando uno, pero usando una variable temporal. 
var toggleit = false
for (togglepos=0; togglepos<toggles.length; togglepos++){
	if (toggleit){
		toggles[togglepos].click();
	}
	toggleit=!toggleit // esto transforma toggleit en su opuesto (true para la priemera vez)
}


## Snippet view

En la consola de chrome hay una opcion snippets dentro de Sources que te permite guardar codigo, ejecutarlo y  debuguearlo desde ahi mismo.


## Bookmarklets 

Se puede ejecutar codigo javascript desde un marcador de chrome. En URL se debe agregar el codigo que tiene el siguiente formato

javascript:(code)()

Ejemplo para crear n toDos

javascript: (function (){
    max = prompt(how many todos?)
    if (max){
        for (x=0; x<=max; x++){
            setTimeout(function(name){
                document.querySelector('input.new-todo').value = name;
                document.querySelector('input.new-todo').dispatchEvent(new Event {'change',
                    'bubbles':true
                })
            })
            x*100, "todo " + x)
        }
    }
})
