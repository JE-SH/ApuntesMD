**Cuando se habla de algún proceso normalmente se tiene una visualización de la acción que se realiza dentro de la computadora, sin  embargo, de una manera un poco externa, a nivel de sistema operativo, está presente una tabla llamada “tabla de procesos”.**
**https://sistemasoperativosunivia.wordpress.com/2014/12/08/interbloqueos/

Los procesos que se implementan en un sistema operativo se pueden clasificar según el grado en que comparten la memoria: pesados y ligeros.

Los procesos pesados (proceso Unix) no comparten ninguna porción de la memoria, y cada proceso se ejecuta en su propio procesador virtual con CPU y memoria, sin embargo, todos los procesos sí comparten el mismo espacio de almacenamiento permanente (disco). Su costo de implementación en tiempo de CPU y memoria es mucho más elevado, además de requerir de una MMU (Unidad de Manejo de la Memoria) encargada de la traducción de direcciones virtuales a reales, pero su implementación sería demasiado costosa en tiempo de CPU, puesto que para garantizar una verdadera protección habría que recurrir a un intérprete del lenguaje de máquina. No obstante, garantiza una protección a los procesos en el mismo procesador, permitiendo a los demás procesos continuar sin problemas en caso de que uno fallara

Por otra parte, los procesos livianos o threads, comparten toda la memoria y el espacio de almacenamiento permanente. Existen extensiones que implementan procesos livianos para Unix. Por ejemplo,  el sistema que implementaba el sistema operativo de los computadores Commodore Amiga, que no tenía la MMU necesaria para implementar procesos pesados.

**

https://users.dcc.uchile.cl/~jpiquer/Docencia/SO/aps/node7.html#ref3proc

https://www.dc.fi.udc.es/~so-grado/2_PROCESOS.pdf
http://www.atc.uniovi.es/telematica/2ac/Apuntes-y-Ejercicios/T08-Procesos.pdf
https://www.fing.edu.uy/inco/cursos/sistoper/recursosTeoricos/5-SO-Teo-Procesos.pdf
https://www.dc.fi.udc.es/~so-grado/SO-Procesos.pdf

**

Alguna de esta información contenida se puede separar en:

* Información de identificación 
    

* Identificador del proceso. 
    
* Identificador del proceso padre en caso de existir relaciones padre-hijo (UNIX). 
    
* Información sobre el usuario (identificador del usuario, grupo) 
    

* Estado del procesador
    
* Información del control del proceso.
    

* Información de planificación y estado: 
    

* Estado del proceso 
    
* Evento por el que espera el proceso cuando está bloqueado.
    
* Prioridad del proceso. 
    
* Información de planificación.
    

* Descripción de los segmentos de memoria asignados al proceso. 
    

* Puntero al segmento de datos. 
    
* Puntero al segmento de código. 
    
* Puntero al segmento de pila. 
    

* Recursos asignados
    

* Archivos abiertos (tabla de descriptores o manejadores de archivo). 
    
* Puertos de comunicación asignados.
    

* Punteros para estructurar los procesos en colas o anillos.
    
* Comunicación entre procesos. El BCP puede contener espacio para almacenar las señales y para algún mensaje enviado al proceso.
    

  
**

*6.4 DETECCIÓN Y RECUPERACIÓN DE UN INTERBLOQUEO 442-448 (6 pag)
-6.7 OTRAS CUESTIONES 457-461 (4 pag)







                            rafa

**peter                         _6.1 Recursos 434-437 (3 pag)**
peter  _6.8 INVESTIGACIÓN SOBRE LOS INTERBLOQUEOS 461 (1/2 pag)
peter   _6.9 RESUMEN 461 (1/2 pag)

prisila        +6.3 Algoritmo de la avestruz 441 (1 pag)
**prisilia                       +6.6 CÓMO PREVENIR INTERBLOQUEOS 454-457 (3 pag)**

uriel      -6.2 Introducción a los interbloqueos 437-441 (4 pag)

jose       *6.4 DETECCIÓN Y RECUPERACIÓN DE UN INTERBLOQUEO 442-448 (6 pag)

chema    /6.5 CÓMO EVITAR INTERBLOQUEOS 448-454 (6 pag)

rafa       -6.7 OTRAS CUESTIONES 457-461 (4 pag)



**

Se crea una lista ‘L’.

El orden de procesamiento de datos es arbitrario. 

Iniciamos con R y L vacia.

Agregamos R a la lista y se avanza a los posibles nodos, en este caso A.

L= \[RA\]

De A se pasa a S.

L=\[RAS\]

****

Ya que S no tiene arcos salientes nos obliga a regresar a A.

A ya no tiene más arcos, regresamos a R, que ya no tiene más arcos.

  
**
Amenaza 
interrupcion
interceptacion
modificacion
invencion

elementos sist comp
hardware

**********************03/12/21*******************


ejecución interpretada
un intérprete subyacente ejecutaba las “instrucciones
de hardware” en el software


La BIOS (Sistema básico de entradas y salidas) es un componente esencial que se usa para controlar el hardware. Es un pequeño programa, que se carga en la ROM y realiza funciones funciones a muy bajo nivel en el PC, como la secuencia de arranque, o cómo hacer funcionar el teclado.

Un recurso puede poseer varios puntos de entrada, que son la cantidad de procesos que pueden utilizar simultáneamente el mismo, pero si un recurso tiene sólo un punto de entrada, se lo denomina recurso crítico o recurso no compartible.