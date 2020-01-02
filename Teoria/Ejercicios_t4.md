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
2. Utilizando guantes de látex que protegan los artefactos, hacer una copia in situ del disco de cada ordenador utilizando un bloqueador para evitar escribir en el disco. Es decir, sacar imágenes forenses de los discos.
3. Hacer una copia de los logs del _router_ y un volcado de memoria de este. No apagar el _router_.
4. Hacer una copia in situ del servidor de acceso para estudiar los accesos a la red a posteriori. No apagar el servidor.
5. Para transportar los dispositivos al laboratorio sería una buena idea meterlos en jaulas de Faraday, que evitaran que recibieran más información en forma de ondas que anularían el artefacto.
6. Hay que comenzar una cadena de custodia que indique la fecha, hora, quién ha recogido los dispositivos y qué ha hecho con ellos para llevar un registro de todo y evitar que se puedan anular los artefactos recogidos y saber en qué estado y dónde están en todo momento.

## Ejercicio 3
**Indicar cuáles son las fases del modelo de proceso de una pericial informática y cuáles son los elementos más 
importantes a tener en cuenta en cada una de ellas, en especial los relativos a mantener intactas las propiedades de
las evidencias.**



## Ejercicio 4
**Comentar brevemente las normas fundamentales que debemos seguir en informática forense.**



## Ejercicio 5
**En informática forense, cuáles son los objetivos o fases del proceso que debemos seguir.**


