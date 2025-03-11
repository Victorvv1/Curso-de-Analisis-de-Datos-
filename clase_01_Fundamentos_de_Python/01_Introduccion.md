## 1. Python para Análisis de datos

Bienvenidos al curso de Python para Análisis de Datos. Este curso se centra en los aspectos prácticos de manipular, procesar, limpiar y analizar datos utilizando Python y su potente ecosistema de bibliotecas.

El análisis de datos se ha convertido en una habilidad fundamental en numerosos campos profesionales. En la última década, Python ha emergido como una de las herramientas más potentes y versátiles para esta tarea, transformándose de un lenguaje de vanguardia científica a uno de los pilares fundamentales de la ciencia de datos, el aprendizaje automático y el desarrollo de software en general.

Este curso no se enfoca en metodologías abstractas de análisis, sino en proporcionar las habilidades de programación concretas que necesitarás para convertirte en un analista de datos efectivo. Te equiparemos con el conocimiento práctico de Python y sus bibliotecas especializadas que te permitirán manejar diversos tipos de datos estructurados, incluyendo:

- Datos tabulares (similares a hojas de cálculo)
- Arrays multidimensionales (matrices)
- Tablas relacionadas mediante columnas clave
- Series temporales (uniformes o irregulares)

¿Por qué Python para análisis de datos? Python ofrece ventajas significativas:

1. **Versatilidad**: Funciona como un "elemento de unión" que puede integrar código de otros lenguajes y conectar diferentes sistemas y tecnologías.
2. **Resolución del "problema de los dos lenguajes"**: Elimina la necesidad de usar un lenguaje para investigación/prototipado y otro para producción. Con Python, puedes desarrollar todo el ciclo de vida de un proyecto de datos.
3. **Rico ecosistema**: Bibliotecas como pandas, NumPy, scikit-learn y matplotlib ofrecen herramientas especializadas que han convertido a Python en la opción preferida para tareas analíticas.

Aunque Python tiene algunas limitaciones (es interpretado y por tanto más lento que los lenguajes compilados, y tiene restricciones para aplicaciones altamente concurrentes debido al GIL), sus beneficios en términos de productividad y flexibilidad lo compensan ampliamente para la mayoría de las aplicaciones de análisis de datos.

En este curso, aprenderás a utilizar Python como una herramienta completa para el ciclo de análisis de datos: desde la importación y limpieza inicial hasta la visualización y modelado. Al finalizar, estarás preparado para utilizar estas habilidades en proyectos reales y para profundizar en áreas más especializadas como el aprendizaje automático o la ciencia de datos avanzada.

## 2. Librerías esenciales de Python

El ecosistema de Python para ciencia de datos se compone de varias bibliotecas fundamentales que trabajan en conjunto para proporcionar un entorno completo de análisis. Estas bibliotecas son las piezas clave que han convertido a Python en una herramienta tan poderosa para el trabajo con datos:

- **NumPy**: La piedra angular de la computación numérica en Python. Ofrece:NumPy no solo acelera el procesamiento de datos, sino que también sirve como contenedor estándar para pasar datos entre diferentes algoritmos y bibliotecas, permitiendo que código escrito en lenguajes de bajo nivel como C o FORTRAN trabaje con estos datos sin necesidad de copias adicionales.
    - El objeto `ndarray`: una estructura de datos multidimensional, rápida y eficiente para cálculos numéricos
    - Funciones para realizar operaciones matemáticas vectorizadas
    - Herramientas para lectura/escritura de datos basados en arrays
    - Operaciones de álgebra lineal, transformadas de Fourier y generación de números aleatorios
    - Una API de C bien desarrollada que facilita la interoperabilidad
- **pandas**: Creada inicialmente por Wes McKinney en 2008 mientras trabajaba en AQR Capital Management, esta biblioteca proporciona estructuras de datos de alto nivel y funciones diseñadas para facilitar el trabajo con datos estructurados. Sus principales componentes son:pandas combina la potencia computacional de NumPy con funcionalidades similares a las hojas de cálculo y bases de datos relacionales. Características clave incluyen:
    - `DataFrame`: estructura tabular bidimensional con etiquetas en filas y columnas
    - `Series`: objeto unidimensional similar a un array pero con etiquetas
    - Estructuras con ejes etiquetados que permiten alineación automática de datos
    - Funcionalidad integrada para series temporales
    - Manejo flexible de datos faltantes
    - Operaciones de unión y otras operaciones relacionales (similares a SQL)
- **matplotlib**: La biblioteca de visualización más establecida para Python, creada por John D. Hunter. Aunque existen otras alternativas, matplotlib sigue siendo ampliamente utilizada por:
    - Su capacidad para producir gráficos de calidad para publicaciones
    - Su buena integración con el resto del ecosistema de Python
    - Su amplitud de opciones para personalización de visualizaciones
- **IPython y Jupyter**: Desarrollado inicialmente por Fernando Pérez en 2001 como un mejor intérprete interactivo de Python, este proyecto evolucionó significativamente:
    - IPython promueve un flujo de trabajo de exploración interactiva ideal para análisis de datos
    - Proporciona acceso integrado al sistema operativo, facilitando tareas comunes
    - En 2014, evolucionó al proyecto Jupyter, que amplió la funcionalidad a más de 40 lenguajes de programación
    - Jupyter Notebook permite crear documentos que combinan código ejecutable, visualizaciones y texto narrativo
- **SciPy**: Una colección de paquetes que resuelven problemas fundamentales en ciencia computacional:
    - `scipy.integrate`: Rutinas de integración numérica
    - `scipy.linalg`: Álgebra lineal avanzada
    - `scipy.optimize`: Optimización de funciones
    - `scipy.signal`: Procesamiento de señales
    - `scipy.sparse`: Matrices dispersas
    - `scipy.stats`: Distribuciones de probabilidad y tests estadísticos
- **scikit-learn**: Desarrollada desde 2007, se ha convertido en la principal biblioteca de aprendizaje automático para Python, con módulos para:scikit-learn está más orientada a la predicción y aplicación práctica de algoritmos.
    - Clasificación (SVM, bosques aleatorios, regresión logística)
    - Regresión (Lasso, Ridge)
    - Clustering (k-means, agrupamiento espectral)
    - Reducción de dimensionalidad (PCA, selección de características)
    - Evaluación y selección de modelos
    - Preprocesamiento de datos
- **statsmodels**: Biblioteca enfocada en estadística inferencial y econometría, que incluye:A diferencia de scikit-learn, statsmodels pone mayor énfasis en la inferencia estadística, proporcionando estimaciones de incertidumbre y valores p para los parámetros.
    - Modelos de regresión (lineal, generalizada, robusta)
    - Análisis de varianza (ANOVA)
    - Análisis de series temporales (ARIMA, VAR)
    - Métodos no paramétricos
    - Visualización de resultados estadísticos

Estas bibliotecas forman el núcleo del ecosistema de Python para análisis de datos, aunque el panorama continúa expandiéndose con proyectos como TensorFlow, PyTorch y muchas otras herramientas especializadas.

## 3 . Instalación y configuración

La instalación de un entorno adecuado para análisis de datos con Python requiere configurar correctamente tanto Python como sus diversas bibliotecas. Se recomienda utilizar Miniconda, una instalación mínima del gestor de paquetes conda, junto con conda-forge, una distribución de software mantenida por la comunidad. Esta configuración proporciona un entorno flexible y reproducible que funciona en múltiples sistemas operativos.

**Proceso de instalación por sistema operativo:**

**Windows:**

- Descargar el instalador de Miniconda para la versión más reciente de Python desde conda.io (generalmente la versión de 64 bits)
- Durante la instalación, decidir si se quiere añadir Miniconda al PATH del sistema:
    - Si se añade, esta instalación podría sobreescribir otras versiones de Python existentes
    - Si no se añade, será necesario utilizar el acceso directo específico del menú de inicio
- Para verificar la instalación, abrir "Anaconda Prompt (Miniconda3)" desde el menú inicio y ejecutar el comando `python`

**GNU/Linux:**

- Descargar el instalador de Miniconda apropiado para la arquitectura del sistema (típicamente x86_64)
- Ejecutar el script de instalación con el comando `bash Miniconda3-latest-Linux-x86_64.sh`
- Se recomienda instalar en la ubicación predeterminada del directorio de inicio
- Durante la instalación, es recomendable permitir la modificación de los scripts del shell para activar automáticamente Miniconda
- Verificar la instalación abriendo un nuevo terminal y ejecutando `python`

**macOS:**

- Descargar el instalador apropiado:
    - Para computadoras con Apple Silicon (2020 en adelante): Miniconda3-latest-MacOSX-arm64.sh
    - Para Macs con Intel (anteriores a 2020): Miniconda3-latest-MacOSX-x86_64.sh
- Instalar ejecutando `bash $HOME/Downloads/Miniconda3-latest-MacOSX-[arquitectura].sh`
- Se recomienda permitir que el instalador modifique el perfil del shell
- Verificar la instalación abriendo un nuevo terminal y ejecutando `python`

**Configuración del entorno de análisis de datos:**

Una vez instalado Miniconda, el proceso para configurar el entorno de trabajo es similar en todos los sistemas operativos:

1. **Configurar conda-forge como canal predeterminado:**
    
    ```bash
    
    conda config --add channels conda-forge
    conda config --set channel_priority strict
    
    ```
    
2. **Crear un entorno dedicado para análisis de datos:**Es importante recordar que este entorno debe activarse en cada nueva sesión de terminal con `conda activate pydata-book`.
    
    ```bash
    
    conda create -y -n pydata-book python=3.10
    conda activate pydata-book
    
    ```
    
3. **Instalar los paquetes esenciales:**
    
    ```bash
    
    conda install -y pandas jupyter matplotlib
    
    ```
    
4. **Instalar paquetes adicionales según sea necesario:** Existen dos métodos principales para instalar paquetes:Para instalar todos los paquetes utilizados en el libro:
    - `conda install`: método preferido cuando el paquete está disponible
    - `pip install`: alternativa cuando un paquete no está disponible a través de conda
    
    ```bash
    
    conda install lxml beautifulsoup4 html5lib openpyxl requests sqlalchemy seaborn scipy statsmodels patsy scikit-learn pyarrow pytables numba
    
    ```
    
5. **Actualizar paquetes cuando sea necesario:**Es recomendable no mezclar los métodos de actualización (es decir, no actualizar con pip lo instalado con conda y viceversa).
    - Con conda: `conda update nombre_paquete`
    - Con pip: `pip install --upgrade nombre_paquete`

**Entornos de desarrollo:**

Para el trabajo de análisis de datos, existen varias opciones de entornos de desarrollo:

- **IPython/Jupyter Notebook**: Especialmente útil para exploración interactiva y visualización de datos
- **Editores de texto avanzados**: VS Code, Sublime Text (con soporte para Python)
- **IDEs especializados**:
    - PyDev (gratuito, integrado en Eclipse)
    - PyCharm (comercial, con versión gratuita para desarrolladores de código abierto)
    - Python Tools for Visual Studio (para usuarios de Windows)
    - Spyder (gratuito, incluido con Anaconda)
    - Komodo IDE (comercial)

La elección del entorno de desarrollo depende de las preferencias personales y del tipo de trabajo que se realice. Para exploración de datos y prototipado, Jupyter Notebook ofrece grandes ventajas, mientras que para desarrollo de software más estructurado, un IDE puede proporcionar herramientas adicionales valiosas.