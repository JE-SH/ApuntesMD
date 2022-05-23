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

**Objeto** 

Tiene lista de características.

**Abstracción** 

Captar componentes dentro de algun modelo. Reconocer **características escenciales**. Lo que lo hace ser un árbol.

**Encapsulamiento** 

Oculta las características no relevantes de una clase. Especialidades de una profeción.

**Modularidad** 

Lo que conforma a la profeción.

     __Qué puede hacer__ .  

**Herencia** 

Relación dependiendo el ancestro padre-hijo. Lo que se le puede compartir. Características que comparten.

**Polimorfismo** 

Diferentes comportamiento que puede llegar a tener.

**Pojo** 

Clases 

**Setters y getters** 

**Coesipo** 

Su función es definir. El programa hace una sola cosa bien.

*Clase* modela un objeto, en encapsula en una sola cosa.

**Bajo acoplamiento** su unica relacion son objetos. -> Buen código <- Alta cohesión

Operador de indirección->

**Método** 

`nivel_de_acceso tipo_static valor_de_retorno nombre_método(){    }`

Un constructor no es método porque no se puede acceder a el. 

### Proyecto

Crear dentro de src nuevo package semana 1

## 
