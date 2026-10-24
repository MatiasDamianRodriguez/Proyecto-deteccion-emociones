# KB-21: Detección de emociones faciales

Trabajo integrador de la Tecnicatura en Ciencia de Datos e IA del IFTS N.° 18 (CABA).

## Descripción

KB-21 es un estudio ficticio de videojuegos que busca analizar las emociones faciales de los jugadores durante una partida. El proyecto explora un conjunto de imágenes etiquetadas, estudia su calidad, entrena una red neuronal convolucional (CNN) y analiza sus resultados. También incluye un tablero de Power BI.

## Estructura del repositorio

```text
.
├── base_expresiones_faciales/
│   ├── DATASET/                         # Imágenes; no se incluyen en Git
│   │   ├── train/
│   │   │   └── 1/ ... 7/                # Una carpeta por clase
│   │   └── test/
│   │       └── 1/ ... 7/
│   ├── train_labels.csv
│   └── test_labels.csv
├── Codigo/
│   ├── 01_inventario.ipynb
│   ├── 02_calidad.ipynb
│   ├── 03_estadisticas.ipynb
│   ├── 04_preparacion.ipynb
│   ├── 05_cnn.ipynb
│   └── 06_hipotesis.ipynb
├── Datos/                               # Arreglos NumPy generados por el notebook 04
│   ├── X_entrenamiento.npy
│   ├── X_validacion.npy
│   ├── X_prueba.npy
│   ├── y_entrenamiento.npy
│   ├── y_validacion.npy
│   ├── y_prueba.npy
│   └── pesos_clase.npy
├── Graficos/
│   ├── 01_imagenes_por_emocion.png
│   ├── 02_histogramas_calidad.png
│   ├── 03_cajas_por_emocion.png
│   ├── 03_cara_promedio.png
│   ├── 03_correlacion_medidas.png
│   ├── 05_curvas_entrenamiento.png
│   ├── 05_matriz_confusion.png
│   └── 06_acierto_vs_calidad.png
├── Modelos/
│   └── cnn_emociones.keras
├── Resultados/
│   ├── inventario.csv
│   ├── calidad.csv
│   ├── dataset_limpio.csv
│   ├── resumen_emociones.csv
│   ├── prueba_imagenes.csv
│   ├── predicciones_prueba.csv
│   ├── metricas_emociones.csv
│   ├── matriz_confusion.csv
│   ├── acierto_por_calidad.csv
│   └── acierto_gris_color.csv
├── Tablero/
│   └── KB21.pbix
├── .gitignore
├── requirements.txt
├── Trabajo Integrador – KB-21_ detección de emociones faciales (1).docx
└── README.md
```

Los notebooks guardan sus resultados en `Datos/`, `Graficos/`, `Modelos/` y `Resultados/`. El contenido de `Datos/` se ignora en Git; puede regenerarse con el notebook 04. Las imágenes de `base_expresiones_faciales/DATASET/` también se ignoran y deben obtenerse por separado. Los CSV de etiquetas sí están incluidos.

## Dataset

El conjunto contiene 15.339 imágenes de rostros de 100 × 100 píxeles: 12.271 para entrenamiento y 3.068 para prueba. Cada partición debe tener las carpetas `1` a `7`, con las imágenes correspondientes a los archivos `train_labels.csv` y `test_labels.csv`.

| Carpeta | Emoción |
| --- | --- |
| `1` | Sorpresa |
| `2` | Miedo |
| `3` | Asco |
| `4` | Felicidad |
| `5` | Tristeza |
| `6` | Enojo |
| `7` | Neutral |


## Cómo ejecutar el proyecto

Se utilizó Python 3.10. Para volver a generar los análisis y resultados, hace falta disponer del dataset con la estructura indicada arriba.

### 1. Crear el entorno e instalar dependencias

Desde la carpeta raíz del repositorio, en PowerShell:

```powershell
py -3.10 -m venv venv
.\venv\Scripts\Activate.ps1
python -m pip install --upgrade pip
python -m pip install -r requirements.txt
```


### 2. Ejecutar los notebooks

Con el entorno activado, iniciar JupyterLab desde la raíz:

```powershell
python -m jupyter lab Codigo
```

Abrir y ejecutar las celdas de cada notebook en este orden:

1. `Codigo/01_inventario.ipynb`: verifica archivos y etiquetas; genera el inventario.
2. `Codigo/02_calidad.ipynb`: analiza la calidad y genera el dataset limpio.
3. `Codigo/03_estadisticas.ipynb`: produce estadísticas y visualizaciones descriptivas.
4. `Codigo/04_preparacion.ipynb`: prepara y separa los datos para el modelo.
5. `Codigo/05_cnn.ipynb`: entrena y evalúa la CNN; guarda el modelo y sus métricas.
6. `Codigo/06_hipotesis.ipynb`: analiza el acierto según la calidad de las imágenes.

Ejecutarlos en orden es importante porque algunos notebooks utilizan archivos producidos por los anteriores. Las rutas del proyecto están definidas en relación con la carpeta `Codigo/`; se recomienda abrir los notebooks desde ahí y no cambiar el directorio de trabajo del kernel.

### 3. Consultar los resultados

- Los CSV de `Resultados/` contienen inventarios, datos limpios, métricas y predicciones.
- `Graficos/` contiene las visualizaciones generadas durante el análisis.
- `Modelos/cnn_emociones.keras` es el modelo entrenado.
- `Datos/` contiene los arreglos de entrenamiento, validación y prueba que genera el notebook 04.
- `Tablero/KB21.pbix` se puede abrir con Power BI Desktop. Para actualizarlo después de regenerar los resultados, actualizar las fuentes CSV desde `Resultados/`.

## Alcance y hallazgos

El flujo de análisis cubre el inventario y la verificación del dataset, el análisis de calidad, las estadísticas descriptivas, la preparación de datos, el entrenamiento y la evaluación de una CNN, y el análisis de hipótesis. En el conjunto analizado se detectaron 13 imágenes inutilizables, que se excluyeron del dataset limpio. El informe del trabajo integrador documenta el contexto y las decisiones del proyecto.
