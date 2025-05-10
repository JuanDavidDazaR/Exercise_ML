# Exercise_ML

Este ejercicio consiste en el análisis y procesamiento de un conjunto de datos de una empresa de comercio electrónico con el objetivo de entrenar un modelo de aprendizaje automático que prediga si un producto es nuevo o usado.

### Metodología 

Después de realizar el EDA correspondiente se seleccionaron 13 columnas, la selección se hizo por tres método el Chi-square, matriz de correlación y adicional el PCA para la selección de columna que tenga mas relevancia para le modelo que prediga si es nuevo o usado. 

Lo siguiente de realizar este EDA, en el notebook 002_model_training, s seleccionaron 5 modelos, como el objetivo es clasificar un producto  los modelos usados fueron:

-   **Random Forest**: Ensamble de árboles de decisión que combina múltiples árboles para mejorar la precisión y reducir el sobreajuste.
-   **XGBoost**: Algoritmo de boosting basado en árboles, optimizado para velocidad y precisión, ideal para problemas complejos.
-   **Logistic Regression**: Modelo lineal simple que predice probabilidades para clasificación binaria, fácil de interpretar.
-   **Decision Tree**: Árbol de decisiones que divide los datos en ramas según reglas, intuitivo pero propenso al sobreajuste.
-   **Naive Bayes**: Clasificador probabilístico basado en el teorema de Bayes, asume independencia entre características, simple pero menos preciso en datos complejos.
-------

#### Los resultados del modelo después del entramiento:

| Modelo                  | Accuracy | Precision   | Recall      | F1-score    | Comentario principal                                                        |
|-------------------------|----------|-------------|-------------|-------------|-----------------------------------------------------------------------------|
| **Random Forest**       | 0.8635   | 0.87 / 0.85 | 0.87 / 0.85 | 0.87 / 0.85 | Mejor rendimiento general. Robusto, preciso y bien balanceado.       |
| **XGBoost**             | 0.8518   | 0.87 / 0.84 | 0.86 / 0.85 | 0.86 / 0.84 | Excelente rendimiento. Ideal si se desea un modelo optimizable y eficiente. |
| **Logistic Regression** | 0.8513   | 0.85 / 0.86 | 0.88 / 0.81 | 0.86 / 0.84 | Muy buen desempeño para un modelo simple. Bien balanceado.                  |
| **Decision Tree**       | 0.8420   | 0.86 / 0.82 | 0.84 / 0.84 | 0.85 / 0.83 | Fácil de interpretar, pero algo menos preciso. Puede sobreajustarse.        |
| **Naive Bayes**         | 0.6422   | 0.89 / 0.57 | 0.38 / 0.95 | 0.53 / 0.71 | Bajo rendimiento general. Sesgo alto hacia una clase. No recomendado.    |
----
En la evaluación de los modelos se consideraron las métricas de **Accuracy**, **Precision**, **Recall** y **F1-score**, tanto para la clase 0 como para la clase 1.
-   **Accuracy** indica el porcentaje total de predicciones correctas. Aunque útil, puede ser engañosa en presencia de clases desbalanceadas.
-   **Precision** mide cuántas de las predicciones positivas fueron realmente positivas (importante si el costo de un falso positivo es alto).
-   **Recall** evalúa cuántos de los casos positivos reales fueron correctamente identificados (relevante si los falsos negativos son costosos).
-   **F1-score** es el balance entre precision y recall, útil cuando se requiere un equilibrio entre ambas.
    
1.  **Random Forest** mostró el mejor rendimiento general, liderando en **accuracy** (86.35%) y con métricas equilibradas en ambas clases. Esto indica un modelo robusto, preciso y balanceado, capaz de generalizar bien sin sobreajuste.
2.  **XGBoost** se acercó mucho a Random Forest, con un rendimiento competitivo y f1-scores similares. Es una excelente opción si se busca un modelo más optimizable y rápido para entornos de producción.
3.  **Logistic Regression** también se desempeñó bien, destacando por su simplicidad y eficiencia. Aunque no tan potente como los anteriores, ofrece resultados comparables con menor costo computacional.
4.  **Decision Tree** es fácil de interpretar, pero mostró menor precisión y f1-score en la clase 1, lo que indica una ligera tendencia al sobreajuste y menor capacidad de generalización.
5.  **Naive Bayes** presentó un bajo desempeño general. Aunque tuvo una alta precision en la clase 0 y un recall alto en la clase 1, su desequilibrio entre clases y baja f1-score lo hacen inadecuado para este problema.
---
## Conclusiones:
Tras entrenar y evaluar cinco clasificadores — Random Forest, XGBoost, Logistic Regression, Decision Tree y Naive Bayes — podemos extraer varias conclusiones clave sobre su rendimiento y conveniencia para la tarea de predecir si un producto es **nuevo** o **usado**.

Se eligió **Random Forest** como modelo final debido a que obtuvo el mejor desempeño general en términos de precisión, recall y f1-score, superando al resto de los modelos con una exactitud del 86.3%. Este algoritmo destaca por su robustez frente al sobreajuste, su capacidad para capturar relaciones no lineales entre las variables, y su buen rendimiento sin requerir un ajuste exhaustivo de hiperparámetros. Además, maneja bien datos categóricos transformados y ofrece interpretabilidad a través de la importancia de características. 


