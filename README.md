# Grupo 3 — Evento Evaluativo 2: Análisis de Datos

Proyecto de la asignatura **Análisis de Datos** (Instituto Tecnológico Metropolitano, docente Daniel Alexis Nieto Mora, semestre 2026-2).

## Integrantes

| Nombre | Usuario de GitHub |
|---|---|
| Santiago Betancur | @Xantyagoh |
| Diego Alzate | @DiegoA1123 |
| Carlos Mendez | @carmarisx |
| Sebastian Cadavid | @Exmen9 |
| Daniel Martinez | @danielmmnez |

## Descripción del proyecto

Este repositorio documenta las tres fases pedidas en el Evento Evaluativo 2:

1. **Exploración de bases de datos**: se exploraron 3 datasets de distinto tipo (tabular, imágenes, texto) y se justificó la selección de la base final.
2. **Análisis Exploratorio de Datos (EDA)**: sobre el dataset seleccionado (Titanic), se realizó revisión de valores faltantes, detección de atípicos, análisis de distribuciones, análisis univariado y multivariado, formulación y prueba de hipótesis, y un listado de insights.
3. **Preprocesamiento y reducción de dimensionalidad**: limpieza e imputación, transformación logarítmica de `fare`, codificación de variables categóricas, escalado/normalización y reducción de dimensionalidad con PCA (con scree plot) y t-SNE.

## Dataset seleccionado

**Titanic** (pasajeros del RMS Titanic, 1912), fuente secundaria cargada vía `seaborn.load_dataset('titanic')`. Ver la justificación completa de por qué se eligió sobre los otros dos datasets explorados en [`notebooks/01_exploracion_datasets.ipynb`](notebooks/01_exploracion_datasets.ipynb).

## Estructura del repositorio

```
.
├── README.md
├── requirements.txt
├── .gitignore
├── notebooks/
│   ├── 01_exploracion_datasets.ipynb   # Fase 1: exploración y selección de la base de datos
│   ├── 02_eda.ipynb                    # Fase 2: EDA completo + pruebas de hipótesis
│   └── 03_preprocesamiento.ipynb       # Fase 3: codificación, escalado y PCA
```

## Cómo ejecutar

```bash
python -m venv venv
source venv/bin/activate        # En Windows: venv\Scripts\activate
pip install -r requirements.txt
jupyter notebook notebooks/
```

Los tres notebooks son independientes entre sí en cuanto a carga de datos (cada uno vuelve a cargar lo que necesita), pero deben leerse en orden: `01` → `02` → `03`.

## Principales hallazgos (detalle en `02_eda.ipynb` y `03_preprocesamiento.ipynb`)

- Solo sobrevivió el ~38% de los pasajeros: la clase objetivo está desbalanceada.
- El sexo es el factor más asociado con la supervivencia (chi-cuadrado p ≈ 0, V de Cramér ≈ 0.54, efecto fuerte).
- Clase y sexo interactúan: las mujeres de 1ª clase sobrevivieron en un ~97%, las de 3ª solo en un ~50%, y los hombres de 2ª en un ~16%.
- La edad no es un buen predictor por sí sola: no es normal (Shapiro-Wilk), y con Mann-Whitney la diferencia entre grupos no es significativa (p ≈ 0.16, d de Cohen ≈ −0.16).
- `fare` tiene un sesgo fuerte (≈ 4.79) que la transformación log(1+x) reduce a ≈ 0.39.
- `deck` tiene ~77% de faltantes y se eliminó; `age` (~20%) se imputó con la mediana.
- Con las 9 variables estandarizadas, PC1 + PC2 explican ~43.6% de la varianza y se necesitan unas 5 componentes para llegar al 80%. Ni PCA ni t-SNE separan con claridad a sobrevivientes de no sobrevivientes.

## Video explicativo

Enlace al video (máx. 8 minutos): _pendiente — agregar enlace aquí antes de la entrega final_.

## Aporte de cada integrante

| Integrante | Aporte |
|---|---|
| Santiago Betancur | Estructura del repositorio y `01_exploracion_datasets.ipynb`: carga y exploración de Titanic, Digits y SMS Spam. Revisión y fusión de los Pull Requests. |
| Diego Alzate | Fase 1: tabla comparativa y selección del dataset. Fase 2: valores faltantes, valores atípicos y transformación logarítmica de `fare`. |
| Carlos Mendez | Fase 2: distribuciones, análisis univariado y multivariado, patrones combinados de clase y sexo, y formulación de hipótesis. |
| Sebastian Cadavid | Fase 2: pruebas de hipótesis (supuestos, Mann-Whitney y tamaño del efecto) e insights. Fase 3: limpieza y codificación de variables. |
| Daniel Martinez | Fase 3: escalado, PCA (con scree plot), t-SNE y comparación. Sección de principales hallazgos del README. |

## Nota sobre el uso de herramientas de IA

Usamos IA como apoyo para estructurar el código y algunos textos de los notebooks. Todo el código lo ejecutamos y revisamos nosotros, y al revisarlo corregimos cosas que estaban mal o incompletas. Las decisiones del análisis las tomamos y discutimos en el equipo.

- **Santiago:** revisé los Pull Requests del equipo antes de fusionarlos.
- **Diego:** al revisar `fare` vi que tenía un sesgo muy fuerte y apliqué la transformación logarítmica para reducirlo.
- **Carlos:** completé el análisis univariado con las variables que faltaban (`embarked`, `sibsp`, `parch`) y agregué los patrones combinados de clase y sexo.
- **Sebastian:** al revisar las pruebas de hipótesis agregué los supuestos de normalidad y el tamaño del efecto, y dejé H2 como no concluyente.
- **Daniel:** corregí el escalado del PCA para estandarizar las 9 variables y reescribí su interpretación.
