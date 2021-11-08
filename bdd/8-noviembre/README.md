# Apuntes día 8 de noviembre

## Tema 3: *_SQL_*

SQL {structure querry language}

### Conceptos generales

* Este lenguaje contiene relativamente pocas sentencias
* Las secuencias se forman for clausulas
* El lenguaje no entiende de mayusculas o minusculas.
  * Pero se usan mayusculas como buena practica
* Las secuencias se divide en líneas por clusulas para mantener estilo
* Las clausulas que daremos en clase son obligatorias

Las sentencias que veremos son:

* SELECT
* INSERT
* DELETE
* UPDATE

### Select

El select es equivalente a la proyección no a la selección

```SQL
SELECT * FROM CLIENTE
```

Esto muestra todas las tuplas de Cliente.

Aunque SELECT sea la proyección, esta proyección *no* borra los duplicados a no ser que se lo indiques; no es una proyección algebraica.

```SQL
SELECT NBC FROM CLIENTES
```

Para que no existan duplicados lo escribiriamos de la siguiente forma añadiendo la extension _DISTINCT_.

```SQL
SELECT DISTINCT NBC
FROM CLIENTES;
```

Si quiero proyectar sobre 2 columnas lo puedo especificar:

```SQL
SELECT DNI, NBC
FROM CLIENTES;
```

Lo que no podemos hacer es utilizar el elemento de seleccionar todos (*) junto con una columna. (`SELECT DNI, *`)

Para crear un alías para la selección que queremos hacer lo escribiremos de la siguiente manera:

```SQL
SELECT FF_FI "Número de días"
FROM PLAN_DOCENTE;
```

También se aceptaría como nombre _numero_de_dias_, otro ejemplo visto puede ser:

```SQL
SELECT UNIQUE CDC CIUDAD 
FROM CLIENTE;
```

Esto muestra la columna de CDC pero con el nombre de columna CIUDAD

```TXT
CIUDAD
-------
LA LAGUNA
TACORONTE
```

El objeto del _FROM_ del _SELECT_ puede ser producto cartesiano de tablas

```SQL
SELECT *
FROM TABLA1, TABLA2;
```

Esto equivale a `TABLA1 X TABLA2`, tengamos en cuenta que el producto cartesiano no es equivalente a una yunción natural.

```SQL
SELECT C1.DNI
FROM CUENTA C1, CLIENTE C2;
```

Para representar el producto cartesiano:

```SQL
SELECT *
FROM T1 CROSS JOIN T2;
```

Para representar la yunción natural:

```SQL
SELECT *
FROM T1 NATURAL JOIN T2;
```

Un ejemplo real:

```SQL
SELECT CDC
FROM CLIENTE NATURAL JOIN CUENTA;
```

Visto en álgebra relacional como: `P(CDC)(CLIENTE*CUENTA)`.

Para realizar una yunción interna de tablas incluyendo una condición de la que depender lo hacemos de la siguiente manera:

```SQL
SELECT CDC
FROM CLIENTE INNER JOIN CUENTA ON (CIENTE.DNI = CUENTA.DNI);
```

Podemos utilizar las siguiente clausulas:

* ON (_predicado_)
* USING (_predicado_)
* AND (_predicado_)
* OR (_predicado_)
* NOT (_predicado_)

También existe la clausula _WHERE_ (opcional) que podemos utilizar así: `WHERE CLIENTE.DNI = CUENTA.DNI;`.
Si decidimos utilizar esta cláusula debe ir justo después de _FROM_ y equivale al operador selección del álgebra relacional.

Dentro del _WHERE_ puede aparecer constantes, atributos, operaciones, expresiones, etc.

Esta selección nos da los DNI de las personas con cuenta en la sucursal con código 1.

```SQL
SELECT DNI
FROM CUENTA
WHERE CS=1;
```

Esta selección nos da los DNI de las personas con cuenta en la sucursal con código 1 y 2, está mal porque una cuenta con dos códigos de cuenta no puede existir.

```SQL
SELECT DNI
FROM CUENTA
WHERE (CD=1) AND (CS=2);
```

Esta selección nos da los DNI de las sucursales con saldo mayor a 10.000:

```SQL
SELECT DNI
FROM CUENTA
WHERE SLD >= 10000;
```

El operador lógico _BETWEEN_:

`expresion between exp1 and exp2`

Si la expresión pertenece a [exp1, exp2], devuelve true, se puede obtener lo contrario escribiendo un _NOT_ delante del _BETWEEN_.

Por ejemplo:

```SQL
SELECT DNI
FROM CUENTA
WHERE  CS=1 AND (NC BETWEEN 100 AND 300);
```

También se podría poner como `(NC >= 100) AND (NC <= 300)`

El operador lógico _IN_:

`expresion NOT IN (conjunto de valores)`

Devuelve true si el valor está contenido en la expresión, este se pude negar igual que el _WHERE_.

```SQL
SELECT DNI
FROM CUENTA
WHERE CS IN (2, 4, 6);
```

También se podría poner como: `(CS=2) OR (CS=4) OR (CS=6)`, la operación contraria sería usando _AND_ en lugar de _OR_.

DNI de personas que tienen cuenta en la sucursal donde tiene cuenta la persona con DNI 1111.

```SQL
SELECT DNI
FROM CUENTA
WHERE CS IN(SELECT CS
            FROM CUENTA
            WHERE DNI=1111);
```

Para negar la condición pondríamos `NOT IN`.

Una resta se podría ver de la siguiente manera:

```SQL
SELECT CS
FROM CUENTA C1
WHERE DNI NOT IN (SELECT DNI
                  FROM CUENTA
                  WHERE SLD > 10000);
```

En algebra relacional sería: `P(DNI)(CUENTA) - P(DNI)(DLC > 10000)(CUENTA)`.
