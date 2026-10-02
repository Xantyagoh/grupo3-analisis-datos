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
3. **Preprocesamiento y reducción de dimensionalidad**: codificación de variables categóricas, escalado/normalización y reducción de dimensionalidad con PCA.

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

## Video explicativo

Enlace al video (máx. 8 minutos): _pendiente — agregar enlace aquí antes de la entrega final_.

## Flujo de trabajo en equipo (GitHub)

Para que los commits reflejen la participación real de cada integrante:

1. Cada integrante trabaja sobre su propia rama (`git checkout -b nombre/fase1-exploracion`, por ejemplo) y abre un Pull Request hacia `main` cuando termina su parte.
2. Cada quien hace commits de su propio trabajo, con su usuario y correo de GitHub configurados (`git config user.name` / `user.email`), en vez de que una sola persona suba todo el código del equipo.
3. Mensajes de commit descriptivos, por ejemplo: `fase2: agrega boxplots de outliers en age y fare`, no `update` o `cambios`.
4. Se recomienda que cada integrante sea responsable principal de al menos una fase/notebook, pero que revise y comente el trabajo de los demás (vía Pull Request) para que la organización y trazabilidad en GitHub (criterio de la rúbrica) quede clara.

## Nota sobre el uso de herramientas de IA

Este proyecto usó IA como apoyo para estructurar el código y los notebooks. La rúbrica del evento evalúa explícitamente la **autenticidad y conciencia del trabajo**: antes de grabar el video, cada integrante debe ejecutar el código, revisar los resultados con sus propios datos (pueden variar ligeramente según la versión de las librerías) y estar en capacidad de explicar con sus palabras cada decisión tomada (por qué se imputó así, por qué se escogió ese dataset, qué significa cada gráfica).
