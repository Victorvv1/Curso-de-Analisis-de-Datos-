# Funciones

## 1. Introducción

Las funciones son uno de los elementos fundamentales de cualquier lenguaje de programación, y en Python son especialmente poderosas y flexibles. En el contexto del análisis de datos, las funciones nos permiten organizar, reutilizar y abstraer operaciones complejas, haciendo nuestro código más legible, mantenible y eficiente.

Este módulo explora en profundidad las funciones en Python, desde los conceptos básicos hasta técnicas avanzadas particularmente útiles en análisis de datos. Entenderemos cómo las funciones pueden transformarse en herramientas esenciales para manipular, limpiar y analizar datos de manera efectiva.

## 2. Definición y llamada de funciones

Las funciones en Python se definen utilizando la palabra clave `def`, seguida del nombre de la función y paréntesis que pueden contener los parámetros. El cuerpo de la función se escribe como un bloque indentado.

```python
def mi_funcion(x, y):
    return x + y

```

Para utilizar (llamar) una función, se escribe su nombre seguido de paréntesis con los argumentos necesarios:

```python
resultado = mi_funcion(1, 2)  # resultado será 3

```

La sentencia `return` especifica el valor que la función devuelve cuando se completa su ejecución. Si no hay una sentencia `return`, o si `return` se usa sin un valor, la función devuelve `None` por defecto:

```python
def funcion_sin_return(x):
    print(x)

resultado = funcion_sin_return("hola")  # Imprime "hola" y resultado será None

```

## 3. Argumentos de función

Python ofrece un sistema flexible para pasar argumentos a funciones.

### Argumentos posicionales y argumentos de palabra clave

Los argumentos posicionales se asignan a los parámetros de la función según el orden en que se pasan. Los argumentos de palabra clave se asignan por nombre, lo que permite especificarlos en cualquier orden:

```python
def describir_persona(nombre, edad, profesion="Estudiante"):
    return f"{nombre} tiene {edad} años y es {profesion}."

# Argumentos posicionales
print(describir_persona("Ana", 28, "Ingeniera"))

# Argumentos de palabra clave
print(describir_persona(edad=28, nombre="Ana", profesion="Ingeniera"))

# Mezclando argumentos posicionales y de palabra clave
print(describir_persona("Ana", edad=28, profesion="Ingeniera"))

# Usando el valor predeterminado para profesion
print(describir_persona("Ana", 28))

```

Los argumentos posicionales deben aparecer antes que los argumentos de palabra clave.

### Valores predeterminados

Los valores predeterminados permiten que ciertos argumentos sean opcionales:

```python
def calcular_pago(cantidad, impuesto=0.15, descuento=0):
    return cantidad * (1 - descuento) * (1 + impuesto)

# Usando todos los valores predeterminados
print(calcular_pago(100))  # 115.0

# Especificando algunos argumentos
print(calcular_pago(100, impuesto=0.10))  # 110.0
print(calcular_pago(100, descuento=0.05))  # 109.25

```

### Número variable de argumentos (*args y **kwargs)

Para funciones que necesitan aceptar un número variable de argumentos, Python ofrece las sintaxis especiales `*args` y `**kwargs`:

```python
def suma_flexible(*args, **kwargs):
    """
    Suma todos los argumentos numéricos.
    - *args recoge argumentos posicionales adicionales en una tupla
    - **kwargs recoge argumentos de palabra clave adicionales en un diccionario
    """
    total = sum(args)

    # Añadir valores del diccionario si son numéricos
    for valor in kwargs.values():
        if isinstance(valor, (int, float)):
            total += valor

    return total

# Ejemplo de uso
print(suma_flexible(1, 2, 3))  # 6
print(suma_flexible(1, 2, 3, x=4, y=5))  # 15
print(suma_flexible(1, 2, 3, x=4, y="no es un número"))  # 10

```

## 4. Espacios de nombres, ámbito y variables locales

Cuando se define una variable en Python, esta pertenece a un "espacio de nombres" o "ámbito", que determina dónde es accesible.

### Ámbito local y global

Las variables definidas dentro de una función existen solo dentro de esa función (ámbito local):

```python
def crear_lista():
    lista = []  # Variable local
    for i in range(5):
        lista.append(i)
    return lista

# La variable 'lista' solo existe dentro de la función
resultado = crear_lista()
print(resultado)  # [0, 1, 2, 3, 4]

# Intentar acceder a 'lista' fuera de la función causaría un error
# print(lista)  # NameError: name 'lista' is not defined

```

Si una función necesita modificar una variable global, debe usar la palabra clave `global`:

```python
contador = 0

def incrementar():
    global contador
    contador += 1
    return contador

print(incrementar())  # 1
print(incrementar())  # 2
print(contador)  # 2

```

### Modificación de objetos mutables

Es importante entender que, aunque no se pueda reasignar una variable global desde una función sin usar `global`, sí se pueden modificar objetos mutables (como listas o diccionarios):

```python
datos = []

def agregar_datos(valor):
    # No estamos reasignando 'datos', solo modificándola
    datos.append(valor)

agregar_datos(5)
agregar_datos(10)
print(datos)  # [5, 10]

```

En análisis de datos, esto puede ser útil para acumular resultados incrementalmente durante el procesamiento de grandes conjuntos de datos.

## 5. Retorno de múltiples valores

En Python, las funciones pueden devolver fácilmente múltiples valores utilizando tuplas:

```python
def estadisticas(numeros):
    """Calcula estadísticas básicas de una lista de números."""
    minimo = min(numeros)
    maximo = max(numeros)
    promedio = sum(numeros) / len(numeros)
    return minimo, maximo, promedio  # Devuelve una tupla

# La tupla retornada puede desempaquetarse directamente en variables
min_val, max_val, avg_val = estadisticas([1, 2, 3, 4, 5])
print(f"Mínimo: {min_val}, Máximo: {max_val}, Promedio: {avg_val}")

# También se puede asignar la tupla completa a una variable
resultado = estadisticas([1, 2, 3, 4, 5])
print(f"Resultado: {resultado}")  # Resultado: (1, 5, 3.0)

```

Una alternativa es devolver los resultados como un diccionario, lo que puede ser más descriptivo:

```python
def estadisticas_dict(numeros):
    """Calcula estadísticas básicas y las devuelve como diccionario."""
    return {
        "minimo": min(numeros),
        "maximo": max(numeros),
        "promedio": sum(numeros) / len(numeros),
        "total": sum(numeros),
        "cuenta": len(numeros)
    }

stats = estadisticas_dict([1, 2, 3, 4, 5])
print(f"Promedio: {stats['promedio']}, Total: {stats['total']}")

```

## 6. Funciones como objetos

En Python, las funciones son objetos de primera clase, lo que significa que pueden:

- Asignarse a variables
- Pasarse como argumentos a otras funciones
- Devolverse como resultado de otras funciones
- Almacenarse en estructuras de datos como listas o diccionarios

Esta característica es extremadamente poderosa para el análisis de datos, permitiendo estrategias de programación más flexibles.

### Asignación de funciones a variables

```python
def cuadrado(x):
    return x ** 2

# Asignar la función a una variable
funcion_matematica = cuadrado

# Usar la variable como una función
print(funcion_matematica(4))  # 16

```

### Funciones como argumentos

```python
def aplicar_funcion(funcion, lista):
    """Aplica una función a cada elemento de una lista."""
    return [funcion(x) for x in lista]

numeros = [1, 2, 3, 4, 5]

# Pasar una función predefinida
print(aplicar_funcion(cuadrado, numeros))  # [1, 4, 9, 16, 25]

# Pasar una función incorporada
print(aplicar_funcion(abs, [-1, -2, 3, -4, 5]))  # [1, 2, 3, 4, 5]

```

### Aplicación en limpieza de datos

Este enfoque es particularmente útil en limpieza de datos, donde podemos definir una serie de transformaciones y aplicarlas de manera consistente:

```python
import re

def eliminar_espacios(texto):
    return texto.strip()

def eliminar_puntuacion(texto):
    return re.sub(r'[^\w\s]', '', texto)

def normalizar_mayusculas(texto):
    return texto.title()

# Lista de funciones de limpieza
transformaciones = [
    eliminar_espacios,
    eliminar_puntuacion,
    normalizar_mayusculas
]

def limpiar_texto(texto, transformaciones):
    """Aplica una serie de transformaciones a un texto."""
    for transformacion in transformaciones:
        texto = transformacion(texto)
    return texto

datos_sucios = [
    "  Ejemplo con espacios  ",
    "texto!con#signos$de%puntuación",
    "TEXTO EN MAYÚSCULAS",
    "texto en minúsculas"
]

datos_limpios = [limpiar_texto(texto, transformaciones) for texto in datos_sucios]
print(datos_limpios)
# ['Ejemplo Con Espacios', 'Texto Con Signos De Puntuación', 'Texto En Mayúsculas', 'Texto En Minúsculas']

```

## 7. Funciones anónimas (lambda)

Las funciones lambda son funciones anónimas (sin nombre) de una sola expresión. Son útiles cuando necesitamos una función simple para una operación breve, especialmente como argumento para otra función.

```python
# Función normal
def cuadrado(x):
    return x ** 2

# Equivalente como lambda
cuadrado_lambda = lambda x: x ** 2

print(cuadrado(5))        # 25
print(cuadrado_lambda(5))  # 25

```

Las lambdas son particularmente útiles cuando se combinan con funciones como `map()`, `filter()` o `sorted()`:

```python
numeros = [1, 2, 3, 4, 5]

# Usando map con lambda
cuadrados = list(map(lambda x: x ** 2, numeros))
print(cuadrados)  # [1, 4, 9, 16, 25]

# Usando filter con lambda
pares = list(filter(lambda x: x % 2 == 0, numeros))
print(pares)  # [2, 4]

# Usando sorted con lambda
estudiantes = [
    {"nombre": "Ana", "nota": 85},
    {"nombre": "Carlos", "nota": 92},
    {"nombre": "Elena", "nota": 78}
]

# Ordenar por nota de mayor a menor
ordenados = sorted(estudiantes, key=lambda e: e["nota"], reverse=True)
print([e["nombre"] for e in ordenados])  # ['Carlos', 'Ana', 'Elena']

```

### Limitaciones de las lambdas

Las funciones lambda tienen limitaciones importantes:

- Solo pueden contener una expresión (no declaraciones)
- No pueden contener asignaciones o instrucciones como `return`
- No permiten documentación con docstrings

Si una función requiere lógica compleja, es mejor usar una función normal con `def`.

## 8. Generadores

Los generadores son funciones especiales que devuelven un iterador que produce una secuencia de valores. En lugar de calcular todos los valores de una vez y devolverlos en una estructura de datos como una lista, los generadores producen valores uno a uno "bajo demanda".

### Creación de generadores con yield

Se crea un generador utilizando la palabra clave `yield` en lugar de `return`:

```python
def generador_cuadrados(n):
    for i in range(1, n+1):
        yield i ** 2

# Crear un generador
gen = generador_cuadrados(5)
print(gen)  # <generator object generador_cuadrados at 0x...>

# Consumir el generador
for valor in gen:
    print(valor, end=" ")  # 1 4 9 16 25

```

La función `generador_cuadrados` no calcula todos los cuadrados de inmediato. En su lugar, la ejecución se pausa en cada `yield` y se reanuda cuando se solicita el siguiente valor.

### Ventajas de los generadores

Los generadores tienen varias ventajas para el análisis de datos:

1. **Eficiencia de memoria**: Ideal para procesar conjuntos de datos grandes que no cabrían completamente en memoria.
2. **Evaluación perezosa (lazy evaluation)**: Los valores se calculan solo cuando son necesarios.
3. **Procesamiento por lotes**: Permite procesar datos en lotes manejables.

### Ejemplo de procesamiento de archivos grandes

```python
def leer_archivo_grande(nombre_archivo, tamano_lote=1000):
    """
    Lee un archivo grande línea por línea y devuelve lotes de líneas.
    Útil para procesar archivos que no caben completamente en memoria.
    """
    lote = []
    with open(nombre_archivo, 'r') as archivo:
        for i, linea in enumerate(archivo):
            lote.append(linea.strip())

            # Cuando acumulamos suficientes líneas, devolvemos el lote
            if (i + 1) % tamano_lote == 0:
                yield lote
                lote = []

        # Devolver el último lote si no está vacío
        if lote:
            yield lote

# Uso
for i, lote in enumerate(leer_archivo_grande("datos_grandes.txt", 100)):
    print(f"Procesando lote {i+1}: {len(lote)} líneas")
    # Procesar el lote...

```

### Expresiones generadoras

Similar a las comprensiones de listas, Python permite crear generadores con una sintaxis concisa llamada "expresión generadora":

```python
# Comprensión de lista (crea toda la lista en memoria)
cuadrados_lista = [x**2 for x in range(1, 6)]
print(cuadrados_lista)  # [1, 4, 9, 16, 25]

# Expresión generadora (crea un iterador)
cuadrados_gen = (x**2 for x in range(1, 6))
print(cuadrados_gen)  # <generator object <genexpr> at 0x...>

# Consumir el generador
print(list(cuadrados_gen))  # [1, 4, 9, 16, 25]

```

Las expresiones generadoras son útiles cuando queremos aplicar transformaciones a secuencias sin crear estructuras intermedias:

```python
# Suma de cuadrados sin crear una lista intermedia
suma = sum(x**2 for x in range(1, 101))
print(suma)  # 338350

```

## 9. El módulo itertools

El módulo `itertools` de la biblioteca estándar proporciona funciones para trabajar con datos iterables de manera eficiente. Estas funciones son especialmente útiles en análisis de datos para tareas como agrupar, filtrar y combinar conjuntos de datos.

```python
import itertools
```

### Funciones clave de itertools

### groupby: Agrupar elementos consecutivos

`groupby` agrupa elementos consecutivos en un iterable según una clave:

```python
datos = [
    {"fecha": "2023-01-01", "categoria": "A", "valor": 10},
    {"fecha": "2023-01-01", "categoria": "B", "valor": 20},
    {"fecha": "2023-01-02", "categoria": "A", "valor": 15},
    {"fecha": "2023-01-02", "categoria": "B", "valor": 25}
]

# Agrupar por fecha
datos_ordenados = sorted(datos, key=lambda x: x["fecha"])
for fecha, grupo in itertools.groupby(datos_ordenados, key=lambda x: x["fecha"]):
    print(f"Fecha: {fecha}")
    total = sum(item["valor"] for item in grupo)
    print(f"  Total: {total}")

```

### chain: Combinar iterables

`chain` permite recorrer múltiples iterables como si fueran uno solo:

```python
datos_enero = [1, 2, 3]
datos_febrero = [4, 5, 6]
datos_marzo = [7, 8, 9]

# Combinar los datos de todos los meses
for valor in itertools.chain(datos_enero, datos_febrero, datos_marzo):
    print(valor, end=" ")  # 1 2 3 4 5 6 7 8 9

```

### combinations y permutations: Generar combinaciones

```python
# Generar todas las combinaciones posibles de 2 elementos
elementos = ["A", "B", "C"]
for combo in itertools.combinations(elementos, 2):
    print(combo, end=" ")  # ('A', 'B') ('A', 'C') ('B', 'C')

print()

# Generar todas las permutaciones posibles de 2 elementos
for perm in itertools.permutations(elementos, 2):
    print(perm, end=" ")  # ('A', 'B') ('A', 'C') ('B', 'A') ('B', 'C') ('C', 'A') ('C', 'B')

```

### product: Producto cartesiano

```python
# Generar todas las combinaciones de productos y tamaños
productos = ["Camiseta", "Pantalón"]
tallas = ["S", "M", "L"]
colores = ["Rojo", "Azul"]

for combinacion in itertools.product(productos, tallas, colores):
    print(combinacion)
# ('Camiseta', 'S', 'Rojo')
# ('Camiseta', 'S', 'Azul')
# ('Camiseta', 'M', 'Rojo')
# ...

```

## 10. Manejo de errores y excepciones

En análisis de datos, es común encontrar datos inesperados o problemáticos. El manejo adecuado de excepciones es crucial para crear código robusto que pueda manejar estas situaciones de manera elegante.

### Estructura básica try-except

```python
def convertir_a_numero(texto):
    try:
        return float(texto)
    except ValueError:
        return None

print(convertir_a_numero("123.45"))  # 123.45
print(convertir_a_numero("abc"))     # None

```

### Captura de excepciones específicas

Es una buena práctica capturar solo las excepciones específicas que esperamos, en lugar de todas las excepciones:

```python
def procesar_dato(valor):
    try:
        resultado = float(valor)
        return resultado
    except ValueError:
        print(f"Error: '{valor}' no es un número válido")
        return None
    except TypeError:
        print(f"Error: El tipo de dato '{type(valor).__name__}' no es válido")
        return None

print(procesar_dato("123"))    # 123.0
print(procesar_dato("abc"))    # Error: 'abc' no es un número válido, None
print(procesar_dato([1, 2]))   # Error: El tipo de dato 'list' no es válido, None

```

### Bloques try-except-else-finally

- `try`: Contiene el código que podría generar una excepción
- `except`: Se ejecuta si ocurre una excepción en el bloque try
- `else`: Se ejecuta si NO ocurre ninguna excepción en el bloque try
- `finally`: Se ejecuta SIEMPRE, independientemente de si ocurrió una excepción

```python
def procesar_archivo(nombre_archivo):
    try:
        archivo = open(nombre_archivo, 'r')
        contenido = archivo.read()
    except FileNotFoundError:
        print(f"Error: El archivo '{nombre_archivo}' no existe")
        return None
    except PermissionError:
        print(f"Error: No tienes permiso para leer '{nombre_archivo}'")
        return None
    else:
        print(f"Archivo '{nombre_archivo}' leído correctamente")
        return contenido
    finally:
        try:
            archivo.close()
            print(f"Archivo '{nombre_archivo}' cerrado")
        except NameError:
            # Si archivo nunca se abrió (por una excepción temprana)
            pass

```

### Creación de excepciones personalizadas

Para manejar situaciones específicas en análisis de datos, podemos crear nuestras propias excepciones:

```python
class ErrorDatoInvalido(Exception):
    """Excepción lanzada cuando un dato no cumple con los criterios requeridos."""
    pass

def validar_rango(valor, minimo, maximo):
    if not minimo <= valor <= maximo:
        raise ErrorDatoInvalido(f"El valor {valor} está fuera del rango permitido ({minimo}-{maximo})")
    return valor

try:
    edad = validar_rango(150, 0, 120)
except ErrorDatoInvalido as e:
    print(f"Error de validación: {e}")

```

## 4.10 Bonus. Funciones en análisis de datos: Patrones comunes

A continuación, se presentan algunos patrones comunes de uso de funciones en análisis de datos.

### Patrón 1: Función de transformación de datos

```python
def normalizar_datos(datos, minimo=None, maximo=None):
    """
    Normaliza una lista de números al rango [0, 1].
    Si no se especifican mínimo y máximo, se calculan a partir de los datos.
    """
    if not datos:
        return []

    min_valor = minimo if minimo is not None else min(datos)
    max_valor = maximo if maximo is not None else max(datos)

    rango = max_valor - min_valor
    if rango == 0:  # Evitar división por cero
        return [0.5] * len(datos)

    return [(x - min_valor) / rango for x in datos]

# Ejemplo de uso
temperaturas = [5, 10, 15, 20, 25, 30]
temperaturas_norm = normalizar_datos(temperaturas)
print(temperaturas_norm)  # [0.0, 0.2, 0.4, 0.6, 0.8, 1.0]

# Con mínimo y máximo predefinidos (útil para mantener la escala entre diferentes conjuntos)
temp_enero = [0, 5, 10, 15]
temp_febrero = [5, 10, 15, 20]
temp_enero_norm = normalizar_datos(temp_enero, 0, 30)
temp_febrero_norm = normalizar_datos(temp_febrero, 0, 30)

```

### Patrón 2: Función de agregación

```python
def resumir_por_categoria(datos, campo_categoria, campo_valor):
    """
    Agrupa y resume datos por categoría.

    Args:
        datos: Lista de diccionarios
        campo_categoria: Nombre del campo a usar como categoría
        campo_valor: Nombre del campo numérico a agregar

    Returns:
        Diccionario con estadísticas por categoría
    """
    from collections import defaultdict
    import statistics

    # Inicializar estructuras para agrupar
    por_categoria = defaultdict(list)

    # Agrupar valores por categoría
    for item in datos:
        categoria = item.get(campo_categoria)
        valor = item.get(campo_valor)
        if categoria is not None and valor is not None:
            por_categoria[categoria].append(valor)

    # Calcular estadísticas para cada categoría
    resultado = {}
    for categoria, valores in por_categoria.items():
        resultado[categoria] = {
            "count": len(valores),
            "sum": sum(valores),
            "mean": statistics.mean(valores) if valores else None,
            "median": statistics.median(valores) if valores else None,
            "min": min(valores) if valores else None,
            "max": max(valores) if valores else None
        }

    return resultado

# Ejemplo
ventas = [
    {"producto": "A", "region": "Norte", "ventas": 100},
    {"producto": "B", "region": "Norte", "ventas": 150},
    {"producto": "A", "region": "Sur", "ventas": 200},
    {"producto": "B", "region": "Sur", "ventas": 120},
]

resumen_por_producto = resumir_por_categoria(ventas, "producto", "ventas")
for producto, stats in resumen_por_producto.items():
    print(f"Producto {producto}: {stats['count']} ventas, total: {stats['sum']}, promedio: {stats['mean']}")

```

### Patrón 3: Función de filtrado con criterios variables

```python
def filtrar_datos(datos, **criterios):
    """
    Filtra una lista de diccionarios según múltiples criterios.

    Args:
        datos: Lista de diccionarios
        **criterios: Pares clave-valor donde la clave es el campo y el valor es el valor a filtrar

    Returns:
        Lista filtrada de diccionarios
    """
    resultado = datos

    for campo, valor in criterios.items():
        # Permitir funciones como criterios (para filtros complejos)
        if callable(valor):
            resultado = [item for item in resultado if campo in item and valor(item[campo])]
        else:
            resultado = [item for item in resultado if campo in item and item[campo] == valor]

    return resultado

# Ejemplo
empleados = [
    {"id": 1, "nombre": "Ana", "edad": 28, "departamento": "Ventas", "salario": 45000},
    {"id": 2, "nombre": "Carlos", "edad": 35, "departamento": "IT", "salario": 52000},
    {"id": 3, "nombre": "Elena", "edad": 24, "departamento": "IT", "salario": 48000},
    {"id": 4, "nombre": "David", "edad": 41, "departamento": "Ventas", "salario": 60000},
]

# Filtro simple por departamento
it_staff = filtrar_datos(empleados, departamento="IT")
print("Personal de IT:")
for emp in it_staff:
    print(f"  {emp['nombre']}, {emp['edad']} años, ${emp['salario']}")

# Filtro con función (personas con salario mayor a 50000)
altos_salarios = filtrar_datos(empleados, salario=lambda x: x > 50000)
print("\nEmpleados con salario alto:")
for emp in altos_salarios:
    print(f"  {emp['nombre']}, ${emp['salario']}")

```

### Patrón 4: Función de aplicación en cascada

```python
def aplicar_transformaciones(datos, transformaciones):
    """
    Aplica una serie de transformaciones en cadena a un conjunto de datos.

    Args:
        datos: Los datos a transformar
        transformaciones: Lista de funciones a aplicar en orden

    Returns:
        Datos transformados
    """
    resultado = datos
    for transformacion in transformaciones:
        resultado = transformacion(resultado)
    return resultado

# Funciones de transformación
def remover_nulos(datos):
    return [x for x in datos if x is not None]

def convertir_a_entero(datos):
    return [int(x) if isinstance(x, (int, float)) else x for x in datos]

def duplicar_valores(datos):
    return [x * 2 for x in datos]

# Aplicar transformaciones en cascada
datos_crudos = [1, 2, None, 3.5, 4, None, 5]
pipeline = [remover_nulos, convertir_a_entero, duplicar_valores]
resultado = aplicar_transformaciones(datos_crudos, pipeline)
print(resultado)  # [2, 4, 6, 8, 10]

```
