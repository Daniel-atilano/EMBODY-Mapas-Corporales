# EMBODY – Mapas Corporales (Acceso al experimento)

Este repositorio documenta cómo **acceder, ejecutar y recuperar datos** de la versión web del experimento **EMBODY – Mapas Corporales**, con el objetivo de que **otros investigadores** puedan replicar el protocolo y correr sesiones de manera consistente.

> **Importante (créditos y procedencia):**  
> Esta implementación es una **copia** del *emBODY tool* desarrollado por **Enrico Glerean, Lauri Nummenmaa y Juulia Suvilehto**.  
> Para su uso en este proyecto, el experimento fue **traducido al español** y adaptado para su implementación local (infraestructura INB UNAM).   
> Publicado bajo licencia MIT.

---

## 1) Acceso a la aplicación web del experimento

El **manual de operación** (`manual.pdf`) contiene una guía **paso a paso** y **material gráfico** (pantallas, navegación y flujo) para ejecutar el experimento desde la interfaz web.

- **URL del experimento (v1):** http://132.248.142.189/v1
- **Manual (PDF):** [`manual.pdf`](manual.pdf)

### Recomendación previa a sesiones
Antes de correr sesiones con participantes:
- Verifica conectividad a la URL del experimento.
- Usa el navegador/equipo con el que planeas mantener consistencia durante toda la recolección.
- Revisa el manual completo para asegurar que el flujo (activación/desactivación y registro por emoción) se siga sin variaciones.

---

## 2) Al finalizar: guardar el ID del participante (crítico para recuperar/ubicar datos)

Una vez que el participante **contesta** el experimento, es **indispensable guardar el `ID`** que queda registrado en la sesión.

- Ese **ID** es la clave para **buscar/ubicar** al participante dentro de la carpeta correspondiente en el servidor, en la ruta asociada a `subjects` (ver sección 3).
- En términos operativos: si no guardas el ID, **se vuelve difícil o imposible** rastrear de forma confiable el registro del sujeto en el almacenamiento del servidor.

---

## 3) Acceso a sujetos (subjects) en el servidor

Para acceder a los **sujetos** los usuarios deben ingresar a la ruta del servidor:

- **Ruta local en servidor:** `/var/www/html/v1/subjects`

**Requisitos de red / infraestructura:**
- **IP del servidor:** `172.24.250.39`
- **Acceso:** disponible **desde el cluster del INB UNAM** (red interna).
- **Usuario:** `server_v1`
- **Contraseña** Previa solicitud al creador de este repositorio o al correo dan.luchin06@gmail.com

> Si estás fuera del cluster/red interna del INB UNAM, es posible que no tengas conectividad directa al servidor (IP privada) ni a las rutas internas.

---

## 4) Manual de operación (PDF)

Para la guía operativa detallada (flujo del experimento, pantallas, navegación y consideraciones de ejecución), consulta:

- [`manual.pdf`](manual.pdf)

---

## 5) PASO 7 (opcional): preguntas posteriores para análisis cualitativo

El protocolo puede incluir un **PASO 7** adicional después de que la persona haya coloreado los cuerpos.  
Este paso consiste en realizar preguntas para obtener una **explicación cualitativa** (verbal) de la experiencia emocional y del patrón corporal dibujado.

> **Este PASO 7 es opcional.**  
> Se recomienda **solo si tu estudio incluye análisis cualitativo** de la respuesta emocional (por ejemplo: conceptualización, narrativa y desencadenantes).

### Preguntas sugeridas (repetir por emoción y por mapa)
Una vez que la persona haya coloreado los cuerpos, se pueden hacer las siguientes preguntas:

**a) Concientización emocional / búsqueda de la razón emocional**
- “¿Hay alguna razón del por qué dibujaste esa sensación en esa parte del cuerpo?”
- “¿Por qué crees que sientes esa sensación en esas regiones?” *(mencionar las regiones que dibujó el participante)*  
> Realizar la pregunta tanto para el mapa de **ACTIVACIÓN** como para el de **DEACTIVACIÓN**.

**b) Conceptualización y descripción emocional**
- “¿Qué es para ti [EMOCIÓN que se esté registrando]?”
- “¿Cómo lo sientes?, ¿cómo lo definirías?”

**c) Desencadenantes emocionales de la vida cotidiana**
- “¿Qué acontecimientos o qué situaciones te desencadenan esta emoción?”

Este bloque se repite para cada una de las **14 emociones** presentadas en el instrumento.

---

## 6) Sugerencias de buenas prácticas para replicación

- Documentar **fecha/hora** de cada sesión, el **ID del sujeto** (ver sección 2) y el **contexto de red** (desde qué nodo/segmento del cluster se accedió).
- Verificar disponibilidad del servicio web antes de programar sesiones.
- Mantener consistencia de navegador/equipo.

---

## 7) Análisis de mapas corporales con MATLAB

La carpeta `matlab/` contiene los scripts y datos necesarios para **preprocesar, visualizar y analizar estadísticamente** los mapas corporales obtenidos con el experimento.

### Contenido de la carpeta `matlab/`

| Archivo / Carpeta | Descripción |
|---|---|
| `embody_demo.m` | Script principal de preprocesamiento y visualización individual por sujeto |
| `embody_stats.m` | Script de análisis estadístico grupal (t-test de una muestra con corrección FDR) |
| `load_subj.m` | Función auxiliar para cargar los datos CSV de cada sujeto |
| `FDR.m` | Función para la corrección de comparaciones múltiples (Benjamini-Hochberg FDR) |
| `showpaint.m` | Función auxiliar para visualizar trazos de pintura sin preprocesar |
| `base.png` | Imagen base de la silueta corporal usada como fondo en las visualizaciones |
| `mask.png` | Máscara binaria que delimita la región corporal válida para el análisis estadístico |
| `demo_subjects/` | Carpeta con 3 sujetos de demostración (IDs: `243952`, `642687`, `984332`) |
| `models/PNAS2014/` | Archivo `2014_Bodily_Maps_of_Emotions.mat` con los mapas del artículo original de Nummenmaa et al. (2014) |

### Estructura de datos por sujeto

Cada subcarpeta de `demo_subjects/` (nombrada con el ID del sujeto) contiene:

- **`0.csv` a `13.csv`**: Un archivo CSV por cada una de las **14 emociones**, con los movimientos del ratón y los trazos de pintura registrados durante la sesión.
- **`presentation.txt`**: Orden de presentación de las emociones para ese sujeto (el experimento aleatoriza el orden entre participantes).
- **`data.txt`**: Metadatos del sujeto.

Las 14 condiciones emocionales (indexadas de 0 a 13) son:

| Índice | Emoción |
|--------|---------|
| 0 | Nada especial (neutral) |
| 1 | Miedo |
| 2 | Ira |
| 3 | Asco |
| 4 | Tristeza |
| 5 | Felicidad |
| 6 | Sorpresa |
| 7 | Ansiedad |
| 8 | Amor |
| 9 | Depresión |
| 10 | Desprecio |
| 11 | Orgullo |
| 12 | Vergüenza |
| 13 | Celos |

### Flujo de análisis

#### Paso A — Preprocesamiento individual (`embody_demo.m`)

1. Ajusta la variable `basepath` para que apunte a la carpeta que contiene los sujetos recolectados.
2. El script carga los datos de cada sujeto con `load_subj`, que lee los archivos CSV de cada emoción siguiendo el orden indicado en `presentation.txt`.
3. Reconstruye el mapa de activaciones a partir de las posiciones del ratón registradas mientras el botón estaba presionado (campo `paint` del CSV).
4. Aplica un **filtro gaussiano** (kernel de 15×15 píxeles, σ=5) sobre la imagen reconstruida para simular el tamaño del pincel.
5. Calcula la **diferencia activación − desactivación** restando la mitad derecha de la silueta a la izquierda (diseño del experimento: lado izquierdo de la pantalla = activación, lado derecho = desactivación).
6. Guarda los resultados preprocesados en la carpeta `preprocessed/` como archivos `.mat` con el nombre `<ID_sujeto>_preprocessed.mat`.
7. Genera una figura por sujeto con una cuadrícula de los 14 mapas corporales, coloreados con un mapa de calor bicromático frío-caliente.

#### Paso B — Análisis estadístico grupal (`embody_stats.m`)

1. Carga todos los archivos `.mat` generados en el Paso A desde la carpeta `preprocessed/`.
2. Realiza un **t-test de una muestra** (contraste frente a media = 0) píxel a píxel para cada una de las 14 condiciones, considerando únicamente los píxeles dentro de la máscara corporal (`mask.png`).
3. Aplica **corrección por comparaciones múltiples** mediante el método de Benjamini-Hochberg (FDR; función `FDR.m`) a nivel de todas las condiciones combinadas.
4. Genera una figura con los **t-mapas estadísticos** de cada emoción usando un mapa de color frío-caliente, donde los valores no significativos aparecen en negro.

> **Requisitos de software:** MATLAB con Image Processing Toolbox y Statistics and Machine Learning Toolbox.  
> El código fue desarrollado originalmente por Enrico Glerean y Lauri Nummenmaa. Los propios autores señalan que sería relativamente sencillo portar el código a Python para quienes no dispongan de licencia MATLAB.

---

## 8) CITACIÓN (requerida si usas el instrumento)

Si utilizas este instrumento en investigación, por favor cita:

Nummenmaa L., Glerean E., Hari R., Hietanen, J.K. (2014)  
**Bodily maps of emotions**, *Proceedings of the National Academy of Sciences of the United States of America*  
doi:10.1073/pnas.1321664111  
http://www.pnas.org/content/111/2/646.abstract
