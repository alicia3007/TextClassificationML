# Clasificación de Décadas Históricas en Español mediante Machine Learning y Transformers

## Descripción del Proyecto

Este proyecto aborda el problema de clasificación automática de textos históricos en español, cuyo objetivo consiste en predecir la década de origen de un documento a partir de su contenido textual.

La solución combina técnicas tradicionales de Machine Learning basadas en TF-IDF con modelos modernos de Deep Learning utilizando Transformers, explorando diferentes estrategias de representación textual, validación y ensamble de modelos.

El trabajo fue desarrollado en el contexto de competencias de Machine Learning sobre clasificación histórica y se centró tanto en el rendimiento predictivo como en la capacidad de generalización de los modelos.

---

## Objetivos

* Clasificar automáticamente documentos históricos por década.
* Comparar enfoques tradicionales y modelos Transformer.
* Diseñar representaciones textuales capaces de capturar señales lingüísticas temporales.
* Reducir el sobreajuste y mejorar la capacidad de generalización.
* Evaluar diferentes estrategias de validación y ensamble.

---

## Tecnologías Utilizadas

### Lenguaje

* Python

### Ciencia de Datos

* Pandas
* NumPy
* SciPy

### Machine Learning

* Scikit-Learn
* Logistic Regression
* Linear SVM
* SGD Classifier
* Voting Classifier

### Deep Learning y NLP

* PyTorch
* Hugging Face Transformers
* RoBERTa-BNE
* BERTIN

### Entorno de Desarrollo

* Jupyter Notebook
* Kaggle

---

## Metodología

### 1. Análisis Exploratorio y Preprocesamiento

Se realizó una limpieza mínima del texto con el fin de preservar señales históricas relevantes.

Entre las transformaciones aplicadas se incluyen:

* Eliminación de boilerplate proveniente de Google Books.
* Corrección de palabras fragmentadas por OCR.
* Eliminación de duplicados.
* Conservación de rasgos ortográficos históricos.

Una conclusión importante del proyecto fue que una limpieza excesiva elimina información temporal valiosa para la clasificación.

---

## Representación del Texto

La representación textual se construyó mediante una combinación de cuatro vectorizadores TF-IDF:

* Character n-grams cortos.
* Character n-grams largos.
* Character n-grams sin límites de palabra.
* Word n-grams.

Estas representaciones fueron integradas mediante FeatureUnion con pesos diferenciados para capturar simultáneamente:

* Patrones ortográficos históricos.
* Variaciones morfológicas.
* Estructuras léxicas.
* Información semántica.

---

## GlobalSpecialistClassifier

Uno de los principales aportes del proyecto fue el diseño de una arquitectura jerárquica propia denominada:

### GlobalSpecialistClassifier

El sistema opera en dos niveles:

#### Modelo Global

Realiza una primera predicción sobre todas las décadas disponibles.

#### Modelos Especialistas

Una vez realizada la predicción global, un clasificador especializado refina la decisión dentro de bloques de décadas cercanas.

Esta estrategia permite reducir errores entre periodos históricos similares y mejorar la precisión final del sistema.

---

## Ensamble de Modelos

Los clasificadores tradicionales se combinaron mediante un VotingClassifier compuesto por:

* Logistic Regression
* Linear SVM
* SGD Classifier

El objetivo fue aprovechar fortalezas complementarias de cada modelo y aumentar la robustez de las predicciones.

---

## Validación y Prevención de Data Leakage

Durante el desarrollo se identificó que múltiples textos provenían del mismo libro histórico.

Utilizar una validación tradicional basada en StratifiedKFold producía una sobreestimación artificial del desempeño debido a la presencia simultánea de fragmentos del mismo libro en entrenamiento y validación.

Para solucionar este problema se implementó:

### GroupKFold

Esta estrategia garantiza que fragmentos pertenecientes al mismo documento permanezcan en el mismo fold, proporcionando una estimación mucho más realista de la capacidad de generalización.

---

## Modelos Transformer

Además de los modelos basados en TF-IDF, se evaluaron arquitecturas Transformer especializadas para español.

### RoBERTa-BNE

Modelo desarrollado por la Biblioteca Nacional de España y entrenado sobre grandes colecciones de textos históricos en español.

### BERTIN

Utilizado como modelo alternativo para comparación y respaldo experimental.

Los modelos fueron ajustados mediante fine-tuning sobre el conjunto de entrenamiento.

---

## Resultados

Los experimentos permitieron comparar:

* Modelos clásicos basados en TF-IDF.
* Arquitecturas Transformer.
* Estrategias jerárquicas de clasificación.
* Diferentes esquemas de validación.

Los resultados mostraron que:

* Los n-gramas de caracteres contienen una fuerte señal temporal.
* El clasificador jerárquico mejora la discriminación entre décadas cercanas.
* GroupKFold proporciona una estimación más confiable que StratifiedKFold.
* RoBERTa-BNE logra una mejor comprensión semántica de textos históricos en español.

---

## Competencias de Kaggle

Este proyecto fue utilizado en competencias de Kaggle relacionadas con clasificación histórica.

Durante el proceso se desarrollaron estrategias de:

* Optimización de modelos.
* Generación de submissions.
* Validación robusta.
* Comparación sistemática de enfoques.

---

## Habilidades Aplicadas

* Machine Learning Supervisado
* Natural Language Processing (NLP)
* Feature Engineering
* TF-IDF Vectorization
* Ensemble Learning
* Model Validation
* GroupKFold Cross Validation
* Deep Learning
* Transformers
* Fine-Tuning
* Data Science
* Kaggle Competitions
