# **Proyecto de Visualización: Análisis de Perfiles de riesgo para la diabetes**

Este repositorio contiene el trabajo realizado para la Práctica 2 de la asignatura "Visualización de Datos" del Máster en Ciencia de Datos. El proyecto explora el dataset "*CDC Diabetes Health Indicators*" para identificar perfiles de riesgo en la población y analizar su relación con la prevalencia de la diabetes, con un foco especial en el impacto de la salud mental.

## **🚀 Visualización Interactiva**

El resultado final de este análisis es un dashboard interactivo desarrollado en Tableau. Se pueden explorar los resultados aquí:

[**▶️ Acceder al Dashboard Interactivo en Tableau Public**](https://public.tableau.com/views/Perfilesderiesgoparaladiabetesfinal/Caracterizacindeperfiles?:language=es-ES&:sid&:redirect=auth&:display_count=n&:origin=viz_share_link)

## **1. Selección del Dataset (Resumen PR1)**

El conjunto de datos seleccionado fue el **"CDC Diabetes Health Indicators"** del repositorio de la UCI. La elección se justificó por varios motivos clave:

* **Relevancia temática:** La diabetes es un desafío sanitario de primer orden. El enfoque del proyecto busca explorar no solo los factores de riesgo físicos, sino también la conexión con la salud mental, un ángulo a menudo subestimado.  
* **Complejidad y riqueza:** Con más de 250,000 registros y 21 variables iniciales, el dataset ofrece una base estadística robusta. Combina indicadores binarios, ordinales y cuantitativos, permitiendo un análisis multidimensional.  
* **Originalidad:** El objetivo no era predecir la diabetes, sino ir un paso más allá: segmentar a la población en perfiles de riesgo comprensibles mediante técnicas de clustering, ofreciendo un enfoque exploratorio y novedoso.

La pregunta de investigación principal que guió el proyecto fue: **¿Es posible identificar perfiles de riesgo que combinen factores de salud (especialmente mental), socioeconómicos y de comportamiento, y cómo se asocian estos perfiles con la diabetes?**

## **2. Proceso de análisis y visualización (PR2)**

El trabajo se dividió en dos fases principales: un análisis y preprocesamiento de datos en Python, y la construcción de la visualización interactiva en Tableau.

### **2.1. Análisis y preparación en Python (*Jupyter Notebook*)**

El *notebook* `PR2 - Proyecto de visualizacion.ipynb` detalla el siguiente flujo de trabajo:

1. **Análisis Exploratorio de Datos (EDA):**  
   * Se validó la integridad del dataset, confirmando la ausencia de valores nulos.  
   * Se analizaron las distribuciones de variables clave, identificando el desbalance de la variable objetivo (`Diabetes_binary`) y la fuerte asimetría en las variables de salud mental y física.  
   * Se descubrió que aunque la correlación lineal entre `MentHlth` (salud mental) y la diabetes era baja, los *boxplots* mostraban una clara diferencia en la distribución, sugiriendo una relación más compleja.  
2. **Ingeniería de características:**  
   * Para enriquecer el análisis, se crearon dos índices sintéticos:  
     * `score_habitos_saludables`: Una suma simple de indicadores binarios (actividad física, consumo de frutas y verduras) para obtener un score de 0 a 3\.  
     * `indice_riesgo_cardio`: Una suma de los valores estandarizados (con *RobustScaler*) de **HighBP, HighChol** y **BMI** para crear un indicador de riesgo cardiovascular combinado.  
3. ***Clustering*** **no supervisado:**  
   * Se utilizó el algoritmo **K-Means** para segmentar a la población en grupos homogéneos.  
   * Mediante el "método del codo" se determinó que **k=3** era el número óptimo de clústeres, ofreciendo el mejor equilibrio entre detalle e interpretabilidad.  
   * Se generó la variable final cluster, que asigna a cada individuo a uno de los tres perfiles identificados.

El resultado de esta fase fue un archivo CSV enriquecido (`cdc_diabetes_health_indicators_clustered.csv`), que sirvió como fuente de datos para Tableau.

### **2.2. Visualización interactiva en Tableau**

El dashboard público se compone de dos paneles principales:

* **Dashboard 1: Caracterización de Perfiles:** Permite entender la "personalidad" de cada uno de los 3 clústeres. Muestra los valores promedio de los índices de riesgo y hábitos, y una tabla interactiva para explorar en detalle otras métricas como la salud mental, la edad o los ingresos.  
* **Dashboard 2: Análisis de la diabetes por perfil:** Responde a la pregunta de investigación principal. Incluye un gráfico de barras con la prevalencia de diabetes en cada perfil, un scatter plot que valida visualmente la segmentación, y boxplots interactivos para un análisis más profundo.

## **3. Conclusiones y hallazgos principales**

El análisis y la visualización permitieron extraer conclusiones significativas:

1. **Se identificaron 3 perfiles de riesgo claros y distintos:**  
   * **Perfil 1 - "Saludable y consciente":** Bajo riesgo cardiovascular y excelentes hábitos de vida. Presentan la prevalencia de diabetes más baja (12%).  
   * **Perfil 2 - "Alto riesgo cardiovascular":** El grupo de mayor edad y con el índice de riesgo cardiovascular más alto. A pesar de tener hábitos moderados su prevalencia de diabetes es la más alta (27%).  
   * **Perfil 3 - "Hábitos precarios":** Grupo definido por un bajo *score* de hábitos y la peor salud mental y física. Presentan una alta prevalencia de diabetes (21%).  
2. **El rol de la salud mental es específico de un perfil:** El análisis demostró que los problemas de salud mental no son un factor generalizado, sino el rasgo definitorio del **"Perfil de Hábitos Precarios" donde el malestar es crónico** independientemente de si el individuo tiene diabetes o no.  
3. **La segmentación es más potente que el análisis univariado:** El enfoque de clustering permitió descubrir relaciones complejas que un análisis variable por variable no hubiera revelado.

## **🛠️ Herramientas Utilizadas**

* **Lenguaje:** Python 3.x  
* **Librerías Principales:** Pandas, Scikit-learn, Matplotlib, Seaborn  
* **Entorno:** Jupyter Notebook  
* **Herramienta de Visualización:** Tableau Public