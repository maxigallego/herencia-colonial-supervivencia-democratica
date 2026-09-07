# Herencia Colonial y Supervivencia Democrática

Trabajo final de la materia **Ciencia de Datos para Economía y Negocios**, Maestría en Economía Aplicada — Universidad de Buenos Aires, Facultad de Ciencias Económicas.

## Pregunta de investigación

¿En qué medida la identidad del imperio colonizador y la duración del dominio colonial influyen sobre el tiempo hasta la democratización y sobre la supervivencia posterior de los regímenes democráticos?

El análisis distingue dos momentos críticos de las sociedades poscoloniales:

- **Etapa A:** tiempo transcurrido desde la independencia hasta la primera democratización.
- **Etapa B:** supervivencia de los regímenes democráticos una vez establecidos, y riesgo de quiebre autoritario.

## Datos

El análisis integra cuatro fuentes:

- **V-Dem** (Varieties of Democracy) — tipo de régimen político y momentos de democratización.
- **ERT** (Episodes of Regime Transformation) — episodios de autocratización y quiebres democráticos.
- **COLDAT** (Colonial Dates Dataset) — colonizador principal y duración del dominio colonial.
- **QoG** (Quality of Government) — variables de control (antigüedad estatal precolonial, área territorial, producción de petróleo).

Cobertura temporal: 1900–2025. Los colonizadores se agrupan en cuatro categorías: **Británico**, **Francés**, **Ibérico** (España y Portugal) y **Otro europeo** (Bélgica, Alemania, Italia, Países Bajos).

## Metodología

**Two-Part Survival Model**, complementado con otras estrategias de estimación para triangular resultados:

- **Validación del agrupamiento colonial:** PCA + K-Means, comparado contra las categorías históricas con el Índice Rand Ajustado (ARI).
- **Etapa A:** curvas de supervivencia de Kaplan-Meier y test de Log-Rank por colonizador.
- **Etapa B:** modelo de Cox (episodio único), modelo de Andersen-Gill (episodios recurrentes) y Logit de tiempo discreto (BKT) sobre panel país-año.
- **Calidad democrática contemporánea:** Logit Fraccional (Papke y Wooldridge) y Elastic Net para verificar robustez frente a multicolinealidad.
- **Predicción de la primera democratización:** comparación de Regresión Logística + Elastic Net, Random Forest y SVM (kernel RBF) mediante validación cruzada y AUC-ROC.

## Principales hallazgos

- Las excolonias **británicas** democratizaron más rápido tras la independencia y sostienen niveles más altos de calidad democrática, con tendencia de mejora en el tiempo.
- Las excolonias **ibéricas** tardaron sistemáticamente más en democratizarse y, una vez alcanzada la democracia, muestran mayor riesgo de quiebre (odds hasta ~13,5 veces mayor que el legado británico) junto con una tendencia de deterioro.
- El legado **francés** ocupa una posición intermedia: no se diferencia claramente del británico en el ritmo de mejora, pero sí en el nivel promedio alcanzado, con riesgo de quiebre sistemáticamente mayor al británico.
- El modelo predictivo (Elastic Net) alcanza un AUC-ROC de 0,761 al anticipar la primera democratización a partir de características coloniales y estructurales.
- El análisis es **asociacional, no causal**: sin un instrumento que aísle la asignación del colonizador, no puede descartarse que factores previos a la colonización expliquen parte de la asociación observada.

## Contenido del repositorio

| Archivo | Descripción |
|---|---|
| `Informe_Final_Ciencia_de_Datos.pdf` | Informe final con metodología completa, resultados y bibliografía. |
| `Herencia_Colonial_Supervivencia_Democratica.ipynb` | Notebook con el procesamiento de datos, modelos y visualizaciones. |

## Herramientas

Python — `pandas`, `lifelines` (Kaplan-Meier, Cox, Andersen-Gill), `scikit-learn` (K-Means, PCA, Elastic Net, Random Forest, SVM), `statsmodels` (Logit Fraccional).

## Autores

- Maximiliano Gallego
- Luciana Loria
