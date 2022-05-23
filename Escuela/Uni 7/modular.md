aspectos biológicos. Entrenar.
clasificación de proteínas de veneno en animales. 
Correr el algoritmo, mejorar forma de predicción (+ características) e interfaz.
Venómica. Utilidad farmacéutica.
sustancias importantes biotecnológicamente.
Proteínas- info genética 
se toma secuencia y se analizan las partes  
veneno sustancia a partir de genetica. toman secuencia genetica y analiza partes.Contiene fragmentos que permiten dobleces – digiere, entume, descritas a partir de fragmentos de la longitud de la proteína. Bases de datos con info, experimental o reportadas 
secuencia de caracteres, analizan secuencias d
sustancia venen?
enfoques lineales, modelos de markov(estadisticos).
lab humedo
lab incílico
**red recurrente**. (RNN)
**Tensor Flow**
 BD  Blast (etapa previa).
 Búsqueda por organismo o tipo proteína
 longitud aminoácidos->bases nucle…
 apartados con roles
 secuencias
 fasta formato de genoma
     identificador desde >
     secuencia de aminoacidos ->elementos para que aprenda

 tomar fragmento 

 <300 aminoácidos
 proteína
 trabajarlo a travéz de transcriptoma
 info genética-leer material genético y lo que la proteína debe producir.
 lo que se produce en cierto momento

 https://www.ncbi.nlm.nih.gov/pmc/articles/PMC6601600/

 https://www.uniprot.org/uniprot/?query=annotation%20type%20tissue%20specificity%20venom&sort=score

 https://webs.iiitd.edu.in/raghava/toxinpred/prot_submitfreq_S.php?ran=65043
 https://web.archive.org/web/20181229161345/http://bioserv7.bioinfo.pbf.hr:80/ToxClassifier/

 (https://github.com/rgacesa/ToxClassifier

 patrones.
 */
  **entender como se organiza la información genética** 
  */
 **Clasificador de redes para transcriptomas de animales venenosos.**

 *diagrama de flujo
 datos
 implementación del modelo
 implementar 
 revisar datos*

 DIAGRAMA DE TRELLO
 ///////////////////////////////////////////////////////////////////
 jupiterlab 
 sci gitlearn
 carolina elizabeth gomez marquez
 ///////////////////////////////////////////////////////////////////
ayuda para … enfocado a alumnos?
estudiantes par la licensiatura en…
hipótesis lo que se quiere coprobar.

cloud computing

División de Tecnologías para la Integración Ciber-Humana
OpenMP
///////////////////////////////////////////////////////////////////
**Documentos**

* Texto artículo descargado http://inventio.uaem.mx/index.php/inventio/article/view/496
* https://www.hsnstore.com/blog/nutricion/proteinas/sintesis/transcripcion/
* https://www.genome.gov/es/genetics-glossary/Transcripcion
* https://dobetter.esade.edu/es/machine-learning-regulacion
* https://www-cabi-org.wdg.biblio.udg.mx:8443/cabebooks/ebook/20210517786
* https://www.cyted.org/sites/default/files/2016_libro_biotox_para_impresion_26_06_2016_con_portada.pdf
* https://www.researchgate.net/publication/320409501_VENOMICA_Y_ANTIVENOMICA_HERRAMIENTAS_PROTEOMICAS_PARA_HACER_FRENTE_A_LA_PATOLOGIA_DESATENDIDA_DEL_ENVENENAMIENTO_OFIDICO
* https://www.zaragoza.unam.mx/wp-content/Portal2015/publicaciones/libros/cbiologicas/libros/Toxico-ago18.pdf
* https://digital.csic.es/bitstream/10261/3777/1/Juarez.pdf

### Preguntas

* Para la creación de los medicamentos, qué se requiere analizar de las proteínas. - Cómo se crean los medicamentos a partir de la proteína.

* Para qué analizar proteínas/transcriptomas.

* Atchley factors.

* Cómo se estructura una proteína

* Cómo funciona uniprot

* Como se puede ver si es venenoso con info de uniprot

* Sabe si dentro de la secuencia o del archivo fasta se encuentra que es veneno?

### Objetivos

* Identificar venenos desde proteínas o transcriptomas.
* 

La molécula de ADN consiste en dos cadenas que se enrollan entre ellas para formar una estructura de doble hélice. Cada cadena tiene una parte central formada por azúcares y grupos fosfato. Enganchado a cada azúcar hay una de de las siguientes 4 bases: adenina (A), citosina (C), guanina (G), y timina (T).La secuencia de estas bases a lo largo de la cadena es lo que codifica las instrucciones para formar proteínas y moléculas de ARN, que constituye el primer paso del proceso de transcripción y síntesis de la proteína. La codificación de la secuencia del ADN a ARNm se lleva a cabo construyendo una copia complementaria de cada nucleótido

[Ciencias omicas unam](https://www.revista.unam.mx/vol.18/num7/art54/index.html)
[National Human Genome](https://www.genome.gov/es/genetics-glossary/ADN-acido-Desoxirribonucleico)
[Transcripción](https://www.hsnstore.com/blog/nutricion/proteinas/sintesis/transcripcion/)

///////////////////////////////////////////////////////
Para tomar datos hay liks como: https://www.uniprot.org/uniprot/Q9ULB1.fasta
terminación fasta

////////////////////////////////29/03/22
**

, seguida de un SeqID único (identificador de secuencia). El SeqID debe ser único para cada secuencia de nucleótidos y no debe contener espacios, además de tener 25 caracteres o menos, incluyendo sólo letras, números, líneas (- y _), comas, puntos, asteriscos y signos de numeral (#), aunque el personal de la base de datos reemplazará el identificador de secuencia con un número de acceso cuando se procese su envío (NCBI, 2021).

 ›SeqABCD

Después del SeqID sigue la información sobre el organismo fuente del que se obtuvo la secuencia en formato \[modifier=text\] sin espacios alrededor del "=". Como mínimo, se debe incluir el nombre científico del organismo. Se pueden agregar modificadores opcionales para proporcionar información adicional (para ver la lista completa de los modificadores de fuente disponibles y su formato ir a [<ins>https://www.ncbi.nlm.nih.gov/genbank/mods_fastadefline/</ins>](https://www.ncbi.nlm.nih.gov/genbank/mods_fastadefline/)).

 ›SeqABCD \[organism=Mus musculus\] \[strain=C57BL/6\]

 Para el caso de los archivos fasta de UniProt,

**
**DEV OPS**
CLOUD COMPUTING

///

https://pubmed.ncbi.nlm.nih.gov/

https://www.ncbi.nlm.nih.gov/

AA = aminoácido

veneno = sustancia. No todo es toxina. Conglomerado de cosas.

**A una entrada de secuencias es proteína asociada a algo venenoso?**

tkinter

clasificador proteina veneno

venprocator

class

*********

**Preguntas**

* Organización entidad-relación base datos

* Qué se hizo en el código de R para los no venenosos



Organizar trabajo:

* Organizar elementos a ver en el principio: swiss-prot, uniprot

* 
