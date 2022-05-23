CREATE TABLE specialization(id INTEGER PRIMARY KEY, description VARCHAR(50) NOT NULL, id_doctor INTEGER NOT NULL,  foreign key (id_doctor) references doctor(id));
CREATE TABLE doctor(id INTEGER PRIMARY KEY, firstname VARCHAR(30) NOT NULL, lastname VARCHAR(50) NOT NULL);
 CREATE TABLE patient(id INTEGER PRIMARY KEY, firstname VARCHAR(30) NOT NULL, lastname VARCHAR(50) NOT NULL, nss VARCHAR(11) NOT NULL);
 CREATE TABLE diagnose(code INTEGER PRIMARY KEY, details VARCHAR(90) NOT NULL, id_patient INTEGER NOT NULL, foreign key (id_patient) references patient (id));

CREATE TABLE doctorpatient (
ide INTEGER PRIMARY KEY, 
id_doctor INTEGER NOT NULL,
id_patient INTEGER NOT NULL, 
FOREIGN KEY (id_doctor) references doctor(id), 
FOREIGN KEY (id_patient) references patient(id) );

INSERT INTO specialization VALUES (1, 'cardiologia',3);
INSERT INTO specialization VALUES (2, 'otorrino',3);
INSERT INTO specialization VALUES (3, 'urgencias',2);
INSERT INTO specialization VALUES (4, 'neurologia',1);

INSERT INTO doctor VALUES (1, 'jaime', 'perez');
INSERT INTO doctor VALUES (2, 'rosalba', 'quintero');
INSERT INTO doctor VALUES (3, 'noe', 'nostradamos');

INSERT INTO patient VALUES (1, 'jorge', 'higareda','12345678901');
INSERT INTO patient VALUES (2, 'rosa', 'canales','12345678902');
INSERT INTO patient VALUES (3, 'silvestre', 'estalon','12345678903');
INSERT INTO patient VALUES (4, 'paola', 'quintero','12345678904');
INSERT INTO patient VALUES (5, 'pablo', 'bolt','12345678905');

INSERT INTO diagnose VALUES (3, 'esclerosis multiple', 1);
INSERT INTO diagnose VALUES (1, 'tiroides tiroideo', 2);
INSERT INTO diagnose VALUES (2, 'pomulos inflados', 3);
INSERT INTO diagnose VALUES (4, 'laringitis severa', 4);
INSERT INTO diagnose VALUES (5, 'tumor cerebral', 5);
INSERT INTO diagnose VALUES (6, 'sidrome del crazon roto', 1);
INSERT INTO diagnose VALUES (7, 'parasitos', 2);

INSERT INTO doctorpatient VALUES (1,1,1 );
INSERT INTO doctorpatient VALUES (2,2,2 );
INSERT INTO doctorpatient VALUES (3,3,3 );
INSERT INTO doctorpatient VALUES (4,1,4 );
INSERT INTO doctorpatient VALUES (5,2,5 );


ALTER TABLE specialization ADD id_doctor INTEGER;
ALTER TABLE specialization ADD FOREIGN KEY (id_doctor) REFERENCES doctor(id);

specialization

![7475491c4ba95deca2341f07eecd6c4d.png](7475491c4ba95deca2341f07eecd6c4d.png)
![655301bf3c7efb792fcc73294affc3ef.png](655301bf3c7efb792fcc73294affc3ef.png)
![6bf74f952300eeba270b9e7460d253cd.png](6bf74f952300eeba270b9e7460d253cd.png)
![0b9f6c2acb66d2c3898065b595f95221.png](Imagenes\0b9f6c2acb66d2c3898065b595f95221.png)
![be2aed98eb9bb5832d772927127d58fc.png](Imagenes\be2aed98eb9bb5832d772927127d58fc.png)


Respaldos consistentes en frío:

Archivos a respaldar

SELECT NAME FROM V$DATAFILE

--------------—
LAPTOP-0CJA73SE

----------------------11/10/21
respaldos logicos
respaldo y recuperación
exportar a un usuario especifico mjose1
``
/exp -help
 /   exp sjose (entrar con usuario con permisos en toda db)  exp system
/(tamaño de bufer) solo ENTER
/(en qué directorio) mjose1_respaldo.dmp
/2 (usuario especifico)
/(exporta permisos) sy O ENTER
/(exporta tabla, limpia tablas) ENTER
/(comprime extend bloques adicionales creciendo con dbf, fragmentacion de objetos, exportación genera un extend donde quepa todo objeto) ENTER
/(formato, set de caracteres, )    MJOSE1
[MJOSE2]
ENTER

dir
imp -help
//
``
que importe de un usuario a otro.
FROM USER 
TO USER

**********************
mcesar1   1234
mpatricia1    1234
*************
25/10/21

interbloqueo, toma de registros para actualizar sin realizar commit 

cuando se realiza actualizacion por parte de dos consolas, entra en espera hasta que se realice commit? la primera consola que actualiza los datos.
**Interbloqueo/deadlock**/punto muerto/impasse/
*GENERAR INTERBLOQUEO* tarea
Generar erro de *interbloqueo detectado*
**BLOQUEO ORACLE**
-Todo es secuencial (diferencia de segundos o menos)
-Se generan filas

-https://docs.oracle.com/cd/B19306_01/server.102/b14220/consist.htm#i5704

https://docs.oracle.com/cd/B19306_01/server.102/b14237/dynviews_1147.htm#REFRN30121

http://www.dba-oracle.com/t_find_oracle_locked_objects.htm


**-------------------------------**

Las bases de datos distribuidas ofrecen algunas ventajas  sobre bases de datos centralizadas. Una base de datos distribuida, como su nombre lo indica, se distribuye a través de una matriz de servidores en varias ubicaciones. Es una colección de múltiples bases de datos interconectadas, que se extienden físicamente a través de varias ubicaciones que se comunican a través de una red informática.
Un sistema de administración de bases de datos distribuidas es un sistema de software centralizado que administra una base de datos distribuida de una manera como si estuviera almacenada en una sola ubicación.
* Se usa para crear, recuperar, actualizar y eliminar bases de datos distribuidas.
* Sincroniza la base de datos periódicamente y proporciona mecanismos de acceso en virtud de los cuales la distribución se vuelve transparente para los usuarios.
* Asegura que los datos modificados en cualquier sitio se actualicen universalmente.
* Se utiliza en áreas de aplicación donde numerosos usuarios procesan y acceden grandes volúmenes de datos simultáneamente.
* Está diseñado para plataformas de bases de datos heterogéneas.
* Mantiene la confidencialidad y la integridad de los datos de las bases de datos.
