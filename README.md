# funciones
 Prácticamente todos los lenguajes de programación actuales permiten una forma de crear funciones definidas por el usuario.
* No siempre se denominan funciones.
* En otros lenguajes pueden llamarse:
  * Subrutinas
  * Procedimientos
  * Métodos
  * Subprogramas
Una función en Python es un bloque de código reutilizable que realiza una tarea específica cuando se llama. Las funciones toman ciertos valores de entrada (llamados argumentos) y pueden devolver un valor como resultado.

Ejemplo simple de una función en Python:


```` python 
def saludar(nombre):
     Esta función imprime un saludo personalizado."""
    print("¡Hola, " + nombre + "!")
 ````   
Llamamos a la función para saludar a alguien.
saludar("Juan")
saludar("María")
En este ejemplo, hemos definido una función llamada saludarque toma un argumento nombre. Cuando llamamos a esta función con un nombre, imprimirá un mensaje de saludo personalizado en la consola. Puedes reutilizar esta función para saludar a cualquier persona simplemente pasando su nombre como argumento.
* Al escribir un código específico útil, conforme se realice el desarrollo, es probable que ese segmento de código se use con frecuencia y se tiene que repetir muchas veces en la aplicación.
* Se podría replicar el código todas las veces que sea necesario (copy & paste)
* Si después es necesario modificar el código en cuestión por:
  * algún problema que deba solucionarse o 
  * necesita mejoras de alguna manera.
  * y hay copias del código esparcidas por toda su aplicación se deberán realizar los cambios necesarios en todos lados.<br><br>
* **Solución:**
* Definir una función de Python que realice la tarea.
* En cualquier lugar de la aplicación donde necesite realizar la tarea, simplemente se llama a la función.
* En el futuro, si decide cambiar cómo funciona, entonces solo se necesita cambiar el código en una ubicación, que es el lugar donde está defina la función.
* Los cambios se realizarán de manera automática en todos los lugares donde sea llamada la función.
----------
* Esto podría decirse que es:
  * Abstracción
  * Reusabilidad
* Sigue el principio del desarrollo de software de no repetirse a sí mismo (DRY: Don't Repeat Yourself)
* Principal motivación para el uso de funciones.

  
* Una función se declaran con la palabra reservada *def*
* Una función puede recibir parámetros
* Una función puede retornar un valor, varios o ninguno
* Cuando no retorna nada de manera explícita, siempre retorna *None*
* Una función puede ser recursiva
* Sintaxis general de una función:

``` python
def <function_name>([<parameters>]):
    <statement(s)>
```
 Para llamar a la función:
``` python
<function_name>([<arguments>])
```
* <arguments> son los valores pasados a la función.
* Corresponden a los <parameters> en la definición de la función.
* Se puede definir una función que no acepte ningún argumento, pero los paréntesis aún son necesarios.
* Tanto una definición de función como una llamada a función siempre deben incluir paréntesis, aunque estén vacíos.


  ##### Argumentos posicionales (obligatorios)
* La forma más sencilla de pasar argumentos a una función de Python es con argumentos posicionales u obligatorios.
* En la definición de la función se especifica una lista de parámetros separados por comas dentro del paréntesis:
  ````
  def productos(producto, cantidad, precio):
    print(f" {cantidad} {producto} cuestan {precio} pesos")

  productos("manzanas", 5, 7.5)
  ```

* Los parámetros (producto, cantidad y precio) se comportan como variables definidas localmente en la función.
* Cuando se llama a la función, los argumentos que se pasan ("manzanas", 5, 7.5) están vinculados a los parámetros en orden
 Los argumentos posicionales son la forma más sencilla de pasar datos a una función
* Ofrecen la menor flexibilidad.
* El orden de los argumentos en la llamada debe coincidir con el orden de los parámetros en la definición. 
* Por supuesto, no hay nada que nos impida cambiar el orden especificado en la definición de la función

  ##### Argumentos nombrados o de palabra clave (Keyword arguments)

* Cuando se invoca a una función se pueden especificar los argumentos en el formato <palabra_clave>=\<valor>.
* Cada <palabra_clave> debe coincidir con un parámetro en la definición de la función de Python. 
* Por ejemplo, la función productos() se puede invocar con argumentos de palabras clave de la siguiente manera:
````
productos(producto="manzanas", cantidad=5, precio=7.5)
````
* Ahora sí es posible cambiar el orden de los parametros

  ##### Parámetros por defecto (default)

* Se especifica en una definición de función de Python de la forma <nombre>=\<valor>
* \<valor> se convierte en un valor predeterminado para ese parámetro.
* Se denominan parámetros predeterminados u opcionales. 
* Ejmplo:

````
  def productos(producto="productos", cantidad="0", precio=0.0):
    print(f" {cantidad} {producto} cuestan {precio} pesos")

# Invocación sin argumentos
productos()
````
###  Retorno de Valores y uso de la palabra clave return.
* Una instrucción *return* en una función de Python tiene dos propósitos:
1. Al terminar la función devuelve el control de ejecución a partir de donde se llamó.
2. Proporciona un mecanismo para regresar datos donde se llamó o asignó.

````
    def f1():
    print("Hola")
    print("Mundo")
    returnf1()
````
``
    def f2():
    print("Hola")
    print("Mundo")
    f2()
``
* *return* no necesita estar al final de una función.
* Pueden aparecer en cualquier parte del cuerpo de una función
* Puede aparecer incluso varias veces

####  Funciones sin valor de retorno (None).
``
def f(x):
    if x < 0:
        return
    if x > 10:
        return
    print(x)
``
* Puede usarse para la comprobación de errores

```python
def f():
    if error_cond1:
        return
    if error_cond2:
        return
    if error_cond3:
        return

    <normal processing>
```
* Cuando no se da ningún valor de retorno, una función devuelve el valor especial None
``
  def f():
    return
  print(f())
``

#### Parámetros variables (`*args` y `**kwargs`).

* En ocasiones, cuando se está definiendo una función, es posible que no sepa de antemano cuántos argumentos va a tomar.
* Ejemplo: Se desea escribir una función de Python que calcule el promedio de varios valores.

`` 
   def avg(a, b, c):
    return (a + b + c) / 3
   avg(1, 2, 3)
``
Restricciones:
* el número de argumentos aprobados debe coincidir con el número de parámetros declarados.
* No funciona esta implementación para cualquier cantidad de valores distinta a tres

Si se define la función con parámetros opcionales:

``
 def avg(a, b=0, c=0):
    match True:
        case True if b==0 and c==0:
            avg = a
        case True if c==0:
            avg = (a + b)/2
        case _:
            avg = (a + b + c)/3
    return avg
    avg(5)
``

* Otra forma de pasar a una función un número variable de argumentos con empaquetado y desempaquetado de tupla de argumentos utilizando el operador asterisco (*).
* Cuando el nombre de un parámetro en una definición de función está precedido por un asterisco (*), indica el empaquetado de tupla de argumentos. 
* Todos los argumentos correspondientes en la llamada a la función se empaquetan en una tupla a la que la función puede hacer referencia por el nombre de parámetro dado. 
* Ejemplo:

``
def f(*args):
    print(f"args: {args}")
    print(f"Tipo: {type(args)}, Longitud: {len(args)}")
    print("Valores")
    for x in args:
            print(f"{x}",end="|")
f(1, 2, 3)
``

### Funciones como Objetos


####  Asignación de funciones a variables.

##### Escriba una función double que obtenga el doble de un valor mediante el uso de una variable.

````
 # Definir la función double
 def double(x:int)->int:
    return x * 2
 # Asignar la función double a la variable my_double
 my_double = double
 print(type(my_double))
 # Llamar a la función a través de la variable
 result = my_double(5)
 # Imprimir el resultado
 print(result)
````

* Este programa define una función llamada `double` que toma un argumento `x` y devuelve el doble del mismo.
* La función `double` se asigna a la variable `my_double`.
* La función `my_double` se llama con el argumento 5 y el resultado se asigna a la variable `result`. 
* Finalmente, el programa imprime el valor de `result` en la pantalla, que es el resultado de llamar a la función `double` con el argumento 5.


  ####  Paso de funciones como argumentos.
  ##### Escriba un programa que mediante el uso de dos funciones: double() y cuad(), se pueda obtener el cuadrado del doble de un número entero. La función double debe ser usada como argumento de cuad.


````
def double(x:int)->int:
    return x * 2

# Llamar a la función a través de la variable
doble = double(3)

def cuad(f):
    return f ** 2

cuadrado = cuad(doble)
print(cuadrado)


````

* Este programa define dos funciones, `double` y `cuad`
* las utiliza para calcular el cuadrado del doble de un número. 
* Primero, la función `double` multiplica su argumento por 2 y lo devuelve.
* Luego, la función `cuad` toma un argumento `f` y devuelve el cuadrado de `f`.
* El programa asigna la función `double` a la variable `my_double`, llama a `my_double` con el argumento 5 y asigna el resultado a la variable `doble`.
* Finalmente, el programa llama a `cuad` con `doble` como argumento y asigna el resultado a la variable `cuadrado`, que se imprime en pantalla.


#### Funciones anónimas (lambda functions).
Las funciones lambda en Python son funciones anónimas que se pueden definir en una sola línea de código. 

  - Las funciones lambda:
        * se definen utilizando la palabra clave `lambda`, seguida de los argumentos de la función separados por comas y luego dos puntos.
        * es una expresión que se evalúa y devuelve como resultado.
        - son funciones anónimas, lo que significa que no tienen un nombre definido.
        - se pueden asignar a una variable y luego llamar a través de esa variable.
        - se utilizan comúnmente como argumentos de otras funciones, como `map()`, `filter()`, `reduce()`, etc.
        - son útiles para escribir código más conciso y legible (cuando se trabaja con funciones simples y de una sola línea)


````
def identity(x):
    return x

print(identity(3))
````

### Recursión

#### Definición de funciones recursivas.

* Una definición recursiva es aquella en la que el término definido aparece en la propia definición.
* Capacidad de una función de llamarse a sí misma
* La mayoría de los problemas de programación se pueden resolver sin recursividad. 
* Entonces... la recursividad no suele ser necesaria.
--------
* El recorrido de estructuras de datos en forma de árbol es un ejemplo.
* Debido a que se trata de estructuras anidadas, se ajustan fácilmente a una definición recursiva.
* Es probable que un algoritmo no recursivo para recorrer una estructura anidada sea algo burdo.
* Una solución recursiva puede ser más elegante y eficiente.

````
def f():
    x = 10
    f()
````


## Ejercicios en "Guizero":
##### **`-Creando una Aplicación GUI con Guizero`**

El siguiente código es un ejemplo de cómo crear una aplicación de interfaz gráfica de usuario (GUI). Esta aplicación creará una ventana con el título "Hello world".

```python
from guizero import App

# Crear una instancia de la aplicación con el título "Hello world"
app = App(title="Hello world")

# Mostrar la ventana de la aplicación
app.display()
````
**"from guizero import App"**: Esta línea importa la clase App de la biblioteca guizero, que se utilizará para crear la aplicación GUI.

**"app = App(title="Hello world")"**: Aquí se crea una instancia de la aplicación (app) con un título específico, que en este caso es "Hello world".

**"app.display()"**: Esta línea muestra la ventana de la aplicación en la pantalla del usuario, lo que permite interactuar con la interfaz gráfica.



##### **`-Creando una Aplicación GUI que muestra un mensaje luego de oprimir un boton generado`**
````python
from guizero import App, Text, PushButton
# Definir una función llamada say_hello que se ejecutará cuando se haga clic en el botón
def say_hello():
    message_2.value = "ICI Rocks!"  # Cambia el valor de message_2 cuando se hace clic

app = App("ICI App")

# Crear un objeto "Text" llamado "message" y mostrar un mensaje en la ventana de la aplica-ción
message = Text(app, text="Welcome to the ICI App!")
message_2=Text(app)
button = PushButton(app, text="Click me!", command=say_hello)

app.display()

````
**1.-** Importa las clases App, Text y PushButton de la biblioteca guizero.

**2.-** Define una función llamada "say_hello" que se ejecutará cuando se haga clic en el botón. Esta función cambia el valor del objeto "message_2" a "ICI Rocks!".

**3.-** Crea una instancia de la clase "App" llamada "ICI App". Esto crea la ventana principal de la aplicación.

**4.-** Crea un objeto Text llamado "message" y muestra el mensaje "Welcome to the ICI App!" en la ventana de la aplicación.

**5.-** Crea un objeto Text llamado "message_2", que inicialmente no contiene ningún texto. Este objeto se utilizará para mostrar un mensaje diferente cuando se haga clic en el botón.

**6.-** Crea un botón llamado "button" con el texto "Click me!" y lo asocia a la función say_hello utilizando el parámetro command.

