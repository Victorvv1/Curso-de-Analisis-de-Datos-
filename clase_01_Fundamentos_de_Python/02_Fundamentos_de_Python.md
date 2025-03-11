## 1. Introducción

Python se ha consolidado como una herramienta fundamental para el análisis de datos gracias a su sintaxis clara, versatilidad y potente ecosistema de bibliotecas. Este módulo presenta los aspectos esenciales del lenguaje Python desde la perspectiva del análisis de datos.
El ecosistema de Python para ciencia de datos ha madurado enormemente en los últimos años. Las bibliotecas como pandas, scikit-learn y statsmodels han evolucionado significativamente, proporcionando herramientas cada vez más potentes y fáciles de usar para el trabajo con datos.
Este módulo se centra en los aspectos de Python que resultan más relevantes para la manipulación de datos. No pretende ofrecer un tutorial exhaustivo del lenguaje, sino proporcionar las habilidades específicas necesarias para trabajar eficazmente con datos estructurados.

**La práctica directa es esencial para desarrollar fluidez con estas herramientas.** Para profundizar en aspectos del lenguaje que no se cubren aquí (como clases y programación orientada a objetos), resulta útil consultar el tutorial oficial de Python y libros como "Python Cookbook", "Fluent Python" o "Effective Python".

## 2. El intérprete de Python

Python es un lenguaje interpretado, lo que significa que ejecuta las instrucciones una por una en tiempo real. El intérprete estándar de Python se activa desde la línea de comandos con el comando `python`:

```python
$ python
Python 3.10.4 | packaged by conda-forge | (main, Mar 24 2022, 17:38:57)
[GCC 10.3.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> a = 5
>>> print(a)
5

```

El símbolo `>>>` es el prompt donde se escriben las expresiones y fragmentos de código. Para salir del intérprete, se puede escribir `exit()` o pulsar Control-D (en Linux y macOS).

Ejecutar programas completos de Python es tan sencillo como llamar a `python` con un archivo `.py` como argumento. Por ejemplo, con un archivo `hello_world.py` que contenga:

```python
print("Hello world")

```

Se puede ejecutar así:

```
$ python hello_world.py
Hello world

```

Sin embargo, los analistas de datos suelen preferir entornos más potentes como IPython o Jupyter Notebooks. IPython es un intérprete mejorado que ofrece funcionalidades adicionales para facilitar el trabajo con datos. Usando el comando `%run`, IPython puede ejecutar código de un archivo dentro del mismo proceso, permitiendo explorar interactivamente los resultados:

```
$ ipython
Python 3.10.4 | packaged by conda-forge | (main, Mar 24 2022, 17:38:57)
Type 'copyright', 'credits' or 'license' for more information
IPython 7.31.1 — An enhanced Interactive Python. Type '?' for help.
In [1]: %run hello_world.py
Hello world
In [2]:

```

El prompt de IPython utiliza el formato numerado `In [n]:`, en lugar del estándar `>>>`.

## 3. IPython como ayuda para la exploración

IPython proporciona funcionalidades que facilitan enormemente la exploración de objetos y módulos. El uso del signo de interrogación (?) permite acceder a información detallada sobre objetos, mientras que el doble signo (??) muestra incluso el código fuente si está disponible. Esta característica es especialmente útil para descubrir las capacidades y propiedades de objetos desconocidos.

Otra aplicación del signo de interrogación es la búsqueda en el espacio de nombres. Por ejemplo, se puede utilizar con caracteres comodín para encontrar todas las funciones de NumPy que contengan "load":

```python
import numpy as np
np.*load*?

```

Esta consulta mostraría funciones como `np.load`, `np.loadtxt` y cualquier otra función relacionada.

## 4. Fundamentos del lenguaje Python

### Semántica del lenguaje

Python se distingue por su énfasis en la legibilidad y claridad. A diferencia de otros lenguajes que utilizan llaves para delimitar bloques de código, Python emplea la indentación (sangrado), lo que fuerza a escribir código visualmente estructurado. Después de un signo de dos puntos (:), el código debe estar sangrado de manera consistente hasta el final del bloque:

```python
for x in array:
    if x < pivot:
        less.append(x)
    else:
        greater.append(x)

```

Se recomienda utilizar cuatro espacios para la indentación, en lugar de tabuladores.

Python no requiere punto y coma al final de las sentencias, aunque se pueden utilizar para separar múltiples sentencias en una línea (algo que generalmente se evita por claridad).

### Todo es un objeto

Una característica fundamental de Python es su modelo de objetos consistente. Cada elemento en Python (números, cadenas, funciones, módulos, etc.) es un objeto con un tipo asociado y datos internos. Esto proporciona gran flexibilidad al lenguaje.

### Comentarios

Los comentarios en Python comienzan con el símbolo `#` y continúan hasta el final de la línea:

```python
# Este es un comentario
x = 5  # Este también es un comentario

```

### Funciones y métodos

Las funciones se llaman utilizando paréntesis y pueden aceptar diferentes tipos de argumentos:

```python
result = f(x, y, z)  # Llamada con argumentos posicionales
result = f(a, b, c, d=5, e="foo")  # Con argumentos posicionales y nominales

```

Los métodos son funciones asociadas a objetos específicos y se accede a ellos mediante la notación de punto:

```python
obj.some_method(x, y, z)

```

### Asignación de variables y referencias

En Python, asignar una variable crea una referencia al objeto, no una copia:

```python
a = [1, 2, 3]
b = a  # b y a apuntan al mismo objeto
a.append(4)  # Esto modifica también b

```

Esta característica es crucial para entender cómo se comportan los datos, especialmente con conjuntos grandes.

### Referencias dinámicas y tipos fuertes

Las variables en Python no tienen un tipo inherente; pueden referirse a diferentes tipos de objetos:

```python
a = 5  # a es un entero
a = "texto"  # ahora a es una cadena

```

Sin embargo, Python es un lenguaje de tipos fuertes, lo que significa que no realiza conversiones implícitas entre tipos incompatibles:

```python
"5" + 5  # Error: no se puede concatenar str e int

```

### Atributos y métodos

Los objetos tienen atributos (otros objetos almacenados dentro) y métodos (funciones asociadas), a los que se accede con la notación de punto:

```python
cadena = "texto"
cadena.upper()  # Método que devuelve "TEXTO"

```

### Duck typing

Python sigue el principio "si camina como un pato y grazna como un pato, entonces es un pato". Esto significa que lo importante es qué métodos implementa un objeto, no su tipo específico. Por ejemplo, para verificar si un objeto es iterable:

```python
def isiterable(obj):
    try:
        iter(obj)
        return True
    except TypeError:
        return False

```

### Importaciones

Los módulos en Python son archivos con extensión `.py`. Se pueden importar de varias maneras:

```python
import modulo
from modulo import funcion
import modulo as m
from modulo import funcion as f

```

### Operadores binarios y comparaciones

Python utiliza la sintaxis matemática estándar para operaciones y comparaciones:

```python
a + b  # Suma
a - b  # Resta
a * b  # Multiplicación
a / b  # División
a // b  # División entera
a ** b  # Potencia
a == b  # Igualdad
a != b  # Desigualdad
a < b   # Menor que

```

Para verificar si dos variables hacen referencia al mismo objeto, se utiliza `is`:

```python
a is b  # True si a y b apuntan al mismo objeto
a is not b  # True si a y b apuntan a objetos distintos

```

### Objetos mutables e inmutables

Algunos objetos (como listas y diccionarios) son mutables, mientras que otros (como cadenas y tuplas) son inmutables:

```python
lista = [1, 2, 3]
lista[0] = 5  # Las listas son mutables

tupla = (1, 2, 3)
tupla[0] = 5  # Error: las tuplas son inmutables

```

### Tipos escalares

Python incluye diversos tipos escalares:

- **None**: El valor nulo de Python.
- **Numéricos**: `int` (enteros de precisión arbitraria) y `float` (punto flotante de doble precisión).
- **str**: Cadenas de texto Unicode.
- **bool**: Valores booleanos `True` y `False`.
- **bytes**: Datos binarios.

### Cadenas de texto

Python maneja cadenas Unicode con gran flexibilidad. Las cadenas pueden definirse con comillas simples o dobles, y las cadenas multilínea con triples comillas:

```python
a = 'texto simple'
b = "otro texto"
c = """texto
multilínea"""

```

Las cadenas son inmutables, pero se pueden manipular mediante métodos que crean nuevas cadenas. Python 3.6 introdujo las "f-strings" para formateo de texto:

```python
nombre = "Ana"
edad = 30
f"{nombre} tiene {edad} años"  # "Ana tiene 30 años"

```

### Bytes y Unicode

Python 3 diferencia claramente entre cadenas Unicode (`str`) y datos binarios (`bytes`):

```python
texto = "español"
bytes_utf8 = texto.encode("utf-8")  # Convierte a bytes con codificación UTF-8
texto_de_nuevo = bytes_utf8.decode("utf-8")  # Vuelve a str

```

### Fechas y horas

El módulo `datetime` proporciona los tipos `datetime`, `date` y `time`:

```python
from datetime import datetime, date, time
dt = datetime(2023, 3, 15, 10, 30)  # 15 de marzo de 2023, 10:30
d = dt.date()  # Solo la fecha
t = dt.time()  # Solo la hora

```

Las diferencias entre fechas producen objetos `timedelta`.

## 2.4 Control de flujo

### Condicionales: if, elif, else

Las estructuras condicionales permiten ejecutar código basado en condiciones:

```python
if x < 0:
    print("Negativo")
elif x == 0:
    print("Cero")
else:
    print("Positivo")

```

### Bucles for

Los bucles `for` se utilizan para iterar sobre colecciones:

```python
for valor in coleccion:
    # Hacer algo con valor

```

Los bucles pueden controlarse con `continue` (saltar a la siguiente iteración) y `break` (terminar el bucle):

```python
for i in range(10):
    if i == 3:
        continue  # Salta el 3
    if i == 7:
        break  # Termina al llegar al 7
    print(i)

```

### Bucles while

Ejecutan un bloque mientras una condición sea verdadera:

```python
while condicion:
    # Hacer algo

```

### La función range

Genera secuencias de números enteros:

```python
range(10)  # 0, 1, 2, ..., 9
range(5, 10)  # 5, 6, 7, 8, 9
range(0, 10, 2)  # 0, 2, 4, 6, 8

```

Es especialmente útil para iterar un número específico de veces:

```python
for i in range(5):
    print(i)

```

### La sentencia pass

No hace nada y se utiliza como marcador de posición donde se requiere una sentencia:

```python
if condicion:
    pass  # Por implementar
else:
    # Código real

```
