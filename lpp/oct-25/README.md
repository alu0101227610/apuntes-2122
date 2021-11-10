# Apuntes día 10 de noviembre

## Teorema del programa estructurado

Todo programa se puede escribir con secuancia de instrucciones, condicionales y bucles.

### Gestión de memoria

* Datos estáticos: Variables que conocen en tiempo de compilación
* Heap: espacio que almacena las estructuras de datos dinámicos como arrays.
* Pila de ejecución: Cuenta con la información de las subrutinas activas. Cada subrutina guarda un bloque de memoria con la información necesaria, llamado registro de activación o stack frame.

Si la pila de ejecución se desborda retornara un error. Esto pasa con un alto número de subrutinas activas. Cada registro de activación cuenta con un puntero a la pos de retorno, los param de entrada, las variables de la función, datos temporales y datos de retorno.

Ruby nos permite hacer _get_ y _set_ de cualquiera de nuestras variables.

```ruby
def var
  return @var
end
```

La diferencia entre _set_ y _get_ recae aquí:

```ruby
def var=(valor)
  @valor = valor
end
```

## Tema 3. Programación Orientada a Objetos

Sus principios son:

* Abstracción: Sacar caracteres importantes
* Encapsulasión: Aisla las propiedades y característica de la clase
* Principio de ocultación: Proteger los elementos y ofrecer solo la interfaz
* Herencia: Relación de clases por jerarquía
* Polimorfismo: Permite asociar un comportamiento diferente asociado al mismo nombre
* Modularidad: divide el problema en módulos y permite integrarlos

### Programación orientada a objetos en Ruby

```ruby

## Para definir una clase:
class MyClass
  def initialize
    @my=1
  end
  # definición de una instancia
  obj = MyClass.new
  # El new llama al método initialize de la clase
end
```

Un ejemplo real es:

```ruby
class MiClase
  def initialize 
   @var=1
  end

  def imprimir
    puts @var
  end

  def funcion(num1, num2)
    v_local = num1 * num2
    @var = v.local + @var
  end
end
```

Supongamos que cambiamos el método imprimir.

```ruby
def imprimir
  puts "el valor es:" + @var
end
```

Esto me va a devolver un error porque no se pueden sumar string y enteros. Para resolver esto definiremos un to_string.

```ruby
def to_s
  return "#@var"
end
```

Si intentamos imprimir escribiendo *@var.to_s* ahora la suma si sería vaida porque estamos pasando el entero a string.