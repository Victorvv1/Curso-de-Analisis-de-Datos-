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

## 5 Conjuntos (Sets)

Los conjuntos son colecciones no ordenadas de elementos únicos. Se definen encerrando elementos separados por comas entre llaves.

```python
conjunto = {1, 2, 3, 4, 5}

```

### Creación de conjuntos

```python
# Conjunto vacío (no se puede usar {}, se confundiría con un diccionario)
vacio = set()

# Conjunto con elementos
numeros = {1, 2, 3, 4, 5}

# Usando la función set() con una secuencia
conjunto = set([1, 2, 2, 3, 3, 3])  # Elimina duplicados automáticamente
print(conjunto)  # {1, 2, 3}

# Mediante comprensión de conjuntos
pares = {x for x in range(10) if x % 2 == 0}
print(pares)  # {0, 2, 4, 6, 8}

```

### Operaciones con conjuntos

1. **Añadir y eliminar elementos**:

```python
conjunto = {1, 2, 3}
conjunto.add(4)  # Añade un elemento
print(conjunto)  # {1, 2, 3, 4}

conjunto.remove(2)  # Elimina un elemento (error si no existe)
print(conjunto)  # {1, 3, 4}

conjunto.discard(5)  # Elimina si existe (no error si no existe)
print(conjunto)  # {1, 3, 4}

elemento = conjunto.pop()  # Elimina y devuelve un elemento arbitrario
print(elemento)  # 1
print(conjunto)  # {3, 4}

conjunto.clear()  # Vacía el conjunto
print(conjunto)  # set()

```

1. **Operaciones de conjuntos**:

```python
a = {1, 2, 3, 4}
b = {3, 4, 5, 6}

# Unión
print(a | b)  # {1, 2, 3, 4, 5, 6}
print(a.union(b))  # {1, 2, 3, 4, 5, 6}

# Intersección
print(a & b)  # {3, 4}
print(a.intersection(b))  # {3, 4}

# Diferencia
print(a - b)  # {1, 2}
print(a.difference(b))  # {1, 2}

# Diferencia simétrica (elementos en a o b, pero no en ambos)
print(a ^ b)  # {1, 2, 5, 6}
print(a.symmetric_difference(b))  # {1, 2, 5, 6}

```

1. **Relaciones entre conjuntos**:

```python
a = {1, 2, 3}
b = {1, 2, 3, 4, 5}
c = {6, 7, 8}

# Subconjunto
print(a.issubset(b))  # True, todos los elementos de a están en b
print(a <= b)  # True

# Superconjunto
print(b.issuperset(a))  # True, b contiene todos los elementos de a
print(b >= a)  # True

# Conjuntos disjuntos (sin elementos en común)
print(a.isdisjoint(c))  # True, a y c no tienen elementos en común

```

### Aplicaciones en análisis de datos

Los conjuntos son particularmente útiles para:

1. **Eliminar duplicados**:

```python
datos = [1, 2, 2, 3, 3, 3, 4, 4, 4, 4]
datos_unicos = list(set(datos))
print(datos_unicos)  # [1, 2, 3, 4]

```

1. **Encontrar valores únicos**:

```python
lista_a = [1, 2, 3, 4, 5]
lista_b = [4, 5, 6, 7, 8]

# Elementos únicos en lista_a (no están en lista_b)
unicos_a = set(lista_a) - set(lista_b)
print(unicos_a)  # {1, 2, 3}

# Elementos únicos en lista_b (no están en lista_a)
unicos_b = set(lista_b) - set(lista_a)
print(unicos_b)  # {6, 7, 8}

# Elementos que están en una lista pero no en la otra
unicos = set(lista_a) ^ set(lista_b)
print(unicos)  # {1, 2, 3, 6, 7, 8}

```

1. **Búsqueda eficiente de pertenencia**:

```python
# Comprobar si una lista tiene valores duplicados
def tiene_duplicados(lista):
    return len(lista) != len(set(lista))

print(tiene_duplicados([1, 2, 3, 4]))  # False
print(tiene_duplicados([1, 2, 2, 3]))  # True

```

## 6. Estructuras de datos anidadas y comprensiones

### Estructuras de datos anidadas

Las estructuras de datos anidadas combinan diferentes tipos de colecciones y son fundamentales en el análisis de datos para representar información jerárquica.

```python
# Diccionario de listas
estudiantes_por_curso = {
    "Matemáticas": ["Ana", "Carlos", "Eva"],
    "Física": ["David", "Beatriz"],
    "Química": ["Fernando", "Gabriela"]
}

# Lista de diccionarios (formato JSON común)
usuarios = [
    {"id": 1, "nombre": "Ana", "email": "ana@ejemplo.com"},
    {"id": 2, "nombre": "Carlos", "email": "carlos@ejemplo.com"},
    {"id": 3, "nombre": "Eva", "email": "eva@ejemplo.com"}
]

# Diccionario de diccionarios
empleados = {
    "E001": {"nombre": "Ana", "departamento": "Ventas", "salario": 45000},
    "E002": {"nombre": "Carlos", "departamento": "IT", "salario": 52000},
    "E003": {"nombre": "Eva", "departamento": "Marketing", "salario": 48000}
}

```

### Comprensiones avanzadas

Las comprensiones pueden combinarse con estructuras anidadas para transformaciones complejas:

```python
# Filtrar empleados con salario > 50000
salarios_altos = {
    id: info for id, info in empleados.items()
    if info["salario"] > 50000
}

# Extraer nombres de estudiantes de todos los cursos
todos_estudiantes = [
    estudiante
    for curso in estudiantes_por_curso.values()
    for estudiante in curso
]

# Crear diccionario de emails a partir de lista de usuarios
emails = {
    u["nombre"]: u["email"] for u in usuarios
}

```

### Transformaciones complejas

```python
# Datos de ventas mensuales por producto
ventas = {
    "Producto A": [100, 150, 130, 120],
    "Producto B": [80, 90, 85, 95],
    "Producto C": [200, 180, 190, 210]
}

# Calcular ventas totales por producto
totales = {producto: sum(cantidades) for producto, cantidades in ventas.items()}
print(totales)  # {'Producto A': 500, 'Producto B': 350, 'Producto C': 780}

# Encontrar el mes con mayores ventas para cada producto
mejor_mes = {
    producto: cantidades.index(max(cantidades)) + 1
    for producto, cantidades in ventas.items()
}
print(mejor_mes)  # {'Producto A': 2, 'Producto B': 4, 'Producto C': 4}

# Calcular el crecimiento porcentual del primer al último mes
crecimiento = {
    producto: (cantidades[-1] - cantidades[0]) / cantidades[0] * 100
    for producto, cantidades in ventas.items()
}
print(crecimiento)  # {'Producto A': 20.0, 'Producto B': 18.75, 'Producto C': 5.0}

```

### 7.  Ejercicios
## Ejercicio 1: Análisis de Calificaciones

Utilizando lo aprendido sobre diccionarios y listas, escribe una función que analice un conjunto de calificaciones de estudiantes y devuelva:

1. El promedio de calificaciones
2. La calificación más alta y la más baja
3. Un diccionario con los estudiantes agrupados por categoría:
    - "Excelente": >=9
    - "Bueno": >=7 y <9
    - "Regular": >=6 y <7
    - "Reprobado": <6

**Datos de entrada:**

```python
calificaciones = [
    {"nombre": "Ana", "calificacion": 9.5},
    {"nombre": "Carlos", "calificacion": 8.2},
    {"nombre": "Eva", "calificacion": 7.8},
    {"nombre": "David", "calificacion": 5.9},
    {"nombre": "Beatriz", "calificacion": 6.5},
    {"nombre": "Fernando", "calificacion": 9.2},
    {"nombre": "Gabriela", "calificacion": 4.8},
    {"nombre": "Héctor", "calificacion": 7.0}
]

```

### Solución Ejercicio 1:

```python
def analizar_calificaciones(calificaciones):
    # 1. Calcular promedio
    notas = [estudiante["calificacion"] for estudiante in calificaciones]
    promedio = sum(notas) / len(notas)

    # 2. Calificación más alta y más baja
    maxima = max(notas)
    minima = min(notas)

    # 3. Agrupar por categoría
    por_categoria = {
        "Excelente": [],
        "Bueno": [],
        "Regular": [],
        "Reprobado": []
    }

    for estudiante in calificaciones:
        nota = estudiante["calificacion"]
        nombre = estudiante["nombre"]

        if nota >= 9:
            por_categoria["Excelente"].append(nombre)
        elif nota >= 7:
            por_categoria["Bueno"].append(nombre)
        elif nota >= 6:
            por_categoria["Regular"].append(nombre)
        else:
            por_categoria["Reprobado"].append(nombre)

    return {
        "promedio": round(promedio, 2),
        "maxima": maxima,
        "minima": minima,
        "por_categoria": por_categoria
    }

```

---

## Ejercicio 2: Procesamiento de Datos de Ventas

Tienes datos de ventas de productos organizados por región y trimestre. Utiliza comprensiones de listas y diccionarios para:

1. Calcular las ventas totales por producto
2. Encontrar la región con mayores ventas totales
3. Crear un ranking de productos por ventas totales

**Datos de entrada:**

```python
ventas = {
    "Norte": {
        "Q1": {"Producto A": 150, "Producto B": 120, "Producto C": 180},
        "Q2": {"Producto A": 170, "Producto B": 130, "Producto C": 190},
        "Q3": {"Producto A": 160, "Producto B": 125, "Producto C": 185},
        "Q4": {"Producto A": 180, "Producto B": 135, "Producto C": 195}
    },
    "Sur": {
        "Q1": {"Producto A": 130, "Producto B": 110, "Producto C": 160},
        "Q2": {"Producto A": 140, "Producto B": 115, "Producto C": 170},
        "Q3": {"Producto A": 135, "Producto B": 120, "Producto C": 165},
        "Q4": {"Producto A": 150, "Producto B": 125, "Producto C": 175}
    },
    "Este": {
        "Q1": {"Producto A": 160, "Producto B": 130, "Producto C": 190},
        "Q2": {"Producto A": 170, "Producto B": 140, "Producto C": 200},
        "Q3": {"Producto A": 165, "Producto B": 135, "Producto C": 195},
        "Q4": {"Producto A": 175, "Producto B": 145, "Producto C": 205}
    }
}

```

### Solución Ejercicio 2:

```python
def analizar_ventas(ventas):
    # Inicializar estructura para ventas por producto
    productos = set()
    for region in ventas.values():
        for trimestre in region.values():
            productos.update(trimestre.keys())

    ventas_por_producto = {producto: 0 for producto in productos}
    ventas_por_producto_trimestre = {producto: {"Q1": 0, "Q2": 0, "Q3": 0, "Q4": 0} for producto in productos}
    ventas_por_region = {region: 0 for region in ventas.keys()}

    # Calcular ventas totales por producto y por región
    for region, trimestres in ventas.items():
        for trimestre, productos_venta in trimestres.items():
            for producto, cantidad in productos_venta.items():
                ventas_por_producto[producto] += cantidad
                ventas_por_producto_trimestre[producto][trimestre] += cantidad
                ventas_por_region[region] += cantidad

    # 1. Ventas totales por producto
    ventas_totales = ventas_por_producto

    # 2. Trimestre con mayor venta para cada producto
    mejor_trimestre = {
        producto: max(trimestres.items(), key=lambda x: x[1])[0]
        for producto, trimestres in ventas_por_producto_trimestre.items()
    }

    # 3. Región con mayores ventas totales
    region_mayor_venta = max(ventas_por_region.items(), key=lambda x: x[1])[0]

    # 4. Ranking de productos por ventas
    ranking = sorted(ventas_por_producto.items(), key=lambda x: x[1], reverse=True)

    return {
        "ventas_totales_por_producto": ventas_totales,
        "mejor_trimestre_por_producto": mejor_trimestre,
        "region_mayor_venta": region_mayor_venta,
        "ranking_productos": ranking
    }

```

---

## Ejercicio 3: Análisis de Texto

Escribe una función que analice un texto para obtener:

1. La frecuencia de cada palabra (ignorando mayúsculas/minúsculas)
2. Las 5 palabras más comunes
3. La cantidad de palabras únicas
4. La longitud promedio de las palabras

Utiliza tuplas, listas, diccionarios y conjuntos según sea apropiado. No consideres signos de puntuación como parte de las palabras.

**Datos de entrada:**

```python
texto = """
Python es un lenguaje de programación poderoso y fácil de aprender.
Python tiene estructuras de datos eficientes y de alto nivel, y un
enfoque simple pero efectivo a la programación orientada a objetos.
La elegante sintaxis de Python y su tipado dinámico, junto con su
naturaleza interpretada, hacen de él un lenguaje ideal para scripting
y desarrollo rápido de aplicaciones en diversas áreas y en la mayoría
de las plataformas. El intérprete de Python y la extensa biblioteca
estándar están disponibles en formato fuente o binario sin costo para
todas las plataformas, y pueden distribuirse libremente.
"""

```

### Solución Ejercicio 3:

```python
def analizar_texto(texto):
    import re
    from collections import Counter

    # Convertir a minúsculas y eliminar signos de puntuación
    texto = texto.lower()
    texto = re.sub(r'[^\w\s]', '', texto)

    # Dividir en palabras
    palabras = texto.split()

    # 1. Frecuencia de cada palabra
    frecuencia = {}
    for palabra in palabras:
        if palabra in frecuencia:
            frecuencia[palabra] += 1
        else:
            frecuencia[palabra] = 1

    # 2. Las 5 palabras más comunes (usando Counter)
    contador = Counter(palabras)
    palabras_comunes = contador.most_common(5)

    # 3. Cantidad de palabras únicas
    palabras_unicas = len(set(palabras))

    # 4. Longitud promedio
    longitud_total = sum(len(palabra) for palabra in palabras)
    longitud_promedio = longitud_total / len(palabras)

    return {
        "frecuencia": frecuencia,
        "palabras_comunes": palabras_comunes,
        "palabras_unicas": palabras_unicas,
        "longitud_promedio": round(longitud_promedio, 2)
    }

```

