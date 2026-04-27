# Reconocimiento facial con Eigenfaces — Caras de la clase

Trabajo grupal para la materia **Data Mining Avanzado**
Maestría en Ciencia de Datos · 2026 — 2° Cuatrimestre

## 📋 Descripción

Implementación clásica de **Eigenfaces** (PCA aplicado a imágenes de caras)
para detectar y comparar las caras de los 14 alumnos de la clase.

El pipeline parte de fotos individuales de cada alumno (en distintos formatos
y con distintas variantes de nombre en los archivos) y produce:

- Una matriz de distancias entre todos los alumnos.
- Un ranking de los pares más parecidos / menos parecidos.
- La "cara gemela" de cada alumno dentro del grupo.

## 🧪 Pipeline

1. **Carga de fotos** desde Google Drive (formatos `.jpg`, `.jpeg`, `.png`, `.heic`).
2. **Detección de rostros** con DeepFace (RetinaFace), con respaldo en Haar Cascade
   para imágenes donde DeepFace no detecta cara.
3. **Recorte por borde oval** del rostro (no rectangular) usando los landmarks
   faciales de DeepFace, y conversión a escala de grises 30×30 px.
4. **Reducción de dimensionalidad** con PCA → Eigenfaces (~50 componentes).
5. **Cálculo de vector promedio** por alumno (cada alumno aporta varias fotos).
6. **Matriz de distancias euclidianas** entre vectores promedio.
7. **Ranking** de pares más / menos parecidos.

## 📁 Estructura del repositorio

```
eigenfaces-dma/
├── eigenfaces_caras_clase.ipynb   # Notebook principal (Google Colab)
├── requirements.txt               # Librerías necesarias
├── .gitignore                     # Evita subir fotos al repo
└── README.md                      # Este archivo
```

## ⚠️ Importante: privacidad de las fotos

**Las fotos de los alumnos NO se incluyen en este repositorio.**

Cada integrante del grupo debe tener acceso a la carpeta compartida de Google Drive
con las imágenes. La ruta usada en el notebook es:

```
/My Drive/MAESTRIA CS DATOS/2026 - 2 Cuatrimestre/Data Mining Avanzado/Nuestras caras
```

Si trabajan en una carpeta distinta, modifiquen la variable `ruta_fotos`
en la **Celda 3** del notebook.

## 🚀 Cómo ejecutar

1. Abrir el notebook `eigenfaces_caras_clase.ipynb` en **Google Colab**.
2. Asegurarse de tener acceso a la carpeta compartida de Google Drive.
3. Ejecutar las celdas en orden. La primera vez:
   - Las celdas 1 y 2 instalan e importan librerías.
   - La celda 3 monta el Drive (pide autorización).
   - La celda 7 puede tardar ~15-20 minutos (procesa todas las fotos).
4. El procesamiento usa **checkpoints**: si Colab se reinicia, retoma desde donde quedó.

## 👥 Grupo de trabajo

- Mariángeles Alomar
- Judith Luna
- Federico Spinelli
- Juan Ignacio Cacchione

## 📚 Referencias

- Turk, M., & Pentland, A. (1991). *Eigenfaces for recognition*. Journal of Cognitive Neuroscience.
- DeepFace: <https://github.com/serengil/deepface>
- scikit-learn PCA: <https://scikit-learn.org/stable/modules/generated/sklearn.decomposition.PCA.html>
