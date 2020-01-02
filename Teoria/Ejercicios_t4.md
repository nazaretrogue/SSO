# Tema 4: _Hacking_ ético y análisis forense

## Ejercicio 1
**Indicar las etapas que se siguen en un análisis de penetración, explicando qué objetivo se persigue en cada una de
ellas e indicando alguna herramienta que se puede usar.**

Las fases del _pentesting_ son:

* Contrato con el cliente que quiere realizar las pruebas: se crea un contrato con el cliente y se incluye un acuerdo de confidencialidad, en el que se firma no revelar información privada del sistema o empresa.
* Crear un equipo de _hacking_: se elegirán miembros de la empresa contratada para llevar a cabo el análisis de penetración y se planificarán las pruebas que se llevarán a cabo según el tipo de análisis que la empresa cliente quiera.
* Se realizan los tests: el equipo de _hacking_ actuará como un atacante para mostrar vulnerabilidades en el sistema. Para ello, seguirán los siguientes pasos:
    - Reconocimiento del sistema. Se pueden utilizar herramientas como ```maltego``` para representar las relaciones presentes en el sistema, o ```nmap``` para el reconocimiento de la red.
    - Escaneo para ver las vulnerabilidades. Se utilizan escáneres de puertos para saber los servicios activos y escáneres de vulnerabilidades para encontrar una grieta por la que infiltrasrse. Se utilizan herramientas como ```openVAS``` para analizar la vulnerabilidades.
    - Ganar el acceso al sistema. Se intenta entrar al sistema co nla información recogida durante el escaneo. Algunas herramientas de las que se pueden usar son ```hydra-gtk``` o ```John the ripper``` para llevar a cabo ataques de contraseñas, ```armitage```, que es una herramienta gráfica que recomienda métodos de ataque para un sistema, o herramientas como ```dnschef``` o ```ettercap``` que están preraparas para llevar a cabo un _network spoofing_.
* Analizar los resultados y realizar un informe: los datos recopilados durante la fase anterior se utilizarán para generar un informe.
* Entregar el informe al cliente: es la forma de tener feedback. El cliente decidirá entonces las medidas que tomará en consecuencia del informe entregado.

De forma general durante el análisis se pueden utilizar distribuciones de SOs con herramientas preparadas para estos análisis, como Kali Linux, Pentoo, BlackArch o Santoku (para móviles).

## Ejercicio 2
**Suponga que actuamos de perito forense en el registro de un sospechoso y encontramos una red local con 2 ordenadores
(ambos apagados), un _router_ y un equipo NAS (Network Access Server) encendido, ¿qué pasos deberamos seguir en las fases
de recopilación y preservación de evidencias?**

Los pasos a seguir serían:

1. Tomar fotografías del sitio y los distintos elementos sin tocar nada.
2. Utilizando guantes de látex que protegan los dispositivos, hacer una copia in situ del disco de cada ordenador utilizando un bloqueador para evitar escribir en el disco. Es decir, sacar imágenes forenses de los discos.
3. Hacer una copia de los logs del _router_ y un volcado de memoria de este. No apagar el _router_.
4. Hacer una copia in situ del servidor de acceso para estudiar los accesos a la red a posteriori. No apagar el servidor.
5. Para transportar los dispositivos al laboratorio sería una buena idea meterlos en jaulas de Faraday, que evitaran que recibieran más información en forma de ondas que anularían el artefacto.
6. Hay que comenzar una cadena de custodia que indique la fecha, hora, quién ha recogido los dispositivos y qué ha hecho con ellos para llevar un registro de todo y evitar que se puedan anular los elementos recogidos y saber en qué estado y dónde están en todo momento.

## Ejercicio 3
**Indicar cuáles son las fases del modelo de proceso de una pericial informática y cuáles son los elementos más 
importantes a tener en cuenta en cada una de ellas, en especial los relativos a mantener intactas las propiedades de
las evidencias.**

El proceso de peritaje sigue las fases siguientes:

1. Generación del encargo. Se nombra al perito responsable del caso y se establece el presupuesto. Se inicia cuando alguien realiza el encargo y finaliza con la aceptación del perito.
2. Actuación y generación de un informe. Se lleva a cabo todo el análisis de los dispositivos y se genera el informe sobre lo investigado. Se toman imágenes forenses de los dispositivos para su análisis y así evitar invalidar las pruebas recopiladas. Además, se lleva a cabo un registro cronológico, una cadena de custodia, de los elementos, que incluye quién es el responsable en cada momento de los dispositivos, la fecha de entrega y recepción y qué operaciones ha llevado a cabo sobre ellos. A partir de una hipótesis y con ayuda de la información recabada se intentará descubrir si la hipótesis es válida o no.
3. Entrega del informe y emisión. El informe contendrá fotos y/o vídeos del escenario y las pruebas tecnológicas además de la cadena de custodia. Es importante que contenga un título para identificarlo fácilmente, el documento donde se incluye el objeto del informe, antecedentes, referencias, el análisis..., cada página debe estar identificada con una cabecera (perito, expediente y título del informe) y pie de página (número de página, fichero, peticionario, firma, sello y fecha). Por último, y de manera opcional, puede tener un cuarto elemento, un visado.
4. Proceso judicial. El Tribunal puede citar al perito a discutir el informe antes de la declaración y ratificación de este.
5. Análisis posterior al cierre del caso y lecciones aprendidas. Se lleva a cabo un análisis económico (gastos reales - gastos presupuestados), un análisis de ejecución (qué se ha aprendido del caso para futuros encargos) y un análisis de satisfacción del cliente.

## Ejercicio 4
**Comentar brevemente las normas fundamentales que debemos seguir en informática forense.**



## Ejercicio 5
**En informática forense, cuáles son los objetivos o fases del proceso que debemos seguir.**

Las fases de un proceso de forense digital son las siguientes, aunque no tienen que ser secuenciales:

* Identificación del incidente. Se informa al responsable de la investigación detalladamente todo lo que ha ocurrido, las consecuencias, la escena del delito..., para poder tomar una decisión respecto a la actuación que se debe llevar a cabo. Se lleva a cabo la identificación de los bienes informáticos implicados, su uso dentro de la red, el inicio de la cadena de custodia y la revisión del entorno legal de los bienes.
* Recopilación de evidencias. Se recopilan las evidencias, idealmente no perdiendo ninguna. Para ello, no se deben apagar los equipos, debe identificarse cada uno, hay que documentar el proceso y precintar y proteger los elementos para su transporte...
* Preservación de evidencias. Para evitar la corrupción de las evidencias recogidas, se utilizan imágenes forenses que eviten la modificación de los dispositivos originales. Adems se utilizan la cadena de custidia comenzada en la primera fase citada, donde se lleva un registro cronológico de la manipulación de cada elemento del caso durante el desarrollo de este. La cadena de custoria incluye los nombres de las personas que tienen los elementos en su poder y las fechas de entrega y recepción.
* Análisis de evidencias. Con los elementos recogidos se analizan y extraen conclusiones. Se parte de una hipótesis y el responsable de la investigación debe descubrir los artefactos que validen o no dicha hipótesis. El responsable debe ser cuidadoso con las pruebas puesto que estas pueden sufrir manipulaciones que anulen los artefactos. Los análisis pueden ser de distintos tipos:
        - Análisis temporal: que incluyen la cronología de los eventos, metadatos y logs.
        - Análisis de datos ocultos: incluye la reconstrucción de datos ocultos (que tiene la extensión cambiada, han sido borrados, cifrados...).
        - Análisis de archivos y aplicaciones: incluye el examen de sus contenidos, versiones y tipos, relaciones entre archivos...
* Documentación y resultados. Se genera un informe que incluye los resultados que se han encontrado durante el proceso. El documento debe ser metódico, detallado y patente desde el inicio del análisis, debe responder a las preguntas que se han formulado al principio o a lo largo del proceso y debe tener una estructura. En él se detallan las conclusiones obtenidas de manera objetiva, sin incluir juicios del valor del responable del análisis.
