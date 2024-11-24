# SmartAthletics
Este proyecto se centra en el análisis de datos de rendimiento atlético, utilizando técnicas de apredizaje automático para clasificar diferentes tipos de entrenamientos basados en métricas de actividad física.

Pregunta de investigación: ¿Es posible obtener un clasificador capaz de predecir el tipo de beneficio físico percibido por un individuo tras la práctica de una actividad de atletismo con una precisión del 80% desde los datos de un reloj inteligente con GPS integrado?

## Tabla de Contenidos
* Tecnologías Utilizadas
* Pasos Principales
* Arquitectura
* Resultados

## Tecnologías Utilizadas:
  ### Librerías y versiones 
  * Python v3.11.2
  * NumPy v1.26.4
  * Pandas v2.2.3
  * Seaborn v0.12.2
  * Datetime v3.11.2 
  * Scikit-learn v1.4.2
  * XGBoost v2.0.1
  * Matplotlib v3.7.2

## Pasos Principales
Recolección de Datos: Se recopilaron datos de rendimiento atlético a través de dispositivos de seguimiento.
Preprocesamiento de Datos: Los datos fueron limpiados y normalizados para asegurar su calidad.
Entrenamiento del Modelo: Se entrenaron varios modelos utilizando algoritmos como Regresión Logística, SVM, KNN, Random Forest y XGBoost.
Evaluación: Se evaluaron los modelos utilizando la métrica de precisión (Accuracy).

## Arquitectura
La arquitectura del proyecto incluye:
Los datos fluyen desde la recolección hasta el preprocesamiento, seguido del entrenamiento del modelo y finalmente la evaluación.

### Componentes Clave:
Recolección de Datos: Reloj inteligente con GPS integrado.
Preprocesamiento: Limpieza, normalización y coficación de variables categóricas utilizando Pandas y sklearn.
Modelos: LogisticRegression, SVM, KNN, Random Forest, XGBoost para clasificación.

## Resultados
### Tabla de Parámetros XGBoost

| Parámetro         | Valor |
|--------------------|-------|
| max_depth          | 3     |
| n_estimators       | 50    |
| learning_rate      | 0.1   |
| colsample_bytree   | 0.5   |
| reg_lambda         | 0     |
| gamma              | 0.3   |

### Tabla de Resultados de Modelos

| Modelo                     | Precisión (Entrenamiento) | Precisión (Validación) |
|----------------------------|---------------------------|-------------------------|
| RandomForestClassifier      | 1.0                       | 0.7586                  |
| LogisticRegression          | 0.6507                    | 0.6552                  |
| KNeighborsClassifier        | 0.7031                    | 0.6379                  |
| SVC                        | 0.6638                    | 0.6897                  |
| XGBoost                    | 0.9956                    | 0.7931                  |

La precisión promedio de los modelos en LOOCV es de: 0.6933
La precisión del modelo sobre datos de prueba es de: 0.9333

Dada la limitada muestra de datos, tanto en cantidad como el hecho de pertenecer a un mismo individuo, las métricas alcanzadas en el modelo no fueron las esperadas ni fueron consistentes sobre los diferentes conjuntos de entrenamiento, validación y prueba. En los datos recopilados, existe un desbalance en las etiquetas de la variable objetivo, lo que hacía que las clases minoritarias tuvieran muy pocas observaciones en el conjunto de entrenamiento y por ende se obtiene una generalización limitada en estas clases.
 
A partir de la optimización del mejor modelo y los resultados de precisión en entrenamiento y validación, se evidenció un sobreajuste de los algoritmos empleados, se buscó reducir el sesgo al utilizar métodos de ensamble en serie basados en árboles (boosting), permitiendo reducir el sobreajuste en cierta medida. 

Para mejorar la generalización del algoritmo se espera obtener datos de diversos individuos, lo que aumente la cantidad de datos, especialmente en las etiquetas minoritarias; se busca además clasificar a los individuos por su nivel de condición física y objetivos para crear modelos ajustados a ciertos arquetipos de entrenamiento, logrando así una mayor precisión en la clasificación.



