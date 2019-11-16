# Tema 2: seguridad en sistemas operativos

## Ejercicio 1
**Indicar las ventajas e inconvenientes de una autenticación multifactor (MFA).**

La autenticación multifactor se da cuando utilizamos dos o más medidas de autenticación.

Entre los pros están:
* Mayor seguridad, puesto que es más complicado conseguir las claves/contraseñas
o factores biométricos si hay varias capas.

Entre los contras encontramos:
* Necesidad de llevar un token encima como una tarjeta, un usb...
* Mayores costes al tener que implantar varias capas para la autenticación.
* Riesgos de perder o sufrir el robo del token.
* Mayor incomodidad para el usuario al tener que usar varios métodos de
autenticación.
* No se eliminan por completo los riesgos de sufrir un ataque.

## Ejercicio 2
**¿Qué elementos del fortalecimiento del sistema operativo son los más efectivos
a la hora de mitigar amenazas? Justifícalo.**

A la hora de fortalecer el sistema, hay que tener en cuenta que no es un proceso
estático, sino que va cambiando a medida que pasa el tiempo y se actualiza el
sistema, se añaden aplicaciones...

Los elementos a fortalecer son:

* **La distribución o kernel de nuestro sistema.** Cada vez que se actualiza o
instala una nueva distribución hay que asegurarse de que los fuentes descargados
son fiables, hay que comprobar la firma y monitorizar el compilado. También hay
que tener en cuenta la configuración preestablecida si es un binario precompilado.
* **Arranque del sistema.** El hecho de que el sistema pueda arrancarse de un
live CD, por ejemplo, supone un riesgo puesto que alguien con acceso físico al
sistema podría hacerlo y comprometer la seguridad. Hay que evitar que esto ocurra
protegiendo el boot de arranque, la BIOS y evitar que se pongan el funcionamiento
servicios que requieren de la red durante el arranque del sistema (como iptables).
* **Funcionamiento general del sistema  y aplicaciones.** Eliminar todas aquellas
funcionalidades y aplicaciones que no son necesarias o no usamos, restringir los
mecanismos de acceso y llevar a cabo actualizaciones periódicas, entre otras
medidas.

## Ejercicio 3
**En un sistema de control de acceso discrecional (DAC):**
**1. ¿Qué es una lista de control de acceso (ACL)? Dar un ejemplo en Linux.**
Es una estructura de datos que indica los permisos sobre cada objeto (columnas
de la tabla) respecto a cada usuario (filas). Es decir, sirve para restringir qué
permisos tiene cada usuario sobre un recurso del sistema. Por ejemplo, un archivo
tendrá una columna asociada en la tabla, y cada celda de dicha columna corresponde
al permiso que tiene un usuario: de lectura, de escritura, de propiedad...

**2. ¿Qué es una capacidad? Dar un ejemplo en Linux.**
Es una estructura de datos al igual que las ACL, pero en este caso la lista está
ligada al objeto e indica los permisos que tiene cada usuario sobre dicho archivo.
Por ejemplo, cuando tenemos un archivo abierto, hay una tabla de descriptores de
archivos que apunta a la tabla de ficheros abiertos. Eso es una capacidad que
está implementada en Linux, puesto que, por lo general, se utilizan ACL en lugar
de capacidades (excepto casos concretos como este).

**3. ¿Qué ventajas/inconvenientes tiene cada método desde el punto de vista de
implementación y uso?**

En general, las ACL son más utilizadas que las capacidades debido a que son más
sencillas de implementar y utilizar. Usando capacidades es más complicado revocar
los permisos, ya que habría que recorrer a cada usuario en búsqueda de los permisos
de un objeto concreto para poder quitarlos; eso supone un coste computacional
relativamente alto. Además, las ACL consumen menos tiempo, ya que en sistemas
Unix se redujeron los tipos de usuarios a tres: propietario, grupo y otros.

## Ejercicio 4
**1. ¿Cómo conviven en las actuales distribuciones de Linux el sistema DAC
tradicional con el sistema MAC añadido?**

Cuando se produce una llamada al sistema y hay tanto sistema DAC como MAC, el
procedimiento es similar al de DAC pero añadiendo la capa extra de MAC después de
hacer las comprobaciones con DAC. La llamada al sistema supone una búsqueda en
los inodos para buscar el objeto que contiene el procedimiento llamado. Tras esto,
se llevan a cabo las comprobaciones genéricas de errores, y tras ellas, los
chequeos con DAC. Si éstos son correctos, se pasaría a los hooks de LSM, y si estos
son correctos, se ejecutarían las comprobaciones de MAC.

Es decir, que ambos sistemas convivan juntos significa una capa extra de seguridad
donde garantizamos que la política de seguridad establecida en el sistema se
está cumpliendo.

**2. Comentar cómo se materializa alguna de las posibles implementaciones DAC
vistas.**

En los sistemas que implementan *Security Enhanced Linux* se implementa DAC. Cuando
un usuario solicita el acceso a un recurso, se lleva a cabo una comprobación DAC
en una primera instancia para comprobar si se continua con el proceso de acceso
al recurso o si por el contrario se deniega el acceso y la operación finaliza.

## Ejercicio 5
**Recordar múltiples claves es difícil. Sugiere un esquema mediante el cual una
persona pueda crear claves fáciles de recordar pero difíciles de adivinar para
diferentes casos o sitios.**

Un primer método para crear claves es utilizando la técnica de *persona, acción,
objeto*, de forma que se generen contraseñas relativamente largas, un poco
aleatorias pero que, al seguir una regla nemotécnica, son fáciles de recordar.

También se pueden generar las claves utilizando letras de canciones que puedan
gustar a la persona o frases de libros, generando una contraseña larga y que
también es fácil de recordar.

Estas dos reglas son un ejemplo de cómo pensar una clave que sea sencilla de
recordar pero difícil de averiguar para un atacante; no obstante, puede haber
muchas otras formas de generarlas sin tener que seguir ninguna de estas dos
reglas.
