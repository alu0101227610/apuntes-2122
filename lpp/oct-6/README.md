# Apuntes día 6 de octubre

## Git

Es un sistema automático de gestión de versiones distribuido.

* Instalar:

`sudo apt-get install git`

* Configurar:

```git
git config --list
git config --global user.name Antonella García
git config --global user.email alu0101227610@ull.edu.es
```

* Ejemplo de creación desde cero de un repositorio.
  1. Creamos una carpeta y un archivo a versionar.
  2. Empleamos el comando _git init_ para transformar el directorio en repositorio.

Para hacer una copia del directorio de trabajo al directiorio .git (donde se mantendra el control de versiones) empleamos:

`git add "fichero.extension"`

o para añadir todos los cambios de un directorio

`git add .`

Si configuramos en flobal se aplica en el gitconfig de /home, si configuramos en local afecta al /.git que hemos inicializado en el directorio de trabajo.

Para ver el estado de nuestro control de versiones usamos _git status_, pero aún no se ha subido nada, para hacer un guardado real en la rama en la estamos (main) y no dejarlo pendiente usamos:

`git commit -m "Primer commit"`

Si no se configura no dice los datos en los commit.

En conclusión, la forma de trabajar es:

1. Cambias los estados de los ficheros
2. Realizas un _git add_ de los ficheros modificados
3. Aplicas la confirmación con _git commit_

Utilizamos _git log_ para mostrar todos los commit realizados. Otra herramienta que utilizaremos es añadir mi repositorio local a un repositorio remoto, en github.com. Para eso hay que establecer un camino:

`git remote add nombre_rama URL`

Con el camino ya hecho, subiremos los datos al remoto con:

`git push nombre_rama main`

Para bajar el contenido de la nube en otra máquina ponemos:

`git clone URL`

Esto crea un camino al repositorio llamado origin, esto significa que para hacer nuevamente un push desde la maquina hacemos:

`git push origin main`

Con _git pull_ hacemos un _git fetch_ y un _git merge_ por lo que unimos la información del servidor con la de la rama local.