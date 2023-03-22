#¿Qué es Angular?

Angular es un popular framework de JavaScript para la creación de aplicaciones web, que ha recibido en 2017 un avance importante frente a la versiones anteriores,
mejorando su rendimiento, tamaño y sintaxis. En este curso aprenderás a crear aplicaciones con Angular, avanzarás paso a paso en su uso, desde la instalación,
configuración y arquitectura hasta la publicación final de una aplicación. Al final del curso habrás creado tu primera aplicación utilizando esta potente plataforma
elegida por miles de desarrolladores en el mundo y mantenida por Google.


#Modulos

Agrupa diferentes funcionalidades de la aplicación como rutas, servicios, librerias, etc, todos los elementos con los que vamos a trabajar en nuestra app

#Plantillas 

Parte visual de un componente, HTML con inyección de datos

#Directivas

Directivas estructurales agregan/eliminan elementos

Directivas de atributo cambian la aparencia o comportamiento de elementos


#Componentes

Para generar un  componente utilize el siguiente comando de angular CLI: ng generate component <nombre_del_componente>

@Component({
    selector: 'app-app',
    templateUrl: 'ruta/component.html',
    styleUrls: [ ''ruta/componenet.css ]
})

Los decoradores nos van a permitir configurar el componente, dentro de los decoradores tenemos 3 propiedades:

Selector: Es la forma de invocar o llamar el componente en HTML

templateUrl: Define la ruta o la plantilla del componenete

styleUrls: Define la ruta de los stylos


Dentro de la clase de un componente podemos encontrar dos elementos:

Constructor(){}: Se inicializa junto con la aplicación

NgOnit(){}: Se inicializa al momento de utilizar el componente


Para mostrar variables de TS en HTML podemos utilizar llaves dobles {{ variable }}

#Enviar datos a un componente:

Podemos enviar datos del componente padre al hijo con @input. Para ello debemos modificar el selector hijo agregando entre corchetes [] nombre de la variable y
asignandole un valor, EJ:

<app-component [variable] = " 'valor' " ></app-component>

En el componente hijo se debe importa @Input y se debe colocar el nombre de la variable que recibe del padre:

TS: @Input() variable


#Directiva NgIf

Esta directiva sirve para ocultar o mostrar secciones de HTML, EJ:

variable = 2

<div  *NgIf="variable = 2" >
    Cumple condición
</div>


Uso del ELSE con la directiva NgIf:

<div  *NgIf="variable = 2"; else otroTexto >
    Cumple condición
</div>

<ng-template #otroTexto>
    Se muestra si no Cumple la condición
</ng-template>


#Controlar estilos con NgStyle y NgClass

NgStyle es una directiva que nos permite injectar directamente estilos en un elemento de HTML:

<div [NgStyle]="{'color': 'verde'}" >
    Elemento
</div>

NgClass es una directiva muy parecida a NgStyle, pero lo que hace es injcetar una clase:

https://angular.io/api/common/NgClass


#NgFor

Esta directiva sirve para desplegar una lista de Objetos en HTML

TS:
    this.object = ["uno", "dos"];

HTML:
    <li *NgFor="let item for object"> {{item}} </li>


Se puede obtener el index de un elemento:  <li *NgFor="let item for object; i = index"> {{item}} {{i}} </li>


#Enrutamiento angular

Se genera el proyecto y se marca la opción de agregar routing.

Se modifica en el archivo app-routing.modules.ts, donde consta de parametros dentro del objecto routes

siempre debe tener definido un path y el componente que vayamos a trabajar:

const routes: Routes = [{
    path: '', component: myComponente
}]

para que funcionen los enrutamientos se debe definir en el archivo app.component.html el selector:

<router-outlet> </router-outlet>

== Navegación por rutas ==

Utilizar los atributos que Angular posee sobre el enrutamiento ayudará a indexar mucho mejor las aplicaciones

Navegación por link:
[RouterLink]="['/mi ruta']"


Enviar información mediante rutas, se utiliza una sintaxis especial:

const routes: Routes = [{
    path: 'ruta/:variable', component: myComponente
}]

Leer información de rutas dinamicas:

En el componente se debe importar el modulo ActivateRoute:

Constructor(private Ruta: ActivateRoute){
    variable: any;
}

this.variable = this.ruta.paraMap.get('variable de la ruta');


#Servicios en Angular

Un servicio nos permite reutilizar código o hacer comunicación de información a varios componentes

Para generar un servicio se debe lanzar el comando:  ng generate service miServicio


#Conectar o obtener datos externos

Para trabajar con datos externos es necesario importar en el archivo de modulos HttpClientModule

Luego para trabajar con los datos en local, se debe importar en el componente HttpClient, siempre que debemos trabajar con estos datos
nos debemos suscribir, ya que nos devuelve un observable

Para el manejo de errores de conexión HTTP, se agrega un parametro adicional en el subscribe que valida la llamada de este


#Renderer

Sirve para trabajar un elemento de HTML que tengamos en el componenete, para utilizarlo se debe importar Renderer2, se inicializa en el Constructor

En el html se debe asignar al elemento la variable #variable

<p #miParrafo> Hola </p>

Docu:
https://angular.io/api/core/Renderer2#renderer2


#Optimizar

ng build --prod

Este comando ayudará a compilar la aplicación y a utilizar todos los ajustes de optimización propios de un servidor de producción.






