# Apuntes día 20 de octubre

## Programación estructurada con Ruby

Lo primero es instalar ruby y rvm, rvm es un gestor de las posibles versiones de Ruby.

```bash
ruby -v
rvm -v 
rvm list known
rvm list
rvm use "version"
```

Para ejecutar un programa en ruby se puede hacer de las siguientes maneras:

```bash
ruby programa.rb
irb programa.rb
```

irb es un intérprete interactivo, muestra la ejecución paulatina de las líneas de código, si ejecutamos _irb_ se abrirá el interprete para programar o escribir las líneas que quieras.

### Asignación

```ruby
identificador = 2.0
$id = 2 #variable global
@variable #variable de instancia
@@variable_de_clase
PI = 3,14 #constante
class UnaClase
array = [1,2,3]
```

Como todo en Ruby es un objeto, crear una variable es realmente crear un objeto. Si la variable a=1 se sustituye por a="a" el objeto a=1 se destruye y se crea a="a" de forma automatica.

Los array pueden conformarse por diferentes tipos de datos y empiezan en 0.
