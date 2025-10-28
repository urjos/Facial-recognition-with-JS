--- a/c:\Users\USER\OneDrive\Desktop\Proyectos\P-AP\Facial-recognition-with-JS\README.md
+++ b/c:\Users\USER\OneDrive\Desktop\Proyectos\P-AP\Facial-recognition-with-JS\README.md
@@ -1 +1,123 @@
-Proyecto de reconocimiento facial con JS
+# 👨‍💻 Reconocimiento Facial con JavaScript y face-api.js

-
-
- +Este proyecto es una aplicación web que implementa reconocimiento facial en tiempo real utilizando la cámara del dispositivo. Es capaz de detectar rostros, identificar puntos de referencia faciales (ojos, nariz, boca) y reconocer a personas previamente registradas, todo directamente en el navegador sin necesidad de un backend.
- +---
- +## ✨ Características Principales
- +- **Detección en Tiempo Real:** Detecta y traza rostros desde el stream de la webcam a una alta velocidad de fotogramas.
  +- **Reconocimiento de Personas:** Identifica a individuos específicos después de haber sido "entrenado" con un conjunto de imágenes de referencia.
  +- **Análisis Facial:** Superpone puntos de referencia faciales (landmarks), cajas delimitadoras y la identidad de la persona reconocida sobre el video.
  +- **Detección de Múltiples Rostros:** Capaz de identificar y reconocer a varias personas en el cuadro simultáneamente.
  +- **Basado en el Navegador:** Todo el procesamiento se realiza en el lado del cliente, lo que garantiza la privacidad y una respuesta rápida.
  +- **Interfaz Sencilla:** Una interfaz de usuario limpia que facilita la interacción y la visualización de los resultados.
- +---
- +## 🛠️ Tecnologías Utilizadas
- +- **HTML5:** Para la estructura de la página web.
  +- **CSS3:** Para el diseño y la presentación visual.
  +- **JavaScript (ES6+):** Para toda la lógica de la aplicación.
  +- **face-api.js:** La biblioteca principal que proporciona los modelos pre-entrenados de redes neuronales para la detección y reconocimiento facial, construida sobre TensorFlow.js.
- +---
- +## 🚀 Cómo Empezar
- +Sigue estos pasos para ejecutar el proyecto en tu máquina local.
- +### Prerrequisitos
- +No necesitas instalar dependencias complejas. Solo necesitas un navegador web moderno que soporte `getUserMedia` (para acceder a la cámara) y un servidor web local para servir los archivos.
- +### Instalación y Ejecución
- +1. **Clona el repositorio:**
- ```bash

  ```
- git clone https://github.com/tu-usuario/tu-repositorio.git
- ```

  ```
- +2. **Navega al directorio del proyecto:**
- ```bash

  ```
- cd Facial-recognition-with-JS
- ```

  ```
- +3. **Inicia un servidor web local:**
- Debido a las políticas de seguridad de los navegadores, los archivos deben ser servidos a través de un servidor HTTP/S. No puedes simplemente abrir el `index.html` desde el sistema de archivos.
-
- Si tienes **Node.js** instalado, puedes usar `live-server`:
- ```bash

  ```
- # Instala live-server globalmente si no lo tienes
- npm install -g live-server
-
- # Inicia el servidor en el directorio del proyecto
- live-server
- ```

  ```
-
- Si tienes **Python** instalado:
- ```bash

  ```
- # Para Python 3
- python -m http.server
-
- # Para Python 2
- python -m SimpleHTTPServer
- ```

  ```
- +4. **Abre la aplicación:**
- Abre tu navegador y ve a la dirección que te indique el servidor local (generalmente `http://127.0.0.1:8080` o `http://localhost:8000`).
- +---
- +## 📖 Uso
- +1. Al abrir la aplicación, el navegador te pedirá permiso para acceder a tu cámara web. Debes aceptarlo.
  +2. La aplicación comenzará a procesar el video en tiempo real.
  +3. Apunta la cámara hacia un rostro. Verás una caja delimitadora alrededor de la cara detectada.
  +4. Si el rostro coincide con alguna de las imágenes de referencia cargadas en el código, se mostrará el nombre de la persona junto con un puntaje de confianza.
- +### ¿Cómo añadir nuevas personas para reconocer?
- +Para que la aplicación reconozca a nuevas personas, debes agregar sus imágenes de referencia en el directorio `labeled_images`.
- +1. Crea una nueva carpeta dentro de `labeled_images` con el nombre de la persona (ej. `Elon Musk`).
  +2. Añade una o más imágenes claras del rostro de esa persona dentro de la carpeta recién creada (ej. `1.jpg`, `2.png`).
  +3. El script cargará automáticamente estas imágenes y creará los descriptores faciales necesarios para el reconocimiento.
- +> **Nota:** Se recomienda usar al menos 2 o 3 imágenes por persona desde diferentes ángulos para mejorar la precisión del reconocimiento.
- +---
- +## ⚙️ ¿Cómo Funciona?
- +El núcleo de este proyecto es la biblioteca **face-api.js**. El flujo de trabajo es el siguiente:
- +1. **Carga de Modelos:** Al iniciar, la aplicación carga de forma asíncrona varios modelos de aprendizaje profundo pre-entrenados que se encuentran en el directorio `/models`. Estos modelos son para:
- - Detección de rostros (`ssd_mobilenetv1`).
- - Detección de puntos de referencia faciales (`face_landmark_68_model`).
- - Reconocimiento facial (`face_recognition_model`).
- +2. **Carga de Descriptores de Referencia:** La aplicación procesa las imágenes del directorio `labeled_images` para generar un "descriptor facial" para cada persona. Un descriptor es un vector de 128 números que representa las características únicas de un rostro.
- +3. **Procesamiento del Video:**
- - La aplicación captura un fotograma del video de la cámara.
- - Utiliza el modelo de detección para encontrar todas las caras en el fotograma.
- - Para cada cara detectada, calcula su descriptor facial.
- - Compara este descriptor con los descriptores de referencia previamente cargados para encontrar la coincidencia más cercana (la menor distancia euclidiana).
- +4. **Visualización:** Finalmente, dibuja los resultados (cajas, nombres, landmarks) en un elemento `<canvas>` superpuesto sobre el video.
- +---
- +## 🤝 Contribuciones
- +Las contribuciones son bienvenidas. Si tienes ideas para mejorar el proyecto, por favor, abre un _issue_ para discutirlo o envía un _pull request_ con tus cambios.
- +---
- +## 📜 Licencia
- +Este proyecto está bajo la Licencia MIT. Consulta el archivo `LICENSE` para más detalles.
