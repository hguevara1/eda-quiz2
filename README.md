# Análisis Exploratorio de Datos (EDA) - Costos Médicos Personales

Este notebook presenta un Análisis Exploratorio de Datos (EDA) sobre un conjunto de datos de costos médicos personales, con el objetivo de entender la distribución de las variables, identificar relaciones clave y detectar patrones o anomalías.

## 📊 Fuente de Datos

Los datos provienen del dataset [Medical Cost Personal Datasets](https://www.kaggle.com/datasets/mirichoi0218/insurance) de Kaggle.

## 🚀 Configuración y Descarga de Datos

El notebook incluye pasos para configurar la autenticación de Kaggle API en Google Colab, descargar el archivo `insurance.zip` y descomprimirlo para obtener `insurance.csv`.

## 📝 Descripción del Dataset

El dataset contiene información personal y médica de beneficiarios de seguros de salud con las siguientes columnas:

*   **`age`**: Edad del beneficiario principal.
*   **`sex`**: Género del contratista ('female' o 'male').
*   **`bmi`**: Índice de Masa Corporal (IMC).
*   **`children`**: Número de hijos o dependientes cubiertos por el seguro.
*   **`smoker`**: Indica si la persona es fumadora ('yes' o 'no').
*   **`region`**: Zona residencial en EE. UU. ('northeast', 'southeast', 'southwest', 'northwest').
*   **`charges`**: Costos médicos individuales facturados en dólares.

## 🔍 Análisis Inicial del DataFrame

### Estadísticas Generales

*   **Número de Filas**: 1338 registros iniciales.
*   **Número de Columnas**: 7 variables.
*   **Tipos de Datos**: Las variables incluyen enteros (`age`, `children`), flotantes (`bmi`, `charges`) y objetos/cadenas de texto (`sex`, `smoker`, `region`).

### Estadísticas Descriptivas (Numéricas)

| Variable | Media   | Mediana | Desv. Est. | Mínimo | Máximo  |
| :------- | :------ | :------ | :--------- | :----- | :------ |
| `age`    | 39.21   | 39.00   | 14.05      | 18.00  | 64.00   |
| `bmi`    | 30.66   | 30.40   | 6.10       | 15.96  | 53.13   |
| `children` | 1.09    | 1.00    | 1.21       | 0.00   | 5.00    |
| `charges`  | 13270.42| 9382.03 | 12110.01   | 1121.87| 63770.43|

*   Se observa que `charges` tiene una media significativamente mayor que su mediana, indicando una distribución asimétrica positiva (sesgada a la derecha) con posibles valores atípicos altos.

### Calidad de Datos

*   **Valores Nulos**: No se encontraron valores nulos en ninguna columna, lo que simplifica el preprocesamiento.
*   **Registros Duplicados**: Se detectó y eliminó **1 fila duplicada**. El DataFrame final contiene 1337 registros únicos.
*   **Consistencia de Variables Categóricas**: Se verificó la unicidad y consistencia de los valores en `sex`, `smoker` y `region`, confirmando que no hay errores tipográficos o inconsistencias.

## 📈 Visualización y Análisis Exploratorio de Datos

### Histogramas de Variables Numéricas

*   **`age`**: Distribución relativamente uniforme, con concentraciones en edades jóvenes y medias.
*   **`bmi`**: Distribución cercana a la normal, ligeramente sesgada a la derecha, con la mayoría en el rango de sobrepeso/obesidad.
*   **`charges`**: Distribución altamente asimétrica positiva, indicando que la mayoría de los costos son bajos, pero hay una cola de valores muy altos.

### Box Plots para Outliers

*   **`bmi`**: Muestra varios valores atípicos, especialmente en el rango superior, indicando casos de obesidad severa.
*   **`charges`**: Confirma la presencia de numerosos valores atípicos en el extremo superior, lo que resalta la alta variabilidad en los costos médicos y la existencia de casos con gastos excepcionalmente elevados.

### Matriz de Correlación (Heatmap)

*   La correlación más fuerte entre las variables numéricas y los `charges` es con la **`age`** (aproximadamente 0.30).
*   El **`bmi`** muestra una correlación positiva débil con los `charges` (aproximadamente 0.20).
*   El **`children`** tiene una correlación muy débil (aproximadamente 0.07).

### Gráfico de Dispersión: Edad vs. Cargos Médicos (Diferenciado por Fumador)

*   Este gráfico es crucial para entender el impacto combinado de `age` y `smoker` en los `charges`.
*   **No Fumadores**: Muestran una correlación positiva moderada entre `age` y `charges`, con costos que aumentan gradualmente con la edad.
*   **Fumadores**: Los costos médicos son **consistentemente y significativamente más altos** para los fumadores en todas las edades, en comparación con los no fumadores. El estado de fumador es un **factor dominante** y un predictor mucho más fuerte de los gastos de salud que la edad o el IMC.

## 🎯 Conclusión del EDA

El análisis exploratorio de datos revela que el factor más influyente en los costos médicos es el **estado de fumador**, superando a la edad y el IMC. Aunque la edad y el IMC muestran correlaciones positivas con los cargos, el ser fumador actúa como un multiplicador masivo de estos costos. El dataset está limpio, sin valores nulos y con una única fila duplicada eliminada, listo para un modelado predictivo o análisis más profundos.
