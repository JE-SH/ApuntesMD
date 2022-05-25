# LaunchX

## Vue

### Instalación

Para empezar verificar que esté `npm install -g @vue/cli`

Creación de nuevo proyecto vue `vue create nombre-proyecto` . ***Nota:*** Para la creación de proyectos desde consola de Visual Studio, verificar que la consola esté en CMD (comand promp)

Para AGREGAR otras carpetas seleccionar **Manually** y dejar <u>Babel, router y vuex</u>, quitar linter

Poner <u>versión 3x, no, dedicado, no</u>

Para correr el server, estar dentro de carpeta de proyecto en consola y typear `npm run serve`.

### Inicio

Dobles significan una variable.

Div "app" se utiliza para poner contenido. Este se puede convertir en método dentro de otro archivo:

```html
const app = Vue.createApp({
    data() {
        return{
            nombre:'Rodrigo'
            ...
            foto
        }
    },
    methods:{

    }
})
app.mount('#app');
```

El "método" app se va a montar en el div con *class='app'*. 

Vue binding: mandar parámetro dentro del mismo vue. -> `v-bind`

    `v-on`: se usa para botones: `... v-on:click = "cambiarUsuario()... "`

Para ahorrar se puede poner solo los `:`.

Sei se desea, quitar todos los componentes con *HELLOWORLD* para evitar errores.

### Api

Para realizar consultas a api's de manera asincrona se puede hacer:

```html
methods:{
        async cambiarUsuario(){
            const res=await fetch('https://link');
            const {results} = await res.json();

            this.nombre = results[0].name.first
            ...
        }
    }
```

--

Objetos en json son con `nombre: valor`.

--

`$store.dispatch('bajarContador')` manda llamar a parte de acciones.

`$store.commit('bajarContador')` manda llamar a parte de mutaciones.

### Partes

**Main** >> app.vue

**< assets:** Archivos multimedia

**< components:** Diviciones para la aplicación. Botones, carruseles, etc.

**< router:** fáciles e intuitivas

**< views:** vistas 

**Estados:** información e e sitio, lo que está sucediendo independiente de vistas y componentes.

    *state* información que se estará manejando. Variables, cambios de movimiento.

    *getters* para recuperar información del estado.

    *mutations* modifica el estado.

    *actions* como mutación, PERO, con código asíncrono (consulta api's), manda llamar a mutación

    *modules* para siertas páginas

**component:** 

    export default{
        name:'App',
        components: {
            HelloWorld
        }
    }

**props:** parámetros que se van a mandar desde otros lados. Se mandan como atributos. Se le declaran parámetros. ej:

    export default{
        name:'HelloWolrd',
        props: {
            msg: String
        }
    }

**Style** aplica estilos a todas las páginas (ej. App.vue)

**Style scoped** aplica estilos solo a página actual (ej. HelloWorld)

commit para mutaciones

dispatch para acciones

# Backend

## POO

El software tiene que tener una alta cohesión y un bajo acoplamieto. Así es legible, reutilizable, mantenible.

**Objeto** 

Tiene lista de características.

**Abstracción** 

Captar componentes dentro de algun modelo. Reconocer **características escenciales**. Lo que lo hace ser un árbol.

**Encapsulamiento** 

Oculta las características no relevantes de una clase. Especialidades de una profeción.

**Modularidad** 

Lo que conforma a la profeción.

     __Qué puede hacer__ .  

**Polimorfismo** 

Diferentes comportamiento que puede llegar a tener.

* Primitivo/Overload :email: 
  
  :battery:<u>Sobrecarga</u> de métodos. Se comunica de diferentes maneras. 
  
  Licenciado e ingeniero :man_health_worker::construction_worker_man:. Varios roles. :performing_arts::man_dancing:

* Real/Override :pen:
  
  :book:<u>Redefinición</u> de métodos. 
  
  Cada clase puede "comer" pero de manera diferente".

```java
class Bike{
    void run(){
    System.out.println("rinning...");
}}

class Poli extends bike{
    Override    
    void run(){
    System.out.println("running safely...")
  }
    public static void main(){
      //Bike b = new Bike();
    Bike b = new Poli();//Ligadura dinámica - upcasting 
  }
}
```

* Grenérico/Overwrite

**Pojo** 

Clases 

**Setters y getters** 

**Coesipo / cohesión** 

Métodos que hagan tarea específica y bien hechas.

Su función es definir. El programa hace una sola cosa bien.

*Clase* modela un objeto, en encapsula en una sola cosa.

**Bajo acoplamiento** su unica relacion son objetos. -> Buen código <- Alta cohesión

Operador de indirección->

:gear:**Reingeniería**

Reestructurar toda la programación.

:arrows_clockwise:**Refactor**

Hacer código legible. 

:chopsticks:**Monolito**

Código en una sola linea/archivo.

Programación en un solo documento

:ninja:**Objetos anónimo.**

`  new Gato().printColor();`

**Definiciones**

----

| :bookmark_tabs:Clase: Conjunto de <u>objetos</u> con características similares que se identifican por nombre, atributos y una serie de funciones o métodos aplicables a todo el conjunto. Es una plantilla para caracterizar o definir objetos. |
| ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |

| :leaves::art:Abstracción: Es la facultad intiuitiva del ser humano que le permite conocer la <u>escencia</u> de las cosas. |
| -------------------------------------------------------------------------------------------------------------------------- |

| :microscope:Modularidad: Es un proceso mental que permite <u>distinguir</u> los componentes de los objetos que estan siendo estudiados. |
| --------------------------------------------------------------------------------------------------------------------------------------- |

| :globe_with_meridians:Encapsulamiento: Permite <u>ocultar</u> las características no relevantes de una clase, destacar las relevantes y modelar su comportamiento. Dando como resultado la Abstracción de Datos. |
| ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |

| :man_beard:Herencia: <u>Relación</u> entre clases cuya existencia depende de un ancestro, la clase base delega sus atributos y métodos a las clases derivadas. |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------- |

| :book::pen:Polimorfismo: Es el conjunto de operaciones <u>aplicables</u> a un objeto por medio de los mensajes que invocan a alguno de los métodos definidos en la clase a la que pertenece el objeto de acuerdo al dominio de la aplicación (Contexto). |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |

| :egg::santa:Objeto: Es una <u>entidad</u> real o imaginaria que tiene identidad, estado y un comportamiento, conforme al conjunto de objetos (clase) a la que pertenece. Es una instancia de una clase. |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |

| :ear_of_rice: Campo semántico: De un baño -> papel, jabón, cepillo, shampoo... |
| ------------------------------------------------------------------------------ |

<u>Una clase de java contiene lo siguiente</u>

* Campos

* Métodos

* Constructores

* Bloques

* Clases anidadas e interfaces

----

**Método** 

`nivel_de_acceso tipo_static valor_de_retorno nombre_método(){    }`

Un constructor no es método porque no se puede acceder a el :arrow_heading_down:. 

**:busts_in_silhouette::couple_with_heart_woman_man: Acoplamiento**

Medida de dependencia entre dos módulos: Están bien relacionados.

Tiene diferentes grados: Alto, medio, bajo->escecial.

**:gear::gear: Cohesión**

Cada clase/método hace una sola cosa y la hace bien.

Tiene niveles: Alto, bajo.

**Relaciones**

* **:department_store: Asociación**

Es un...

Si entre dos o más clase hay interacción que no modificará nada el comportamiento del objeto 

  Modo de interacción donde no utilizas interacción a corto plazo.. .. 

  Persona :standing_person: <u>usa</u> una bicilceta :bike: 

* :heavy_plus_sign: **Agregación**

Tiene un...

Si <u>afecta</u> comportamiento entre ellos.

Mientras dura relación.

Computadora :computer: <u>tiene</u> mouse :computer_mouse:, teclado :keyboard: 

* :notes: **Composición**

Contiene...

Si las separas :arrow_left::arrow_right: deja de ser un bojeto

Entre objetos existe asistencia de pormedio.

Lapiz :pencil2: contiene grafito y borrador

**:man_beard: Herencia**

Relación dependiendo el ancestro padre-hijo. Lo que se le puede compartir. Características que comparten.

* Simple

Empleado->Programadora

_Es un_ :standing_person:->:man_factory_worker:

* Multinivel

Empleado->Programadora->web

(En cadena) :standing_person:->:man_factory_worker:->:man_office_worker:

* Gerarquica

Empleado->Programador & Empleado->web

(En opciones)

:standing_person:->:man_factory_worker: 

:standing_person:->:man_office_worker:

Nuevas clases a partir de referencias. Asociación.

Relación de herencia :deciduous_tree::rhinoceros::standing_person:<u> es un </u>, :atom_symbol: <u>contiene un</u>, :shirt: <u>usa un</u> y :watch: <u class="ag-inline-rule ag-raw-html"><span class="ag-plain-text">tiene un</span></u>

Extiende o especielizar características base a una específica.[]()

Clase derivada se beneficia de herencia.

`extends`

Al hacer extend no se puede tener diferente tipo de acceso. 

Una persona <u>puede ser</u> un empleado.

```java
class Persona{ //privado
  ...
Persona(){
  System.out.println("Hola")
  }
}
public class Emp extends Persona{ //error
...  
  Emp(){
  super() //Pimero lo que diga la clase padre
  System.out.println("Mundo")
  }
}
```

Clase padre/maestra es el modelado de la clase principal.

:part_alternation_mark:**Firma/Signatura**

Permite distinguir sin ambigüedad a los métodos: su declaración y su invocación.

* Valor

* Tipo

* Parámetros

Redefine métodos para la herencia.

## Comandos iniciales

`publis static void main` para iniciar con el primer método (psvm).

## :spider_web: Hilos

Sub-procesos ligeros. 

Multitarea -> multiproceso o multihilo.

Proceso con espacio de memoria.

Cambios de proceso pesan :weight_lifting_man:.

Cada proceso asigna espacio de memria y guarda registros de donde está el espacio.

:twisted_rightwards_arrows:Hilos comparten mismo espacio :artificial_satellite:.

:car:Distribuidor vial -> Toma diferentes caminos sin cambiar el sentido. Menos costosos.

Estados

* 

* Running

* 



**Paralelismo**

Multiples hilos. Soporta multiples peticiones



**Concurrencia**

Procesa todas las solicitudes. Se acomodan en grupos.



### Proyecto

Crear dentro de src nuevo package semana 1    
