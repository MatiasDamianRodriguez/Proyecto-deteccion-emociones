# KB-21: Detección de emociones faciales

Trabajo integrador de la Tecnicatura en Ciencia de Datos e IA, IFTS N° 18 (CABA).

## Descripción

KB-21 es un estudio independiente de videojuegos (empresa ficticia). En las sesiones de prueba con jugadores, el estudio depende de encuestas posteriores, que suelen ser imprecisas. Este proyecto propone un modelo que detecte automáticamente la emoción en la cara del jugador durante la partida, para saber si el juego genera las emociones que busca el equipo de diseño.

## Estado del proyecto

**Preentrega.** Están terminados:

- **Notebook 01:** inventario y verificación del dataset.
- **Notebook 02:** análisis de calidad de las imágenes y limpieza.

Quedan pendientes las estadísticas descriptivas, la visualización de patrones, los modelos predictivos y el tablero de Power BI.

## Estructura del repositorio

├── base_expresiones_faciales/
│   ├── DATASET/              (no incluido, ver sección Dataset)
│   ├── train_labels.csv
│   └── test_labels.csv
├── Codigo/
│   ├── 01_inventario.ipynb
│   └── 02_calidad.ipynb
├── Graficos/                 (gráficos generados por los notebooks)
├── Resultados/               (archivos CSV para Power BI y para los modelos)
├── Modelos/                  (modelos entrenados, próximamente)
├── requirements.txt
└── README.md

## Dataset

Las imágenes **no están incluidas en el repositorio**.

- **Contenido:** 15.339 fotos de rostros de 100×100 píxeles, divididas en `train` (12.271) y `test` (3.068), cada una con 7 carpetas numeradas. 1 = Sorpresa, 2 = Miedo, 3 = Asco, 4 = Felicidad, 5 = Tristeza, 6 = Enojo, 7 = Neutral.

Para ejecutar los notebooks, la carpeta del dataset debe quedar en esta ubicación:

```
base_expresiones_faciales/DATASET/train/1 ... 7
base_expresiones_faciales/DATASET/test/1 ... 7
```

## Cómo ejecutar el proyecto

Requiere Python 3.10.
Colocar el dataset en `base_expresiones_faciales/DATASET/`, como se indica arriba.
instalar las librerías y entorno:
   ```
   python -m venv venv
   venv\Scripts\activate
   pip install -r requirements.txt
   ```
   Ejecutar:
   1. `Codigo/01_inventario.ipynb`
   2. `Codigo/02_calidad.ipynb`

## Resultados principales hasta ahora

- Las 15.339 imágenes se abren correctamente y coinciden al 100% con los archivos de etiquetas.
- Las clases están muy desbalanceadas: felicidad tiene 16,8 veces más imágenes que miedo.
- Se eliminaron 13 imágenes inutilizables (sin contraste, muy borrosas o demasiado oscuras). El dataset limpio tiene 15.326 imágenes.

El detalle de cada decisión está en el documento del trabajo.