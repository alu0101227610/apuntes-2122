# Apuntes día 19 de octubre

## Tema 2: _Programación imperativa_

Es aquella más cercana a la máquina, es posible gracias a la arquitectura de Von Neumann y conseguimos el modelo de programa alcmacenado.

```assembly
mov a, R1
mov b, R2
add R2, R1
mov R1, c
```

Este programa almacena en la memoria de programa y mediante el Program Counter recorremos secualcialmente la memoria de programa. El PC es un registro especial.

Por otra parte, nos abstraemos y la dirección de memoria la llamemos a y así con las variables b y c. Para acceder a los datos en la memoria de datos usamos el (base pointer)BP y el (stack pointer)SP.

```assembly
label suma:
  mov a, R1
  mov b, R2
  add R2, R1
  mov R1, c

  go to next

  mov #1, a
  mov #2, b

  go to suma
```

Este codigo se traduce a:

```C
static int a=1, b=2, c;
void main() {
  c = a + b;

  int n=1, n=2, p;
  p = suma (m+n);
}

int suma(x,y) {
  return x+y;
}
```

En un sistema procedural al llamar a la función 'suma' se reserva memoria para la función.

En la memoria de datos durante la ejecución se modifica solamente la pila y el heap. Dentro de la pila se cuanta con registros de activación para activar subrutinas:

* Valor a devolver
* Parámetros que se le pasa
* Zona de control
* Variables locales
* Variables temporales

En el ejemplo que vimos en la suma, en la pila de ejecución al terminal la llamada a la función la memoeria se borra. La zona de control apunta a su procedimiento previo y los registros de activación permite cambiar variables en tiempo de ejecución y emplear subrutinas.

`hash = {:clave1="valor1", :clave2="a"}`

Los hash definen pares del tipo clave - valor. Para aaceder a un valor del hash:

`hash[:clave1]`
