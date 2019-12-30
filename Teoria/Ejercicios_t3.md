# Tema 3: Desarrollo de sistemas seguros

## Ejercicio 1
**Indicar 4 formas de propagación/infección de _malware_ y cómo podemos prevenirlas.**

El _malware_ se puede distribuir como:

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

Un ataque de desbordamiento de búfer se produce cuando la longitud de los datos introducidos supera la logintud del espacio que
el programador ha reservado. Esto puede provocar corrupción de datos, transferencia de control inesperada o violaciones de acceso a memoria.

Para prevenir el ataque, o mitigar sus efectos, se pueden imponer defensas en dos procedimientos:

* Defensa en tiempo de compilación. La idea es endurecer el programa (_hardening_) para que resista el ataque.
  - Utilizar extensiones y bibliotecas del lenguaje que sean seguras y eviten el desbordamiento.
  - Utilizar mecanimos para proteger la pila y detectar corrupciones de esta.
* Defensa en tiempo de ejecución. Detecta y aborta el ataque si se produce.
  - Proteger el espacio de direcciones con la unidad de gestión de memoria (MMU).
  - Generar accesos ilegales mediante la MMU si se acceden a páginas de memoria críticas.
  - Aleatorización del espacio de direcciones (ALSR) de forma que se desconozca la posición de los objetos como la pila, el heap o la sección de código del programa.

## Ejercicio 3
**¿Qué es un _malware_ sin archivo (_fileless malware_) y cómo puede funcionar?**

Los _fileless malware_ son un tipo de _malware_ que no reside en disco por lo que no infecta archivos, sino que se encuentra en memoria 
y de esta forma evita que un antivirus lo detecte. Los antivirus detectan el _malware_ a través de firmas o trazas en archivos, pero si 
no hay archivos infectados el antivirus es incapaz de encontrar nada puesto que el _fileless malware_ no deja huella.

Este tipo de _malware_ se ejecuta en memoria mientras los programas reales están corriendo y realizando su función; el _malware_ 
mientras tanto se está ejecutando en segundo plano y llevando a cabo el ataque para que se haya creado.

## Ejercicio 4
**Explicar qué es un _shellcode_ y cómo funciona.**

Cuando se produce un desbordamiento de búfer, lo que el atacante pretende es que se pase el control a un fragmento de código 
que él mismo ha colocado y que está almacenado en el búfer desbordado. Este fragmento de código se denomina _shellcode_ y
lo que hace por lo general es transferir el control a un shell que permitirá ejecutar cualquier programa con los mismos privilegios
que el programa que ha sufrido el desbordamiento.

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

La rotura de pila es una vulnerabilidad producida por la destrucción de la dirección de retorno en la pila. Cuando se genera un
ejecutable, las variables locales y la dirección de retorno se encuentran en un búfer común, establecido por la biblioteca que
estamos usando. Cuando las variables superan el tamaño de este búfer, se pisa la dirección de retorno y cuando el programa va a finalizar, provoca un error de segmentación, puesto que ya no hay dirección de retorno.

Normalmente se utiliza para provocar un desbordamiento de búfer (aunque hay otras formas de hacer esto, pero con la rotura de pila 
es lo más común), que indirectamente puede llevar a un ataque _shellcode_.

## Ejercicio 8
**Indicar las contramedidas que podemos tomar para mitigar las amenazas de nuestro sistema, comentando brevemente qué
hacen o qué beneficios tienen cada una de ellas.**

Podemos imponer las siguientes contramedidas:

* Política de seguridad que prevenga el _malware_: imponiendo una política con acciones permitidas y no permitidas nos aseguramos de que los empleados que trabajan como usuarios del sistema cumplan una serie de reglas para evitar la entrada de _malware_ externo al sistema.
* Concienciar y educar a los usuarios para evitar ingeniería social: muchos problemas surgen de la perdida de privacidad sobre contraseñas o claves, que facilitan los propios empleados a los atacantes (muchas veces sin ser conscientes de ello). Educando a los usuarios sobre la privacidad y los riesgos que supone la filtración de datos secretos, se ahorrarían muchos problemas de ataques a los sistemas y redes.
* Mitigar vulnerabilidades: utilizando técnicas de programación segura, usando bibliotecas del lenguaje seguras, mediante el uso de tests para detectar vulnerabilidades como el _fuzzing_, que consiste en inyectar una gran cantidad de datos aleatorios en un programa para ver si se producen fallos en él.
* Mitigar las amenazas: mediante el _hardening_ del propio sistema, debemos reducir la superficie de ataque. Para ello
  - debemos detectar (**detección**) qué ha producido la infección y localizarlo,
  - identificar (**identificación**) el _malware_ en cuestión para saber cómo actuar y
  - eliminar (**eliminación**) las trazas del _malware_ para que no siga propagándose por el sistema. En el caso de detectar el _malware_ pero no poder identificarlo y eliminarlo, es una buena práctica tener copias de seguridad para reponer los archivos dañados.

<!--## Ejercicio 9
**Comentar brevemente los pasos básicos para endurecer (_hardening_) un sistema operativo.**-->
