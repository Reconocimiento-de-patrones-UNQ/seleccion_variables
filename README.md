
# Selección de Variables: Estrategias contra el Ruido

Este repositorio contiene el material de la **Clase 2** de la materia **Reconocimiento de Patrones en Bioinformática**. Tras haber explorado la "maldición de la dimensionalidad" en la Clase 1, en esta sesión nos enfocamos en técnicas críticas para identificar y conservar únicamente las variables que aportan señal biológica real.

### Objetivos

  * **Taxonomía de Selección:** Diferenciar entre métodos de **Filtros**, **Wrappers** y **Embedded**.
  * **Control de Errores:** Aplicar filtros univariados con corrección por testeo múltiple (**FDR/Benjamini-Hochberg**) para gestionar falsos positivos.
  * **Interacciones Multivariadas:** Implementar algoritmos como **RFE** (Recursive Feature Elimination) para capturar la sinergia entre variables.
  * **Regularización e Importancia:** Utilizar modelos de **Lasso** (penalización L1) e importancias de **Random Forest** para selección integrada.
  * **Robustez y Estabilidad:** Evaluar la persistencia de las variables seleccionadas mediante técnicas de **Bootstrap**.
  * **Integridad Metodológica:** Identificar y prevenir el **Data Leakage**, asegurando que la selección ocurra estrictamente dentro de la validación cruzada.

-----

### Estructura del Repositorio

  * [**`Clase2_Seleccion_de_Variables.ipynb`**](https://colab.research.google.com/drive/1nBim8KbIPLNGH2pYK93Ck8O9zfKM1wb0): Notebook práctico que simula un experimento de microarrays (60 pacientes, 4000 genes) para aplicar los métodos discutidos.
  * **`bibliografia_clase2.md`**: Compendio de lecturas fundamentales, incluyendo el review de Saeys et al. (2007) y capítulos clave de *The Elements of Statistical Learning*.

-----

### Cómo ejecutar el material

Para asegurar un ambiente de trabajo estable y con todas las dependencias bioinformáticas listas, sigue estas instrucciones:

#### Opción A: Google Colab (Recomendado)

### Abrir el notebook utilizando el enlace citado a continuación para aprovechar el entorno de Google Colab preconfigurado con todas las dependencias necesarias:

[**`Clase2_Seleccion_de_Variables.ipynb`**](https://colab.research.google.com/drive/1nBim8KbIPLNGH2pYK93Ck8O9zfKM1wb0)

#### Opción B: Ejecución Local

Si prefieres trabajar localmente, asegúrate de tener instalado el stack científico estándar:

``` bash
pip install numpy pandas matplotlib seaborn scikit-learn scipy statsmodels

```

-----

### Nota Pedagógica

Este repositorio está diseñado para la experimentación activa. Siguiendo la metodología de la clase, **no se incluyen las soluciones** de los 5 ejercicios prácticos para fomentar el análisis crítico y la discusión de resultados entre los alumnos.
