# Tema 3: Desarrollo de sistemas seguros

## Ejercicio 1
**Indicar 4 formas de propagación/infección de _malware_ y cómo podemos prevenirlas.**

* _Malware_ empaquetado junto a otro programa que se instala cuando se instala el programa original: para prevenir esto es necesario descargar programas de fuentes confiables y comprobar los hash de los fuentes si disponemos de ellos.
* Archivos adjuntos en e-mails que son ejecutables dañinos: debemos educarnos en el phising y el spam y no abrir, guardar o ejecutar contenido que provenga de remitentes desconocidos.
* Uso de hiperenlaces acortados que nos llevan realmente a un _malware_: debemos tener cuidado con los sitios a los que accedemos y ser siempre conscientes del peligro que suponen páginas no seguras y desconocidas.
* Vulnerabilidades del software que tienen agujeros de seguridad como el buffer overflow.

En general, las contramedidas idóneas serían no dejar pasar el _malware_ a nuestro sistema o bloquear la capacidad de que se modifiquen cosas en él. Entre las contramedidas destacan:

* Utilizar una política de seguridad que prevenga el _malware_ en nuestro sistema.
* Concienciar y educar a la población para evitar la ingeniería social.
* Reducir o eliminar las vulnerabilidades del software.
* Fortalecer el sistema para reducir amenazas.

## Ejercicio 2
**Explicar brevemente qué defensas se suelen utilizar para prevenir/mitigar un ataque de desbordamiento de búfer.**

## Ejercicio 3
**¿Qué es un _malware_ sin archivo (_fileless malware_) y cómo puede funcionar?**

Los _fileless malware_ son un tipo de _malware_ que no reside en disco por lo que no infecta archivos, sino que se encuentra en memoria 
y de esta forma evita que un antivirus lo detecte. Los antivirus detectan el _malware_ a través de firmas o trazas en archivos, pero si 
no hay archivos infectados el antivirus es incapaz de encontrar nada puesto que el _fileless malware_ no deja huella.

Este tipo de _malware_ se ejecuta en memoria mientras los programas reales están corriendo y realizando su función; el _malware_ 
mientras tanto se está ejecutando en segundo plano y llevando a cabo el ataque.

## Ejercicio 4
**Explicar qué es un _shellcode_ y cómo funciona.**

## Ejercicio 5
**¿Qué es un IDS (_Intrusion Detection System_)? Su uso en conjunción con un _firewall_ es ¿incompatible o complementario?
Justifícalo.**

Un IDS es un proceso o dispositivo que analiza el tráfico del sistema y la red para detectar los accesos no autorizados al sistema.
Utilizarlo con un _firewall_ es complementario, ya que el _firewall_ frenará la entrada de tráfico que no deseemos que entre a nuestro sistema, y el IDS comprobará el que sí hemos permitido que entre para verificar que es tráfico deseado y no una intrusión.

Hay dos tipos:

* HIDS (Host IDS): analizan distintas partes de un host para detectar intrusiones (SO, aplicaciones y hardware). Analizan registros de archivos y los comparan con una base de datos que contiene las peculiaridades de ataques conocidos.
* NIDS (Network IDS): analizan los paquetes de red en buscas de eventos, y son notificados al administrador. Detectan ataques mediante paqutes no válidos que violan algún protocolo o mediante el reconocimiento de firmas o del propio ataque que se está llevando a cabo.

## Ejercicio 6
**Indicar las técnicas que suelen utilizar los antivirus para detectar _malware_.**

* Análisis estático: mediante herramientas e ingeniería inversa intentan reconstruir el código.
  - Basado en firmas: el escáner busca información sobre una base de datos de firmas de virus en busca de coincidencias. Se utiliza solo una pequeña parte de la identificación para no almacenar una gran cantidad en memoria (que además pueden ser usadas por el propio atacante). No sirve contra _malware_ desconocido del que no se tiene una firma almacenada con la que comparar.
  - Basado en heurísitcas: detectan nuevo _malware_ mediante análisis estático sin tener una firma que concuerde exactamente, buscando trozos de código sospechosos.
    + Archivos: analizan contenido, propósito, ubicación... del archivo. Si contiene instrucciones de borrado o daño a otro archivo, es malicioso.
    + Pesos: cada aplicación tiene un peso según el daño que puede hacer. Si un programa sobrepasa un umbral con su peso, es malicioso.
    + Reglas: se extraen reglas del programa y se compara con otras previas. Si hay algo sospechoso, es malicioso.
    + Genérico: detecta variantes de _malware_ anterior encajando el programa concreto en alguna familia de _malware_.
* Análisis dinámico: ejecutan el _malware_ en un entorno aislado para analizar el comportamiento durante la ejecución. Se analizan llamadas al sistema, a procedimientos... Se buscan conductas extrañas como borrado de archivos, detección de teclas pulsadas, etc.
* Análisis híbrido: combina análisis estático y dinámico. Primero se buscan firmas y después se analiza el comportamiento.

## Ejercicio 7
**¿Qué es la rotura de pila (_stack smashing_) y cómo puede utilizarse para atacar un sistema?**

## Ejercicio 8
**Indicar las contramedidas que podemos tomar para mitigar las amenazas de nuestro sistema, comentando brevemente qué
hacen o qué beneficios tienen cada una de ellas.**

## Ejercicio 9
**Comentar brevemente los pasos básicos para endurecer (_hardening_) un sistema operativo.**
