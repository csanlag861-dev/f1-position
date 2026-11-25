# 🏎️ F1 Race Position Predictor

Proyecto de Machine Learning desarrollado con Python para predecir la posición final de un piloto en una carrera de Fórmula 1 a partir de diferentes características previas a la competición.

El objetivo es estudiar la relación entre la posición de salida, el circuito y la escudería, y analizar hasta qué punto un modelo de regresión puede estimar el resultado final de un piloto.

## 🎯 Objetivo del proyecto

Desarrollar y evaluar diferentes modelos de Machine Learning capaces de predecir la posición final de un piloto en una carrera de Fórmula 1.

Para ello, se utilizan datos históricos de carreras y se comparan distintos algoritmos de regresión, evaluando su rendimiento mediante métricas como MAE, RMSE y R².

## 📊 Dataset

Los datos utilizados proceden de **Ergast Formula One Database**, distribuidos a través del proyecto TidyTuesday.

- **Fuente:** [TidyTuesday – Formula 1 Races (07/09/2021)](https://github.com/rfordatascience/tidytuesday/tree/main/data/2021/2021-09-07)
- **Origen de los datos:** Ergast API.
- **Formato:** archivos CSV con información histórica de Fórmula 1.

Se utilizan datos relacionados con los resultados de las carreras, los circuitos y las escuderías.

## ⚙️ Variables del modelo

El modelo utiliza las siguientes variables predictoras:

| Variable | Descripción | Tipo |
|---|---|---|
| `grid_aj` | Posición de salida ajustada | Numérica |
| `circuito` | Circuito donde se disputa la carrera | Categórica |
| `escuderia` | Escudería del piloto | Categórica |

**Variable objetivo:**

- `pos_final`: posición final del piloto en la carrera.

### Preparación de los datos

Durante el proceso de preparación se realizan diferentes transformaciones:

1. Selección de los pilotos clasificados en la carrera.
2. Creación de la variable `pos_final` a partir de la posición oficial.
3. Ajuste de la posición de salida (`grid_aj`), tratando los casos en los que un piloto comienza desde el pit lane.
4. Selección de las variables predictoras.
5. Codificación de las variables categóricas mediante **One-Hot Encoding**.
6. División de los datos en conjuntos de entrenamiento y prueba.

## 🤖 Modelos de Machine Learning

Se han implementado y comparado diferentes algoritmos de regresión:

- Regresión lineal (*Linear Regression*).
- Gradient Boosting Regressor.
- Random Forest Regressor.
- Random Forest Regressor ajustado.
- K-Nearest Neighbors Regressor (KNN).
- Decision Tree Regressor.

También se han utilizado dos referencias (*baseline*) para contextualizar los resultados:

- Predecir que la posición final será igual a la posición de salida.
- Predecir la posición media del conjunto de entrenamiento.

## 📈 Evaluación de los modelos

Para evaluar el rendimiento se utilizan tres métricas:

- **MAE (Mean Absolute Error):** mide el error absoluto medio entre las posiciones reales y las predichas.
- **RMSE (Root Mean Squared Error):** penaliza especialmente los errores de predicción más grandes.
- **R² (Coeficiente de determinación):** mide la capacidad del modelo para explicar la variabilidad de la variable objetivo.

### Resultados de la comparativa

Resultados obtenidos durante la validación cruzada:

| Modelo | RMSE CV | MAE CV | R² CV |
|---|---:|---:|---:|
| Regresión lineal | 2.994 | **2.285** | **0.652** |
| Gradient Boosting | **2.994** | 2.301 | **0.652** |
| Random Forest ajustado | 3.069 | 2.326 | 0.635 |
| Random Forest | 3.233 | 2.427 | 0.595 |
| KNN Regressor | 3.371 | 2.539 | 0.559 |
| Árbol de decisión | 3.881 | 2.897 | 0.417 |
| Posición final = parrilla | 4.180 | 3.002 | 0.327 |
| Posición media | 5.096 | 4.362 | -0.004 |

### Interpretación

La **Regresión lineal** obtiene el mejor MAE, con un error absoluto medio de aproximadamente 2.29 posiciones. Gradient Boosting presenta un rendimiento muy similar, con el mismo RMSE y R².

Estos resultados muestran que, para las variables seleccionadas, los modelos de regresión lineal y Gradient Boosting ofrecen las mejores estimaciones de posición final dentro de los algoritmos evaluados.

## 🔍 Análisis de predicciones

Además de comparar las métricas, se analizan las predicciones del conjunto de prueba mediante diferentes visualizaciones:

- Comparación entre posiciones reales y predichas.
- Distribución de los errores de predicción.
- Error absoluto medio según el tramo de la parrilla de salida.

También se realizan simulaciones con escenarios hipotéticos para comprobar cómo cambian las predicciones según la posición de salida, el circuito y la escudería.

## 🛠️ Tecnologías utilizadas

- **Python:** lenguaje de programación.
- **Pandas:** manipulación y análisis de datos.
- **NumPy:** operaciones numéricas.
- **Scikit-learn:** preparación de datos, entrenamiento y evaluación de modelos.
- **Jupyter Notebook / Google Colab:** entorno de desarrollo y experimentación.

## ▶️ Ejecución del proyecto

1. Clona este repositorio:

   ```bash
   git clone <URL_DEL_REPOSITORIO>
   ```

2. Accede al directorio:

   ```bash
   cd <NOMBRE_DEL_REPOSITORIO>
   ```

3. Instala las dependencias necesarias:

   ```bash
   pip install pandas numpy scikit-learn matplotlib seaborn jupyter
   ```

4. Abre el notebook de Jupyter o Google Colab y ejecuta las celdas en orden.

> Nota: ajusta las dependencias a las librerías que finalmente utilice el notebook.

## 🎥 Vídeo explicativo

En el siguiente vídeo se presenta el proyecto, su objetivo, el proceso de preparación de los datos, los algoritmos utilizados y la interpretación de los resultados obtenidos.

📺 **Ver presentación del proyecto en YouTube:**

[Enlace al vídeo de YouTube](https://youtu.be/sd-HiqqbqEs)

## 👨‍💻 Autor

Proyecto desarrollado como parte del aprendizaje práctico de Machine Learning y análisis de datos aplicado al mundo de la Fórmula 1.
