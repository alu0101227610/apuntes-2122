# Apuntes día 26 de octubre

## Desarrollar una clase para representar puntos en los ejes cartesianos

Requerimos de una coordenada x e y para cada punto

```RUBY
class Point
  def initialize(x,y)
    @x, @y = x,y 
    #iniciamos variables de instancia
  end
  def to_s
    "(#{@x}, #{@y})" 
    #método de instancia que accede a las variables de instancia
  end
```

Para acceder a las variables de instancia no podemos hacerlo desde fuera de la clase, usamos _getters_.

```ruby
def get_x
  @x
end

# se prefiere escribir lo siguiente
def get_y
  return @y
end

# se puede también escribir 
attr_reader :x, :y

# Setters
def set_x (valor)
  @x = valor
end

def set_y (valor)
  @y = valor
end

### alternativamente
def x=(valor)
  @x = valor
end

###
attr_writer :x, :y

#También podemos crear el attr_reader y el attr_write usando
attr_accessor :x, :y
```

Normalmente no se emplea más que *attr_reader* para mantener buenas practicas y evitar accedo de otra clase a nuestra clase.

## Metodología de desarrollo software

### Pruebas unitarias
Primero se codifica y posteriormente se crea la prueba para la funcionalidad implementada.

>"Añado una funcionalidad y se prueba y así sucesivamente."

En el rake, haremos la prueba en Ruby. Según los directorios tendremos que tener un directorio _\lib_ donde guardamos el código y un directorio _\test_ donde guardaremos las pruebas.

las pruebas de las pruebas unitarias se llaman _asserts_ o _confirmaciones_.