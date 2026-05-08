## 🔗 Archivos en Google Drive

Los modelos entrenados y datos procesados están en la carpeta compartida de Drive:

**[[Link a carpeta de Drive] (https://drive.google.com/drive/folders/1vGLFDlNlFKpVFhBRHy5VUUWa0kcy7Yaz?usp=sharing)**

El notebook de clasificación espera encontrar estos archivos:
- `DMA/datos_30x30/pca_model.pkl` — modelo PCA entrenado
- `DMA/datos_30x30/imagenes_repr.npz` — caras representativas para comparación visual
- `DMA/nn_pca_v8/red.pkl` — red neuronal entrenada

## 🚀 Cómo ejecutar

### Para clasificar fotos nuevas (lo que necesita el profesor):

1. Abrir `GRUPO_1__zBackPropagation_multiclase.ipynb` en Google Colab
2. Correr todas las celdas en orden
3. En la **última celda (Demo Final)**, subir una foto y la red dice quién es
4. Si la confianza es menor a 0.68, la red clasifica como **"desconocido"**

### Para clasificar varias fotos a la vez:

1. Colocar las fotos en la carpeta `Fotos individuales/` en Drive
2. Las fotos deben tener el nombre del alumno como prefijo (ej: `juan_perez_01.jpg`)
3. Correr la **sección 4** del notebook de clasificación

### Para re-generar los Eigenfaces desde cero:

1. Abrir `eigenfaces_caras_clase.ipynb` en Google Colab
2. Asegurarse de tener acceso a la carpeta de fotos en Drive
3. Ejecutar las celdas en orden (la celda 7 tarda ~15-20 minutos)
4. El procesamiento usa checkpoints: si Colab se reinicia, retoma desde donde quedó

## 📊 Resultados

| Métrica | Valor |
|---|---|
| Arquitectura | 80 → [20] → 14 (tansig + logsig) |
| Train error rate | 18.4% |
| **Test error rate** | **39.3%** |
| Accuracy | 60.7% (8.5x mejor que azar) |
| Umbral de desconocido | 0.68 |
| Fotos nuevas individuales | 7/14 correctas (50%) |

## ⚠️ Privacidad

Las fotos de los alumnos **NO** se incluyen en este repositorio. Cada integrante del grupo debe tener acceso a la carpeta compartida de Google Drive.

## 👥 Grupo 1

- Mariangeles Alomar
- Judith Luna
- Federico Spinelli
- Juan Ignacio Cacchione

## 📚 Referencias

- Turk, M., & Pentland, A. (1991). *Eigenfaces for recognition.* Journal of Cognitive Neuroscience.
- DeepFace: https://github.com/serengil/deepface
- scikit-learn PCA: https://scikit-learn.org/stable/modules/generated/sklearn.decomposition.PCA.html
