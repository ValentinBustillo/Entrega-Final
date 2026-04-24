# Entrega Final - Videojuegos de PlayStation

## Descripción del proyecto

Este trabajo es una continuación de la primera entrega, donde había analizado un catálogo de videojuegos de PlayStation.

En esta entrega volví a usar el mismo dataset, pero ahora agregué una parte de Machine Learning. La idea fue ver si, además de analizar los datos, se podía hacer una predicción simple: saber si un videojuego pertenece o no al género **Action role-playing**.

Para eso usé algunas variables del dataset, principalmente el desarrollador y la empresa editora.

## Objetivo

El objetivo del trabajo fue aplicar algunos modelos de Machine Learning sobre los datos trabajados en la primera entrega.

Los pasos principales fueron:

1. Descargar los datos desde una API.
2. Guardarlos en un archivo CSV.
3. Limpiar un poco los datos.
4. Hacer un análisis exploratorio básico.
5. Crear una variable para saber si el juego es Action RPG o no.
6. Entrenar modelos de clasificación.
7. Comparar los resultados.

## Fuente de datos

Los datos fueron obtenidos desde la API pública de SampleAPIs:

`https://api.sampleapis.com/playstation/games`

La API no requiere usuario ni API Key.

En el notebook, los datos se descargan y después se guardan en este archivo:

`data/videojuegos_playstation.csv`

Luego el trabajo se realiza usando ese CSV.

## Preguntas del trabajo

Algunas preguntas que se intentan responder son:

1. ¿Cuáles son los géneros más frecuentes?
2. ¿Qué desarrolladores aparecen más veces?
3. ¿Qué empresas editoras tienen más juegos publicados?
4. ¿Se puede predecir si un videojuego es Action RPG usando el desarrollador y la empresa editora?

## Problema de Machine Learning

El problema se planteó como una clasificación binaria.

La variable objetivo es `is_action_rpg`:

- `1`: el juego es del género Action role-playing.
- `0`: el juego pertenece a otro género.

La idea fue probar si el modelo podía aprender algún patrón usando las variables disponibles.

## Limpieza de datos

El dataset tenía algunas columnas con formato de lista, por ejemplo los géneros, desarrolladores y empresas editoras.

Por eso hice una limpieza básica:

- Convertí esos datos para poder usarlos mejor.
- Eliminé filas que no tenían género.
- Creé columnas más simples para género, desarrollador y empresa editora.
- Creé la variable `is_action_rpg`.
- Agrupé valores poco frecuentes como `Other`.
- Convertí las variables de texto a números usando encoding.

## Análisis exploratorio

En el análisis exploratorio revisé principalmente los géneros más comunes y la cantidad de juegos Action RPG comparados con el resto.

También se vio que hay muchos más juegos de otros géneros que juegos Action RPG. Esto hace que el dataset esté desbalanceado, y eso puede afectar los modelos.

## Modelos usados

Usé dos modelos:

- Regresión Logística
- Random Forest

La Regresión Logística la usé como modelo más simple, y Random Forest para comparar con un modelo un poco más avanzado.

## Evaluación

Para evaluar los modelos usé:

- Separación entre entrenamiento y testeo.
- Accuracy.
- Classification report.
- Validación cruzada.
- GridSearchCV para probar algunos parámetros.

## Resultados

El modelo logra hacer una primera aproximación, pero no funciona perfecto.

El accuracy puede dar alto, pero eso pasa en parte porque la mayoría de los juegos no son Action RPG. Entonces el modelo tiende a predecir mejor la clase mayoritaria.

Por eso, el resultado sirve como una primera prueba, pero habría que mejorar el dataset para lograr un modelo más fuerte.

## Conclusión

Con este trabajo pude pasar de un análisis exploratorio a un problema de Machine Learning.

Se pudo ver que variables como el desarrollador y la empresa editora pueden aportar información, aunque el dataset tiene limitaciones.

Una mejora posible sería agregar más columnas, como ventas, rating, año de lanzamiento o plataforma. Con más información, el modelo podría mejorar.

## Herramientas usadas

El proyecto fue realizado en Python usando:

- pandas
- requests
- matplotlib
- scikit-learn
- os

## Requisitos

Para ejecutar el notebook se pueden instalar las librerías necesarias con:

```bash
pip install pandas requests matplotlib scikit-learn
```

## Cómo ejecutar el proyecto

1. Abrir el notebook.
2. Ejecutar las celdas en orden.
3. El notebook descarga los datos desde la API.
4. Se genera el archivo `data/videojuegos_playstation.csv`.
5. Después se realiza la limpieza, el análisis y los modelos.

## Archivos

- `proyecto_ml_playstation_storytelling_final.ipynb`
- `data/videojuegos_playstation.csv`
- `README.md`
