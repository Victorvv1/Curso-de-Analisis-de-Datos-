## 1. Introducción

Las estructuras de datos son fundamentales para organizar, almacenar y manipular información de manera eficiente. Python proporciona varias estructuras de datos integradas que son esenciales para el análisis de datos y la programación en general.

Este módulo explora en profundidad las estructuras de datos nativas de Python, que constituyen los bloques fundamentales para trabajar con datos. Aunque más adelante se utilizarán estructuras de datos especializadas proporcionadas por bibliotecas como NumPy y pandas, comprender las estructuras de datos básicas de Python es esencial para trabajar eficazmente con estas herramientas más avanzadas.

Las estructuras de datos integradas de Python son notablemente versátiles y expresivas, lo que permite a los programadores representar problemas complejos de manera clara y concisa. Además, estas estructuras están optimizadas para diferentes casos de uso, lo que permite seleccionar la más adecuada según los requisitos específicos de cada situación.

## 2. Tuplas

Las tuplas son secuencias ordenadas inmutables (no modificables). Se definen encerrando elementos separados por comas entre paréntesis.

```python
tupla = (4, 5, 6)
# También se puede crear sin paréntesis
otra_tupla = 4, 5, 6

```

Las tuplas se pueden construir de varias maneras:

```python
# Tupla vacía
tupla_vacia = ()

# Tupla con un solo elemento (requiere una coma)
tupla_singleton = (42,)

# Usando la función tuple()
tupla_desde_lista = tuple([1, 2, 3])

```

### Propiedades de las tuplas

1. **Inmutabilidad**: Una vez creada, no se puede modificar.

```python
t = (1, 2, 3)
# t[0] = 5  # Esto provocaría un error TypeError

```

1. **Acceso por índice**: Se accede a los elementos mediante índices, comenzando desde 0.

```python
t = (1, 2, 3)
print(t[0])  # 1
print(t[-1])  # 3 (último elemento)

```

1. **Segmentación (slicing)**: Se pueden extraer porciones de una tupla.

```python
t = (1, 2, 3, 4, 5)
print(t[1:3])  # (2, 3)

```

1. **Concatenación**: Se pueden combinar tuplas.

```python
t1 = (1, 2, 3)
t2 = (4, 5, 6)
t3 = t1 + t2  # (1, 2, 3, 4, 5, 6)

```

1. **Anidación**: Las tuplas pueden contener otras tuplas.

```python
anidada = (1, 2, (3, 4))
print(anidada[2][0])  # 3

```

### Desempaquetado de tuplas

El desempaquetado permite asignar los elementos de una tupla a variables individuales.

```python
t = (1, 2, 3)
a, b, c = t
print(a)  # 1
print(b)  # 2
print(c)  # 3

```

También se puede usar el desempaquetado en bucles:

```python
tuplas = [(1, 'a'), (2, 'b'), (3, 'c')]
for numero, letra in tuplas:
    print(f"Número: {numero}, Letra: {letra}")

```

### Aplicaciones de las tuplas

Las tuplas se utilizan comúnmente en los siguientes casos:

1. **Retorno de múltiples valores** desde una función.

```python
def minmax(lista):
    return min(lista), max(lista)

minimo, maximo = minmax([1, 5, 3, 9, 2])

```

1. **Claves en diccionarios**: Al ser inmutables, pueden usarse como claves en diccionarios.
2. **Datos heterogéneos**: Cuando se tienen datos de diferentes tipos que están relacionados lógicamente.

```python
# Nombre, edad, profesión
persona = ("Ana López", 28, "Ingeniera")

```

## 3. Listas

Las listas son secuencias ordenadas mutables (modificables). Se definen encerrando elementos separados por comas entre corchetes.

```python
lista = [1, 2, 3, 4, 5]

```

### Creación de listas

Existen múltiples formas de crear listas:

```python
# Lista vacía
lista_vacia = []

# Lista con elementos
numeros = [1, 2, 3, 4, 5]

# Lista heterogénea
mixta = [1, "dos", 3.0, [4, 5]]

# Usando la función list()
lista_desde_tupla = list((1, 2, 3))

# Mediante comprensión de listas
cuadrados = [x**2 for x in range(10)]

```

### Operaciones con listas

1. **Acceso a elementos**: Similar a las tuplas.

```python
lista = [1, 2, 3, 4, 5]
print(lista[0])  # 1
print(lista[-1])  # 5

```

1. **Modificación de elementos**:

```python
lista = [1, 2, 3, 4, 5]
lista[0] = 10
print(lista)  # [10, 2, 3, 4, 5]

```

1. **Añadir elementos**:

```python
lista = [1, 2, 3]
lista.append(4)  # Añade al final
print(lista)  # [1, 2, 3, 4]

lista.insert(1, 1.5)  # Inserta en posición específica
print(lista)  # [1, 1.5, 2, 3, 4]

lista.extend([5, 6])  # Extiende con otra secuencia
print(lista)  # [1, 1.5, 2, 3, 4, 5, 6]

```

1. **Eliminar elementos**:

```python
lista = [1, 2, 3, 4, 5]
del lista[0]  # Elimina por índice
print(lista)  # [2, 3, 4, 5]

elemento = lista.pop(1)  # Elimina y devuelve el elemento
print(elemento)  # 3
print(lista)  # [2, 4, 5]

lista.remove(4)  # Elimina por valor
print(lista)  # [2, 5]

lista.clear()  # Vacía la lista
print(lista)  # []

```

1. **Ordenamiento y reversión**:

```python
lista = [3, 1, 4, 1, 5, 9, 2]
lista.sort()  # Ordena la lista in-place
print(lista)  # [1, 1, 2, 3, 4, 5, 9]

lista.reverse()  # Invierte el orden
print(lista)  # [9, 5, 4, 3, 2, 1, 1]

# Ordenamiento personalizado
nombres = ["Ana", "carlos", "Beatriz"]
nombres.sort(key=str.lower)  # Ordena sin distinguir mayúsculas/minúsculas
print(nombres)  # ['Ana', 'Beatriz', 'carlos']

```

### Comprensión de listas

La comprensión de listas es una forma concisa y potente de crear listas a partir de expresiones:

```python
# Formato básico: [expresión for elemento in iterable]
cuadrados = [x**2 for x in range(10)]
print(cuadrados)  # [0, 1, 4, 9, 16, 25, 36, 49, 64, 81]

# Con condición: [expresión for elemento in iterable if condición]
pares = [x for x in range(20) if x % 2 == 0]
print(pares)  # [0, 2, 4, 6, 8, 10, 12, 14, 16, 18]

# Anidada
matriz = [[i*j for j in range(1, 4)] for i in range(1, 4)]
print(matriz)  # [[1, 2, 3], [2, 4, 6], [3, 6, 9]]

```

La comprensión de listas suele ser más eficiente y legible que los bucles tradicionales:

```python
# Con comprensión de listas
cuadrados = [x**2 for x in range(10)]

# Equivalente con bucle
cuadrados = []
for x in range(10):
    cuadrados.append(x**2)

```

### Operaciones comunes en análisis de datos

1. **Filtrado**:

```python
# Filtrar valores mayores que 5
datos = [2, 7, 1, 8, 4, 9]
mayores_que_cinco = [x for x in datos if x > 5]
print(mayores_que_cinco)  # [7, 8, 9]

```

1. **Transformación**:

```python
# Convertir temperaturas de Celsius a Fahrenheit
celsius = [0, 10, 20, 30, 40]
fahrenheit = [(9/5) * c + 32 for c in celsius]
print(fahrenheit)  # [32.0, 50.0, 68.0, 86.0, 104.0]

```

1. **Extracción de atributos**:

```python
class Persona:
    def __init__(self, nombre, edad):
        self.nombre = nombre
        self.edad = edad

personas = [Persona("Ana", 28), Persona("Carlos", 35), Persona("Eva", 22)]
nombres = [p.nombre for p in personas]
print(nombres)  # ['Ana', 'Carlos', 'Eva']

```

## 4. Diccionarios

Los diccionarios son colecciones no ordenadas de pares clave-valor. Se definen encerrando pares clave:valor separados por comas entre llaves.

```python
diccionario = {"nombre": "Ana", "edad": 28, "profesion": "Ingeniera"}

```

### Creación de diccionarios

```python
# Diccionario vacío
vacio = {}

# Diccionario con elementos
persona = {"nombre": "Ana", "edad": 28, "profesion": "Ingeniera"}

# Usando la función dict()
persona = dict(nombre="Ana", edad=28, profesion="Ingeniera")

# A partir de secuencia de pares
items = [("a", 1), ("b", 2)]
d = dict(items)

# Mediante comprensión de diccionarios
cuadrados = {x: x**2 for x in range(5)}
print(cuadrados)  # {0: 0, 1: 1, 2: 4, 3: 9, 4: 16}

```

### Operaciones con diccionarios

1. **Acceso a valores**:

```python
persona = {"nombre": "Ana", "edad": 28, "profesion": "Ingeniera"}
print(persona["nombre"])  # Ana

# Usando el método get (evita errores si la clave no existe)
print(persona.get("ciudad", "No especificada"))  # No especificada

```

1. **Modificación**:

```python
persona = {"nombre": "Ana", "edad": 28}
persona["edad"] = 29  # Actualiza un valor
persona["ciudad"] = "Madrid"  # Añade un nuevo par
print(persona)  # {'nombre': 'Ana', 'edad': 29, 'ciudad': 'Madrid'}

```

1. **Eliminación**:

```python
persona = {"nombre": "Ana", "edad": 28, "ciudad": "Madrid"}
del persona["ciudad"]  # Elimina un par
print(persona)  # {'nombre': 'Ana', 'edad': 28}

edad = persona.pop("edad")  # Elimina y devuelve el valor
print(edad)  # 28
print(persona)  # {'nombre': 'Ana'}

persona.clear()  # Vacía el diccionario
print(persona)  # {}

```

1. **Iteración**:

```python
persona = {"nombre": "Ana", "edad": 28, "profesion": "Ingeniera"}

# Iterar sobre claves
for clave in persona:
    print(clave)

# Iterar sobre valores
for valor in persona.values():
    print(valor)

# Iterar sobre pares clave-valor
for clave, valor in persona.items():
    print(f"{clave}: {valor}")

```

### Diccionarios anidados

Los diccionarios pueden contener otros diccionarios, lo que permite representar datos jerárquicos.

```python
empleados = {
    "E001": {
        "nombre": "Ana López",
        "departamento": "Ventas",
        "salario": 40000
    },
    "E002": {
        "nombre": "Carlos Gómez",
        "departamento": "IT",
        "salario": 40000
    }
}

print(empleados["E001"]["salario"])  # 45000

```

### Aplicaciones en análisis de datos

Los diccionarios son extremadamente útiles en análisis de datos para:

1. **Conteo de frecuencias**:

```python
palabras = ["manzana", "naranja", "manzana", "pera", "naranja", "manzana"]
frecuencia = {}

for palabra in palabras:
    if palabra in frecuencia:
        frecuencia[palabra] += 1
    else:
        frecuencia[palabra] = 1

print(frecuencia)  # {'manzana': 3, 'naranja': 2, 'pera': 1}

# Versión más concisa usando defaultdict
from collections import defaultdict
frecuencia = defaultdict(int)
for palabra in palabras:
    frecuencia[palabra] += 1

```

1. **Agrupación de datos**:

```python
estudiantes = [
    {"nombre": "Ana", "curso": "Matemáticas", "nota": 8.5},
    {"nombre": "Carlos", "curso": "Física", "nota": 7.2},
    {"nombre": "Eva", "curso": "Matemáticas", "nota": 9.1},
    {"nombre": "David", "curso": "Física", "nota": 6.8}
]

# Agrupar por curso
por_curso = {}
for estudiante in estudiantes:
    curso = estudiante["curso"]
    if curso not in por_curso:
        por_curso[curso] = []
    por_curso[curso].append(estudiante)

print(por_curso["Matemáticas"])  # [{'nombre': 'Ana', ...}, {'nombre': 'Eva', ...}]

```

1. **Cachés y memoización**:

```python
# Factorial con memoización
memo = {}
def factorial(n):
    if n in memo:  # Comprueba si ya calculamos este valor
        return memo[n]
    if n <= 1:
        return 1
    resultado = n * factorial(n-1)
    memo[n] = resultado  # Guarda el resultado para futuras llamadas
    return resultado

```