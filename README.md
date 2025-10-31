# 🐶 SOS Mascota Tacna

### 📱 Aplicación móvil colaborativa para la localización de mascotas perdidas

---

## 📖 Descripción del Proyecto

**SOS Mascota Tacna** es una aplicación móvil desarrollada en **Flutter + Firebase**, creada para **ayudar a encontrar mascotas perdidas** mediante la colaboración ciudadana.

La app permite que los usuarios:
- Reporten **mascotas perdidas o encontradas** con imagen, descripción y ubicación GPS.  
- Reciban **notificaciones push** cuando se detectan coincidencias cercanas.  
- Se **comuniquen mediante chat** en tiempo real para coordinar rescates.  
- Usen **Inteligencia Artificial (TFLite + OpenAI)** para identificar el tipo de animal.  
- Participen en un **ranking colaborativo** de voluntarios confiables.

> Proyecto académico desarrollado para el curso **Soluciones Móviles II – Universidad Privada de Tacna (UPT, 2025-II)**.

---

## 🎯 Objetivo

Brindar una solución tecnológica moderna y accesible que mejore la **efectividad de la búsqueda y rescate de mascotas**, fomentando la participación comunitaria y el uso responsable de la tecnología.

---

## ⚙️ Tecnologías Utilizadas

| Categoría | Herramientas |
|------------|---------------|
| **Frontend móvil** | Flutter (Dart) |
| **Backend y base de datos** | Firebase (Firestore, Auth, Storage, FCM) |
| **IA local** | TensorFlow Lite |
| **API externa** | OpenAI API |
| **Arquitectura** | MVVM + SOLID |
| **Control de versiones** | Git y GitHub |
| **Automatización CI/CD** | GitHub Actions |
| **Diseño UI/UX** | Material Design 3 + Lottie Animations |

---
#  FD02 – Wiki y el RoadMap
📘 **Wiki del Proyecto:**  
➡️ [Home](https://github.com/UPT-FAING-EPIS/proyecto-si784-2025-ii-u2-sosmascota/wiki)  
➡️ [Roadmap](https://github.com/UPT-FAING-EPIS/proyecto-si784-2025-ii-u2-sosmascota/wiki/Roadmap)  
➡️ [Tecnologías](https://github.com/UPT-FAING-EPIS/proyecto-si784-2025-ii-u2-sosmascota/wiki/Tecnologias)  

---
# 🧠 FD03 – Historias de Usuario, Criterios de Aceptación y Escenarios de Prueba (TensorFlow Lite)

Este documento presenta las **historias de usuario**, **criterios de aceptación** y **escenarios de prueba** del módulo de **TensorFlow Lite (TFLite)** utilizado en la aplicación **SOS Mascota Tacna**, específicamente en las funciones de **reporte de mascota** y **chat entre usuarios**.

El modelo **TFLite** permite clasificar imágenes localmente (perro o gato) y analizar similitudes entre fotografías para facilitar la búsqueda de coincidencias entre reportes.

---

## 🐾 HU01 – Reportar Mascota Perdida (Clasificación con TFLite)

**Como** usuario registrado,  
**Quiero** que la aplicación analice la imagen de mi mascota utilizando el modelo **TFLite**,  
**Para** que el sistema determine automáticamente si es un perro o un gato y mejore el proceso de búsqueda.

### ✅ Criterios de Aceptación
- CA1. El modelo `animales.tflite` debe ejecutarse localmente al subir una imagen.  
- CA2. La predicción debe devolver la etiqueta (“perro” o “gato”) y un porcentaje de confianza.  
- CA3. Si la confianza es menor al 70%, el sistema debe solicitar una nueva imagen.

### 🧪 Escenarios de Prueba
**Escenario 1:**  
Dado que el usuario selecciona una foto clara de su mascota,  
Cuando el sistema ejecuta el modelo `animales.tflite`,  
Entonces el sistema muestra el resultado **“Perro detectado (94%)”** y permite continuar con el registro del reporte.  

**Escenario 2:**  
Dado que el usuario sube una imagen borrosa o con bajo contraste,  
Cuando el modelo `animales.tflite` intenta procesarla,  
Entonces la confianza cae por debajo del 70% y la app muestra el mensaje:  
> “Imagen no reconocida. Intenta subir una foto más clara.”

---

## 💬 HU02 – Chat entre Usuarios (Coincidencia de Reportes con TFLite)

**Como** usuario que conversa con otro mediante el chat,  
**Quiero** que el sistema use el modelo **TFLite** para comparar las imágenes de nuestros reportes,  
**Para** detectar si las mascotas corresponden al mismo animal y facilitar el reencuentro.

### ✅ Criterios de Aceptación
- CA1. El sistema debe comparar los vectores de características (embeddings) generados por `extractor_animales.tflite`.  
- CA2. Si la similitud entre las imágenes es mayor o igual al 85%, debe mostrarse una alerta visual dentro del chat.  
- CA3. Si la similitud es baja, el sistema continúa la conversación sin generar alerta.

### 🧪 Escenarios de Prueba
**Escenario 1:**  
Dado que dos usuarios intercambian imágenes de mascotas similares,  
Cuando el modelo `extractor_animales.tflite` calcula una similitud del **91%**,  
Entonces la app muestra un mensaje en el chat:  
> “🐾 Posible coincidencia detectada entre las mascotas enviadas.”  

**Escenario 2:**  
Dado que las imágenes comparadas son de animales distintos,  
Cuando el modelo ejecuta la comparación,  
Entonces la similitud es menor al 50% y el sistema no muestra ninguna alerta.

---

## 🧾 Conclusión

Los modelos **TensorFlow Lite** integrados en **SOS Mascota Tacna** permiten realizar clasificación e identificación visual directamente en el dispositivo, sin necesidad de conexión constante a Internet.  
Esto mejora la rapidez del análisis y optimiza la interacción entre usuarios al detectar coincidencias de forma automática y eficiente.

---

