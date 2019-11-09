# Tema 1: introducción a la seguridad

## Ejercicio 1
**Indicar las fases de un APT (Advanced Persistent Threat) y qué se pretende en
cada una de ellas.**

1. Búsqueda de un sistema que atacar. Se basa en indagar hasta encontrar la máquina
o sistema al que se desea atacar.
2. Comprometer la red del sistema inicial. Se utilizan troyanos, gusanos, phising
o cualquier otro método para infectar la red a través de las personas que la usan.
3. Establecimiento de una puerta trasera para facilitar la entrada y salida del
sistema de la forma más discreta posible.
4. Escalada de privilegios. Se ganan poco a poco privilegios en el sistema para
poder llevar a cabo operaciones restringidas a ciertos tipos de usuarios.
5. Reconocimiento del sistema interno. Se investiga sobre los tipos de usuarios
que utilizan el sistema, los programas que hay instalados y en uso...
6. Traslado a otros equipos del sistema. Cuando se necesita más información y no
disponemos de ella en el equipo infectado nos desplazamos a otro para continuar
extrayendo información.
7. Mantenimiento de la posición en el sistema sin ser descubiertos mientras se
recaba la información y se llevan a cabo medidas para atacar el sistema.
8. Desempeño del ataque. Una vez recabada la información, se lleva a cabo el ataque:
filtración de datos, toma de control del sistema completo dejándolo inutilizado,
extorsión sobre usuarios del sistema...

## Ejercicio 2
**¿Qué es una política de seguridad y qué elementos debe tener para ser aplicable?**

Es un conjunto de normas y reglas de obligado cumplimiento para asegurar los
comportamientos aceptables y no aceptables en el trabajo. En el caso de no cumplirse
se pueden imponer medidas o sanciones; no obstante, a diferencia de una ley, se
la política se incumple, el no conocer la política es una defensa aceptable.

Para que la política sea aplicable de debe cumplir:
1. Diseminación: debe ser fácilmente accesible y estar disponible.
2. Revisión: debe poder leída por todos, por ejemplo, estando traducida a
varios idiomas.
3. Comprensión: se debe asegurar que los empleados entienden cada requisito de la
política, por ejemplo, sometiéndolos a evaluaciones.
4. Conformidad: los empleados deben aceptar cumplir la política, con un documento
firmado por ejemplo.
5. Aplicación uniforme: todos los empleados cumplen la misma política sin importar
el puesto o estatus dentro de ésta.

## Ejercicio 3
**Cómo podemos clasificar los ataques y cómo se relacionan con la triada CIA.**



## Ejercicio 4
**Comentar brevemente tres de las posibles contramedidas para protegernos de una
amenaza.**

Las contramedidas son actuaciones que se llevan a cabo para evitar o disminuir el
peligro que supone una vulnerabilidad. Entre las contramedidas, existen:

* **Controles físicos**: se utilizan medios físicos para frenar al atacante, como
guardas, cerrojos, búnkers...
* **Controles procedimentales**: usan órdenes o acuerdos para indicar la personal
como actuar en caso de amenaza (leyes, políticas, guías...)
* **Controles técnicos**: frenan los ataques con métodos relacionados con distintas
tecnologías: claves, cifrado, firewall...

## Ejercicio 5
**A qué denominamos TCB (Base de Computación Segura) y qué componentes de un
sistema informático lo forman.**

El TCB (*Trusted computer base*) es un conjunto de elementos hardware, firmware y
software que se encargan de asegurar el sistema mediante unos requisitos. Todo lo
que no forma parte del TBC es, por tanto, inseguro.
