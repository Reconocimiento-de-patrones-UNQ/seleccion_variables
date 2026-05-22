# Bibliografía — Clase 2: Selección de variables

**Maestría en Bioinformática y Biología de Sistemas — UNQ**
**Reconocimiento de Patrones en Bioinformática**

---

## Lectura previa recomendada (30 min)

- **Saeys, Y., Inza, I. & Larrañaga, P. (2007).** *A review of feature selection techniques in bioinformatics.* **Bioinformatics, 23(19), 2507–2517.** El review canónico del tema en bioinformática. Aún hoy es la referencia obligada.
  - DOI: 10.1093/bioinformatics/btm344

- **Capítulo 18 de "The Elements of Statistical Learning"** (Hastie, Tibshirani, Friedman), sección 18.4 — *Univariate Filtering and the FDR*.
  - PDF gratuito: https://hastie.su.domains/ElemStatLearn/

---

## Profundización por tema

### Filtros y testeo múltiple (repaso de Clase 1)

- **Storey, J. D. & Tibshirani, R. (2003).** *Statistical significance for genomewide studies.* PNAS 100(16), 9440–9445. Introduce el concepto de q-value, una alternativa al BH.

### Wrappers y RFE

- **Guyon, I. et al. (2002).** *Gene Selection for Cancer Classification using Support Vector Machines.* Machine Learning, 46, 389–422. El paper original de SVM-RFE en bioinformática.

### Métodos embedded

- **Tibshirani, R. (1996).** *Regression shrinkage and selection via the lasso.* JRSS-B, 58(1), 267–288. El paper original de Lasso. Vale leer la introducción.

- **Friedman, J., Hastie, T. & Tibshirani, R. (2010).** *Regularization Paths for Generalized Linear Models via Coordinate Descent.* Journal of Statistical Software 33(1). El paper de implementación de `glmnet`, referencia técnica.

### Estabilidad

- **Meinshausen, N. & Bühlmann, P. (2010).** *Stability selection.* JRSS-B, 72(4), 417–473. Formaliza el bootstrap de selección que vimos en clase. Lectura técnica pero importante.

---

## Videos recomendados (verificados)

- **StatQuest — Regularization Part 2: Lasso (L1) Regression** (~9 min)
  https://www.youtube.com/watch?v=NGf0voTMlcs
  Explicación visual de por qué Lasso selecciona variables.

- **StatQuest — Ridge vs Lasso Regression, Visualized!!!** (~9 min)
  https://www.youtube.com/watch?v=Xm2C_gTAl8c
  La intuición geométrica L1 vs L2 (relevante para Clase 4 también).

- **StatQuest — Random Forests Part 1: Building, Using and Evaluating** (~10 min)
  https://www.youtube.com/watch?v=J4Wdy0Wc_xQ
  Repaso de RF y su importancia de variables (de Minería de Datos).

---

## Recursos técnicos

### Documentación de scikit-learn

- Feature selection: https://scikit-learn.org/stable/modules/feature_selection.html
- `SelectKBest`: https://scikit-learn.org/stable/modules/generated/sklearn.feature_selection.SelectKBest.html
- `RFE`: https://scikit-learn.org/stable/modules/generated/sklearn.feature_selection.RFE.html

### statsmodels para correcciones múltiples

- `multipletests`: https://www.statsmodels.org/dev/generated/statsmodels.stats.multitest.multipletests.html

### Paquetes especializados

- **Boruta** (selección basada en RF + sombras): https://github.com/scikit-learn-contrib/boruta_py
- **mlxtend** (más wrappers, incluyendo SequentialFeatureSelector): http://rasbt.github.io/mlxtend/

---

## FAQ pedagógico

**1. ¿Cuándo conviene filtros vs embedded?**
- Filtros: cuando tenés muchísimas variables ($p > 10^5$) y querés reducir rápido antes de aplicar algo más complejo.
- Embedded: cuando $p$ es moderado y querés un modelo final.

**2. ¿Cómo elegir el umbral de FDR?**
- 0.05 es el estándar. Para descubrimiento exploratorio puede usarse 0.10. Por debajo de 0.01 sólo si necesitás alta especificidad (ej: clínica).

**3. ¿Bonferroni o BH?**
- Bonferroni controla FWER (probabilidad de **algún** falso positivo). Demasiado estricto en bioinformática.
- BH controla FDR (proporción de falsos positivos entre los rechazados). Estándar moderno.

**4. ¿Cómo encajar la selección en cross-validation?**
- La selección debe ir **dentro** del CV, NO antes. Si filtrás genes sobre todo el dataset y después hacés CV, el test ya "vio" los genes — eso es leakage. Se discute en profundidad en Clase 6.

**5. ¿Por qué Lasso selecciona arbitrariamente entre variables correlacionadas?**
- La penalización L1 tiende a poner el coeficiente en UNA sola de un grupo correlacionado. Cuál: depende del orden numérico del solver. Por eso Elastic Net (Clase 4) es más robusto para grupos.
