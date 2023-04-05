# Laravel

Notas hechas del curso Laravel de Coders Free

Patrón de diseño vista-controlador.

Para ingresar al local host poner liga http://localhost/nombre-archivo/public/

Herramientas: 

* laravel blade snipets

* php inteliphense

## Nuevo proyecto :page_facing_up:

**Crear nuevo documento laravel:** `laravel new nombre_proyecto`

Para ingresar al proyecto: `localhost/nombre_proyecto/public` dentro del navegador :globe_with_meridians:

Patron front controller

Mantiene un patrón vista:eye_speech_bubble: - controlador:video_game: 

## Rutas :motorway:

<u>Patrón: front controller</u>. Un solo punto de entrada a aplicación -> Index.php de la carpeta puclic.

Por seguridad no se ingresan a otras carpetas.

Todas las rutas deben estar dentro de routes/web, donde se establecen el nombre de las rutas

```php
Route::get('nombre_url', function(){  //función anonima para retornar Bienvenido cursos
    return "Bienvenido a cursos";
});
```

Si se manda una variable después de la '/' del url:

```php
Route::get('cursos/{nombre_de_variable_a_recibir}', function($nombre_de_variable_a_recibir)){
    return "Bienvenido al curso $nombre_de_variable_a_recibir"
}
```

Extenciones para facilitar esta tarea:

**laravel snippets** -> Route...

Debido a que el código se lee en cascada :fountain: se puede **reordenar** :one::three::two: la secuencia con la que se leerá el código.

Para agregar variables opcionales se agrega el signo *?* y la variable se inicializa en la función.

```php
    Route::get('cursos/{variable_1}/{variable_2?}', function($variable_1, $variable_2 = null)){
    if($variable_2)
         return "Bienvenido al curso $variable_1 de la categoría $variable_2"
    else 
         return "Bienvenido al curso $variable_1" 
    }
```

Debido a que es mucho código en las rutas, se puede pasar a un **controlador**.

## Controlador :video_game:

### Diagrama de ruta

:motorway:

1. Petición de usuario (asignado a) -------------------------------------- 

:arrow_down:                                                                                            :arrow_up:

2. Controlador (revisa petición y da orden a)            (Deriba datos a) :arrow_right: 4. Vista (Muestra y llena documento html)

:arrow_down:                                                                                             :arrow_up:

3. Modelo (retorna cierta información de la base de datos) 

### Crear controlador por comando :computer:

1. Entrar a la carpeta del proyecto desde consola.

2. ingresar `php artisan make:controller Nombre_del_controadorController` (controller al final) (Se puede abrir terminal de visual studios con ctrl+ñ).

3. Crear métodos de rutas al controlador.

### Implementación

El **namespace** es de dónde está el archivo del controlador.

```php
//dentro de web.php
//agregar:
use App\Http\Controllers; // dirección del controlador
...
Route::get('/', HomeController::class);
```

```php
//dentro de controlador
<?php
namespace App\Http\Controllers;
use Illuminate\Http\Request;

class HomeController extends Controller
{
    public function __invoke()
    {
        //return "Bienvenido a cursos"
        //return "Bienvenido";
        return view('welcome');
    }
}
```

Con **invoke** se administra **una** sola **ruta**.

Para administrar **varias rutas** se puede omitir.

```php
<?php

namespace App\Http\Controllers;

use Illuminate\Http\Request;

class CursoController extends Controller
{
    public function index() // para página principal de cursos
    {
        return "Pagina principal";
    }
    public function create() //para crear formularios
    {
        return "Crear curso";
    }
    public function show($curso) // para mostrar curso / se agrega variable a recibir
    {
        return "Bienvenido al curso $curso";
    }
}
```

:arrow_down:

  Para mandar llamar a las vistas:

```php
<?php

namespace App\Http\Controllers;

use Illuminate\Http\Request;

class CursoController extends Controller
{
    public function index() // para página principal de cursos
    {
        return view('cursos.index');
    }
    public function create() //para crear formularios
    {
        return view('cursos.create');
    }
    public function show($curso) // para mostrar curso / se agrega variable a recibir
    {
        return view('cursos.show',compact('curso')); // como segundo parámetro se agrega array, 
        //                              =
        //return view('cursos.show',['curso'=> $curso]); 
    }
}
```

Cuando se tienen varias **rutas** dentro se agrega el nombre del controlador, la palabra class y el nombre de la siguiente página dentro del archivo *<u>web.php</u>*:

```php
Route::get('cursos', [CursoController::class, 'index']);
//Route::get('cursos', 'CursoController@index'); Laravel <7
Route::get('cursos/create', [CursoController::class, 'create']);
Route::get('cursos/{curso}', [CursoController::class, 'show']);
// una sola página 
Route::get('/', HomeController::class);
//Route::get('/', 'HomeController'); Laravel <7
```

## Vista :eye:

Estos archivos están en <u>resourses/view</u>

Para mantener orden en los trabajos se puede crear una carpeta para todo lo relacionado a las susiguientes páginas de 'cursos', poniendoles nombre como si fueran parte de una página principal.

Ej: 

cursos :open_file_folder:

    index.php

    create.php

    show.php

Dentro del <u>HomeController</u> para solicitar vista se agrega `return view(home)`

Dentro de la vista de Home se agrega:

` <h1>Bienvenido al curso <?php echo $curso;?> </h1> `     

Pero antes de eso se ha creado una *<u>plantilla</u>* para agregar los html más fácil.

Dentro de **views** :open_file_folder: se agregó *<u>layouts</u>*:open_file_folder: para agregar la plantilla principal.

Se le agregan los yields para poder cambiar el nombre de la respectiva área en páginas posteriores.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>@yield('title')</title>
    <!-- fav icon -->
    <!-- estilos -->    
</head>
<body>
    <!-- header -->
    <!-- nav -->
    @yield('content')
    <!-- footer -->
    <!-- script -->
</body>
</html>
```

Esto para que la vista de *<u>home</u>* se vea así:

```php
@extends('layouts.plantilla')

@section('title', 'Home') //que  va a cambiar, por lo que se va a cambiar
                        //en caso de querer usar una variable usar:

//@section('title', 'Curso ' . $curso)
@section('content')
    <h1>Bienvenido a la página principal del principio</h1>
//    <h1>Bienvenido al curso {{$curso}} </h1>

@endsection //término de la sección
```

**extends()** hace la referencia a la carpeta de *<u>views</u>* , agregando la carpeta <u>layout.archivo</u>

Se pueden usar **variables** y **asignar** nombre a la página con title.

Esto se usa para evitar usar muchos comandos en php, reemplazando `<?php echo $curso; ?>` por :arrow_right: `{{$curso}}`

En caso de que no se reconozcan los extend, **verificar** que esté con nombre de home.blade.php

## Base de datos :minidisc:

Se debe dar a Laravel las credenciales.

Si se usa **xampp** se entra a <u>localhost/phpmyadmin/</u>

Para poner credenciales de base de datos se abre el archivo <u>.env</u> 

Por defecto ya vienen datos, solo revisarlos

#### Migraciones

Al momento de manipular la base de datos se realiza con las migraciones.

Dentro de <u>database/migrations</u> se encuentran las acciones a realizar dentro de la base de datos.

Se puede ver la página de [Database: Migrations - Laravel - The PHP Framework For Web Artisans](https://laravel.com/docs/9.x/migrations)

Para realizar las **migraciones** se escribe en consola `php artisan migrate`

Las migraciones se realizan por lotes, es decir que cada vez que se hace una migración, dentro de la DB se guarda registro de los cambios con un id.

#### Nueva migración

Con `php artisan make:migration cursos` se puede crear una nueva migración desde cero. Es recomendable que desde artisan se haga este paso para que sea más fácil. Con 

Para ahorrar pasos se puede utilizar la sintaxis `php artisan make:migration create_cursos_table`

Existen dos métodos: up y down, los cuales pueden realizar acciones y revertirlas respectivamente. 

```php
public function up()
{
    Schema::create('users', function (Blueprint $table)
//Se utiliza la clase schema y el método create para hacer una tabla
//El primer parámetro será el nombre de la tabla y una función anónima.
//Dentro de la función anónima se crea un objeto de tipo Blueprint a cual se le llamará table.
    {
//con table se puede hacer referencia a lo que se va a crear
            $table->id();
            $table-> [...]
    });
}
```

#### Eliminar migración.

Con `php artisan make:rollback` se puede devolver a la última migración que se hizo. Las migraciones que se vayan haciendo a la base de datos con la línea de comandos, se crea al momento un registro con la migración que se hizo y un número de lote. Este número permite tener un historial para cuando se haga <u>rollback</u>, se pueda regresar un lote antes, es decir, si ya llevamos 4 migraciones hechas, con rollback regresa cuando habíamos hecho 3.

Si se ejecuta `php artisan migrate:fresh` se eliminarán (drop) todas las tablas/migraciones y se volverán a hacer con up. Debido a que **destruye** todos los datos para volver a subir las tablas a la base de datos no es factible para hacerlo en producción. Se puede usar cuando se quiere modificar campos de las tablas en desarrollo.

Cuando se ejecuta `php artisan migrate:refresh`, se ejecutará el código con de la función down de **todas** las migraciones y luego el up.

#### Modificar tabla con migración

En caso de necesitar un campo más en una tabla en producción se crea una migración más: `php artisan make:migration add_camponuevo_to_nombretabla_table`, de esta forma 

```php
public function up()
    {
        Schema::table('users', function (Blueprint $table) { //el método table se usa para modificar la tabla que se mencione
            $table->string('avatar')->nullable()->after('email'); 
// nullable para poner null como opción 
// after para acomodarlo después de una columna
        });
    }
public function down()
    {
        Schema::table('users', function (Blueprint $table) {
            $table->dropColumn('avatar');
        });
    }
```

Para poder modificar estructura de datos de la tabla primero agregar la dependencia `composer require doctrine/dbal`, luego como si fuera otra migración `php artisan make:migration cambiar_propiedades_to_users_table`

```php
public function up()
    {
        Schema::table('users', function (Blueprint $table) {
            $table->string('name',100)->nullable()->change();
        });
    }
public function down()
    {
        Schema::table('users', function (Blueprint $table) {
            $table->string('name',255)->nullable(false)->change();
        });
    }

```



#### ORM Elocuent

Técnica de programación que sirve tratar **registros** como **objetos **y cada objetos tiene sus propiedades. 



se crea modelo con php artisan:

`php artisan make:model nombreModelo` este nombre puede ser por **convención**: un modelo "Curso" para administrar una tabla "cursos", se agrega el plural con una 's', pero del **inglés**.

Se crea:

`php artisan make:model Curso`

Con esto se crea una carpeta :open_file_folder: dentro de: <u>app </u>:open_file_folder: / <u>Models</u> :open_file_folder: / Curso.php :bookmark_tabs:



Se tiene clase Curso extendida de Model -> accede a todos los métodos: create, update, delete ... para tratar registros como objetos.



Estos modelos se **llaman** desde **controladores**, pero como aun no se puede mandar o recibir por formularios se usa **tinker**.

(Artisan console documentación de laravel)



Para abrirlo se agrega `php artisan tinker` con esto se cambia a tinker. 

Dentro de <u>consola</u>: 



```tinker
use App\Models\Curso; %% uso del modelo curso
$curso = new Curso; %% instancia de la clase / la variable es nueva instancia Curso
%%Llenarla de propiedades
$curso->name = 'Laravel';
$curso->description = "El mejor framework de PHP";
%%$curso;
$curso->save(); %%Guarda el registro en la base de datos / Cuando guarda el objeto revisa si tiene la propiedad id, si la tiene actualiza, si no, la crea.
```

Si se quisiera que el la convención no fuera en cursos, se puede agregar dentro del archivo generado, en la clase curso lo siguiente:

```php
<?php

namespace App\Models;

use Illuminate\Database\Eloquent\Factories\HasFactory;
use Illuminate\Database\Eloquent\Model;

class Curso extends Model
{
    use HasFactory;
    protected $table = "users";
}

```

pero normalmente se usan convenciones.



#### Llenar tablas con datos de prueba.

Generados por los **factory** y **seeder**. 

Para efectos de esta práctica, solo se ha dejado dentro de migraciones el archivo de cursos y los que estaban por defecto.

Dentro de <u>database</u>:open_file_folder: / <u>seeders</u>:open_file_folder: /DatabaseSeeder.php :bookmark_tabs: agregar código como en tinker:

```php
$curso=new Curso();
$curso->name = "Laravel";
$curso->descripcion = "El mejor framework de PHP";
$curso->categoria="Desarrollo web";

$curso->save(); 
```

luego ejecutar `php artisan migrate:fresh`

`php artisan db:seed` rellena con datos dentro de lo que se definió en el seeder.

PERO :twisted_rightwards_arrows:

`php artisan make:seeder CursoSeeder`

se crea nuevo archivo, se pasa los datos escritos antes. Sin embargo, solo se lee el DatabaseSeeder.

Para cambiarlo se puede usar call:

```php
<?php

namespace Database\Seeders;

    
use Illuminate\Database\Console\Seeds\WithoutModelEvents;
use Illuminate\Database\Seeder;

class DatabaseSeeder extends Seeder
{
    /**
     * Seed the application's database.
     *
     * @return void
     */
    public function run()
    { 
        $this->call(CursoSeeder::class);
    }
}
```

con el simple comando de `php artisan migrate:fresh --seed` se realizan los dos pasos en uno.



#### Factorys

Realizan los datos de llenado.

`php artisan make:factory CursoFactory` crea dentro de <u>database</u>:open_file_folder: / <u>factory</u>:open_file_folder: / CursoFactory :bookmark_tabs: 

Cambiar los nombres de 'Model' por el nombre a trabajar: 'Curso'. Esto se pone manualmente.

De lo contrario se agrega `php artisan make:factory CursoFactory --model=Curso`



```php
<?php

namespace Database\Factories;

use Illuminate\Database\Eloquent\Factories\Factory;
/**use \App\Models\Curso;

 * @extends \Illuminate\Database\Eloquent\Factories\Factory<\App\Models\Curso>
 */
class CursoFactory extends Factory
{
    /**
     * Define the model's default state.
     *
     * @return array<string, mixed>
     */
    public function definition()
    {
        return [
            //se definen todos los campos de la tabla. Se van a asignar con lo siguiente:
            'name' =>$this->faker->sentence(),
            'descripcion' =>$this->faker->paragraph(),
            'categoria' =>$this->faker->randomElement(['Desarrollo web', 'Diseño web'])
        ];
    }
}


```

 y dentro del seeder

```php
<?php

namespace Database\Seeders;

use Illuminate\Database\Console\Seeds\WithoutModelEvents;
use Illuminate\Database\Seeder;
use App\Models\Curso;

class CursoSeeder extends Seeder
{
    /**
     * Run the database seeds.
     *
     * @return void
     */
    public function run()
    {
        //
       Curso::factory(50)->create();
    }
}

```

se refresca la migración.

Dado que esto que en el seeder solo hay una línea de código actualmente, se puede **eliminar** y agregarlo al DatabaseSeeder.



#### Generador de consultas eloquent
