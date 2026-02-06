# Acceso a Datos

## Estructura de Datos

El proyecto EMBODY Mapas Corporales incluye varios archivos de datos y documentación:

### Directorio `data/`

#### `adquisicion.csv`
Contiene información sobre la adquisición de datos:
- Formato: CSV (Comma-Separated Values)
- Ubicación: `/data/adquisicion.csv`
- Propósito: Registro de datos de adquisición para las tareas

#### `orden_exposicion.csv`
Define el orden de exposición de las tareas:
- Formato: CSV (Comma-Separated Values)
- Ubicación: `/data/orden_exposicion.csv`
- Propósito: Especifica la secuencia de presentación de tareas

### Documentos PDF

#### `manual.pdf`
- **Contenido**: Información detallada de acceso al sistema
- **Ubicación**: Raíz del repositorio
- **Uso**: Consulta obligatoria antes de comenzar

#### `Guia_protocol_entrevistador FINAL.docx-8.pdf`
- **Contenido**: Protocolo completo para entrevistadores
- **Ubicación**: Raíz del repositorio
- **Uso**: Guía paso a paso para la conducción de entrevistas

## Cómo Acceder a los Datos

### Método 1: Clonar el Repositorio

```bash
# Clonar el repositorio completo
git clone https://github.com/Daniel-atilano/EMBODY-Mapas-Corporales.git

# Navegar al directorio
cd EMBODY-Mapas-Corporales

# Ver los archivos de datos
ls data/
```

### Método 2: Descargar Archivos Individuales

1. Visita el repositorio en GitHub
2. Navega al archivo que necesitas
3. Haz clic en "Raw" o "Download"
4. Guarda el archivo en tu sistema

### Método 3: Usar la Interfaz Web de GitHub

- Accede directamente a través de:
  - https://github.com/Daniel-atilano/EMBODY-Mapas-Corporales/tree/main/data

## Formato de los Datos

### Archivos CSV

Los archivos CSV utilizan el formato estándar:
- Separador: Coma (`,`)
- Codificación: UTF-8
- Primera fila: Encabezados

### Leer los Datos

Puedes leer los datos CSV con diferentes herramientas:

**Python:**
```python
import pandas as pd

# Leer adquisición
df_adquisicion = pd.read_csv('data/adquisicion.csv')

# Leer orden de exposición
df_orden = pd.read_csv('data/orden_exposicion.csv')
```

**R:**
```r
# Leer adquisición
adquisicion <- read.csv('data/adquisicion.csv')

# Leer orden de exposición
orden <- read.csv('data/orden_exposicion.csv')
```

**Excel/LibreOffice:**
- Abre el archivo directamente o importa como CSV

## Permisos y Privacidad

- Consulta el `manual.pdf` para información sobre permisos de acceso
- Respeta las políticas de privacidad y uso de datos
- No compartas datos sensibles sin autorización

## Actualización de Datos

Si necesitas actualizar los datos:

1. Crea una copia de seguridad
2. Mantén el formato CSV original
3. Verifica la integridad de los datos
4. Documenta los cambios realizados
5. Consulta con el equipo antes de hacer cambios importantes

## Soporte Técnico

Para problemas relacionados con el acceso a datos:

1. Verifica que tienes los permisos necesarios (ver `manual.pdf`)
2. Asegúrate de usar la versión más reciente del repositorio
3. Abre un issue en GitHub si encuentras problemas
