# Apuntes día 13 de octubre

## Crear un repositorio

1. _mkdir_ directorio
    * touch README.md
    * toto.c

2. _git init_: Crea el .git en directorio
3. _git add ._: añade el README.md y todo.c al seguimiento

Al compilar obtenemos a.out y no queremos que el ejecutable de toto.c esté bajo control de versiones. Por lo que creamos un fichero _.gitignore_ y en el escribimos que cualquier fichero `*.out` no sea trackeado.

Si hacemos un _git add ._ solo mete el _.gitignore_ y no el _a.out_, cuando accedemos al estatus README y toto están listos para hacer un commit.

```GIT
git commit .m "commit inicial"
git log --graph --decorate -all
```
