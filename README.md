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

## 7) CITACIÓN (requerida si usas el instrumento)

Si utilizas este instrumento en investigación, por favor cita:

Nummenmaa L., Glerean E., Hari R., Hietanen, J.K. (2014)  
**Bodily maps of emotions**, *Proceedings of the National Academy of Sciences of the United States of America*  
doi:10.1073/pnas.1321664111  
http://www.pnas.org/content/111/2/646.abstract