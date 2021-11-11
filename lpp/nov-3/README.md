# Apuntes día 3 de noviembre

Continuamos con la metodología de desarrollo de software con pruebas unitarias.

## Metología TDD

Desarrollo dirigido por pruebas o test driven development(TDD).

1. Se escribe una prueba para especificar una funcionalidad
2. Se ejecuta y obviamente falla porque no existe el código
3. Se escribe la misma cantidad de código que hace funcionar las pruebas
4. Se ejecuta y confirma el correcto funcionamiento.

### Directorios

en \lib, guardamos el codigo fuente y en \spec guardamos las pruebas. En este tipo de metodología utilizaremos la gema RSpec.

En spec debemos crear un fichero prueba.rb. y en ella iremos escribriendo la descripción de cada una de las pruebas:

```ruby
describe Point do
end

it "debe pder instanciar un punto" do
 #prueba
end
```

La primera prueba siempre da error, porque aun no hemos de crear el fichero point.rb, la primera prueba describe también falla porque hay que crear la clase. Una vez creada pasamos a comprobar que existe una manera de inicializar un punto. Se crea el initizalize con los argumentos esperados.

```ruby
it "se instancia un point(x, y)" do
 #define expect
 expect(Point.new(0,0).not_to eq(nil))
end
```
