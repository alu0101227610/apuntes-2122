# Apuntes día 2 de noviembre

```ruby
class Point
  def metodo instancia
  def initialize(x,y)
    @x, @y = x,y
  end
  def *(valor)
    Point.new(@x*valor, @y*valor)
  end
  def to_s
  return "(#{@x}, #{@y})"
  end

  attr_reader :x, :y
```

## Método de trabajo

1. Crear la clase en file *.rb en un directorio \lib
2. Crear un fichero de pruebas para las pruebas unitarias (son afirmaciones o assert)
    Las pruebas las guardamos en el directorio \test bajo el nombre *tc_loquesea.rb*
    El test desde probar todas las funcionalidades del código

    ```ruby
    def test_simple
      assert("(0,0)", Point.new(0,0).to_s)
      assert(0, Point.new(0,0).x)
      assert(0, Point.new(0,0).y)
    end
    ```

Para probar el test hacemos:

`Ruby -I. tc_loquesea.rb`

Para los test podemos crearun rakefile con la linea de comando a ejecutar:

```ruby
task :pu do
  sh "Ruby -I. \test\tc_loquesea.rb"
end
```

y lo ejecutamos con rake. El -I. hace que busque el fichero en el directorio hacia abajo. En las pruebas unitarias podemos hacer

```ruby
def setup
  @origen = new(0,0)
end
```

y así solo hacemos un punto en luegar de hacer 3 o más.

Añadimos la clase rectangulo

```ruby
class Rectangulo
  attr_reader :x, :y

  def initizalize (x, y)
    @x, @y = x, y
  end
  def to_s
    "Rect #{@x}, #{@y}"
  end
end
```

### Duck Typing

Podemos sumar la clase punto con el rectangulo porque ambos disponen de x e y, aunque sean diferentes. 

Esto se conoce como tipeado pato o duck typing. Esto significa no poner restricciones de tipo en los métodos.