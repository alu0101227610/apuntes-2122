# Apuntes día 11 de octubre

## Raminificaciones en git

* Guarda copias completas de cada versión (no solo diferencias)
* Tiene un código en cada archivo para controlar la integridad
* Cuenta con un árbol que nos permite acceder a las distintas versiones
* Cuenta con un código de los commits realizados (Se relacionan con sus commit padres).

La cabeza(head) en las ramas apunta a generalmente a la rama master. Para crear una rama escribimos `git branch "name"`.

Para ver las ramas que tengo `git branch` o `git branch -v` para tener información más detallada.

Con `git checkout "nombre"` decimos en que rama se guardan los cambios.

Para verificar las modificaciones de dos ramas, creamos una nueva rama común, añadimos la modificación y hacemos commit.

la forma de una fusión rápida de ramas se hace con `git merge "rama_fusión"`.

Para borrar una rama `git branch -d "rama"`.

Para fusionar ramas bifurcadas se usan los nodos extremos de ambas ramas y su ancestro común.

En ocasiones hay ramas que modifican el mismo fichero y en ese caso se debe elegir la versión de la rama que queremos que prevalezca.

Una vez resuelta la diferencia hacemos add, commit y push.

Para ver las ramas y su estado podemos hacer un: `git log --oneline --graph` para verlo de forma limpia.

