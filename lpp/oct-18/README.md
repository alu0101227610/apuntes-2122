# Apuntes día 18 de octubre de 2021

_git branch -vv_: muestra los camvios respecto a la versión en la nube y cuantas versiones han avanzado en el servidor

Si no fusionamos previamente local a la nube no podemos hacer un push. Cuando hacemos el merge, editamos los contenidos y realizamos el push normalmente.

`git push origin --delete "rama"`

Este comando borra la rama del servidor y no la borra local.

`git branch -d "rama`

Si la rama tiene camvios nos avisara para hacer un merge previo. Si queremos borrar aunque hayan estos cambios cambiamos a -D.
