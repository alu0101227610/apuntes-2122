# Apuntes día 27 de octubre

1. Crear _.gitignore_ (.*~)

      ```bash
      git commit "creación de gitignore"
      ```

2. Crear README.md

      ```bash
      git commit "Creando el README.md"
      ```

3. Crear fichero de respuestas

      ```bash
      git commit "Creando el fichero de respuesta"
      ```

4. Git push
5. Creación de la rama doc
    * git branch doc
    * git checkout doc
    * git lola

A continuación hay que meter el grafo de git en un fichero sin solapar lo anterior.

`git log --graph --all --date-relative >> respuestas.txt`

6. git commit

      ```bash
      git commit "Grafo en la rama doc"
      ```

7. git checkout main
    * Añadir _helloworld.rb `"puts "hello""`

      ```bash
      git commit "Creando hola mundo en ruby"
      ```

8. git checkout doc y añado el git log en respuestas de nuevo

      ```bash
      git commit "Grafo con hello world en Ruby añadido"
      ```

Ahora hay que reorganizar los cambios de doc y master:

```bash
git checkout docs
git rebase main
```

La fusión guarda los cambios pero no su orden, la reorganización si. Cuando haces una fusión te pones en main. Para un rebase te pones en la otra que no es main.

Hay que mover el main al final y usamos el merge.

```bash
git checkout main
git checkout merge
```

Pry es un intérprete interactivo que si lo usamos en código nos abre un intérprete interactivo durante la ejecución.

## Estructura de un Rakefile

Un Rakefile hace tarea como un Makefile pero para ejecición. Se puede llamar con Rake, Rake hello o Rake bye.

```Ruby
task :hello do
  sh "ruby helloworld.rb"
end
task :bye do
  sh "ruby byebye.rb"
end
task :default => hello
```

## Cambiamos el initialize de Point

```ruby
# variables locales
def initialize x, y
# variables de instancia
@x, @y =x,y
  #variable de clase
  if define? @@numero_puntos
    @@numero_puntos += 1
  else 
    @@numero_puntos = 1
  end
end
```

Las variables de clase son comaprtidas por todos los objetos del mismo tipo y de momento que no sabemos visibilidad, no accede a las clases hijas. En este caso guardamos el número de objetos (puntos creados).

```ruby
# método de clase
def self.contador
  @@numero_puntos
end
```

Self indica que se referencia a la propia clase.

Al terminal es importante haber hecho un commit con cada funcionalidad añadida.
