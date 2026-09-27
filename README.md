# Proyecto de Visualización 3D de Lesiones en Fondo de Ojo

## Descripción

Este proyecto corresponde a una prueba de concepto para la visualización tridimensional de lesiones identificadas en imágenes de fondo de ojo.

El objetivo es tomar una imagen de fondo de ojo y una máscara de segmentación de una lesión, convertir la región identificada por la máscara en un mapa de altura y representar dicha información como un relieve tridimensional interactivo.

La visualización permite explorar la superficie mediante rotación y zoom, además de modificar la altura del relieve para facilitar la observación de las regiones segmentadas.

El proyecto utiliza imágenes del conjunto de datos IDRiD (Indian Diabetic Retinopathy Image Dataset).

---

## Objetivo

Comprobar técnicamente la posibilidad de representar regiones de interés de imágenes de fondo de ojo como superficies tridimensionales interactivas en un navegador web.

Como parte de la prueba de concepto se evaluaron diferentes bibliotecas de visualización 3D:

- Three.js
- VTK.js
- Plotly 3D

---

## Flujo general

El funcionamiento del prototipo sigue el siguiente proceso:

1. Se carga una imagen de fondo de ojo.
2. Se carga una máscara de segmentación correspondiente a una lesión.
3. La máscara identifica los píxeles pertenecientes a la región de interés.
4. Los píxeles identificados se utilizan para generar una altura artificial.
5. La información se representa como una superficie tridimensional.
6. El usuario puede rotar y hacer zoom sobre la superficie.
7. La altura del relieve puede modificarse mediante un control.

Es importante señalar que la máscara no contiene información de profundidad real. Por esta razón, la altura utilizada en la visualización es una representación artificial cuyo objetivo es facilitar la interpretación visual de las regiones segmentadas.

---

## Datos utilizados

Para las pruebas se utilizó el conjunto de datos IDRiD.

El prototipo utiliza principalmente:

- `IDRiD_01.jpg` — imagen de fondo de ojo.
- `IDRiD_01_MA.tif` — máscara original de microaneurismas.
- `IDRiD_01_MA.png` — máscara de microaneurismas convertida a PNG.
- `IDRiD_01_HE.tif` — máscara original de hemorragias.
- `IDRiD_01_HE.png` — máscara de hemorragias convertida a PNG.

También se generaron algunos archivos auxiliares durante las pruebas:

- `IDRiD_01_MA_visual.png`
- `heightmap_MA.png`

---

## Bibliotecas evaluadas

### Three.js

Three.js se utilizó para desarrollar el prototipo principal de visualización 3D.

Permite crear una superficie tridimensional a partir de la información de la máscara y aplicar la imagen del fondo de ojo como textura.

El prototipo desarrollado permite:

- Visualización 3D.
- Rotación de la superficie.
- Zoom.
- Modificación de la altura del relieve.
- Visualización de la imagen del fondo de ojo.
- Representación de la región identificada mediante la máscara.

El archivo principal de la prueba con Three.js es:

`index.html`

También se conservaron archivos de respaldo y experimentación:

- `index_funcionando.html`
- `index_prueba_relieve.html`

---

### Plotly 3D

Plotly se utilizó para comprobar una alternativa de visualización tridimensional.

La prueba se realizó utilizando los datos reales del conjunto IDRiD y se desarrollaron pruebas con dos tipos de lesiones:

- Microaneurismas (MA).
- Hemorragias (HE).

Los archivos utilizados para estas pruebas son:

- `prueba_plotly.html`
- `prueba_plotly_HE.html`

La prueba permite interactuar con la superficie tridimensional mediante rotación y zoom, además de modificar la altura del relieve mediante un control.

---

### VTK.js

También se realizó una prueba inicial de integración con VTK.js.

La biblioteca no pudo ejecutarse correctamente en la configuración utilizada para esta prueba debido a dependencias de módulos que no fueron resueltas mediante la carga directa desde CDN.

Por este motivo, no se continuó con la implementación del prototipo utilizando VTK.js.

El archivo correspondiente a esta prueba es:

`prueba_vtk.html`

Esto corresponde a una limitación de la configuración utilizada durante la prueba y no significa que VTK.js no pueda utilizarse en otros entornos o configuraciones.

---

## Estructura del proyecto

```text
Proyecto_Visualizacion_3D/
│
├── datos/
│   ├── IDRiD_01.jpg
│   ├── IDRiD_01_MA.tif
│   ├── IDRiD_01_MA.png
│   ├── IDRiD_01_HE.tif
│   ├── IDRiD_01_HE.png
│   ├── IDRiD_01_MA_visual.png
│   └── heightmap_MA.png
│
├── README.md
├── index.html
├── index_funcionando.html
├── index_prueba_relieve.html
├── prueba_plotly.html
├── prueba_plotly_HE.html
└── prueba_vtk.html