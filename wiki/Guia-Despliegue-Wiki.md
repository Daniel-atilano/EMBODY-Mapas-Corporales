# Guía de Despliegue del Wiki

Esta guía explica cómo desplegar y mantener el wiki de EMBODY Mapas Corporales.

## Introducción

El wiki de este proyecto se despliega automáticamente usando GitHub Actions. Cada vez que se realizan cambios en el directorio `wiki/` del repositorio principal, el workflow actualiza el wiki de GitHub automáticamente.

## Arquitectura del Despliegue

### Componentes

1. **Directorio `wiki/`**: Contiene los archivos fuente del wiki en formato Markdown
2. **GitHub Actions Workflow**: Automatiza el despliegue (`.github/workflows/deploy-wiki.yml`)
3. **GitHub Wiki**: Sitio wiki público accesible a través de GitHub

### Flujo de Despliegue

```
Editar archivo en wiki/ → Commit → Push → GitHub Actions → Wiki actualizado
```

## Métodos de Despliegue

### Método 1: Despliegue Automático (Recomendado)

El despliegue automático se ejecuta cuando:

1. Se hace push a la rama `main` o `master`
2. Los cambios afectan archivos en el directorio `wiki/`
3. Se activa manualmente desde GitHub Actions

**Pasos:**

1. Edita o crea archivos `.md` en el directorio `wiki/`
2. Realiza commit de los cambios:
   ```bash
   git add wiki/
   git commit -m "Actualizar wiki: descripción de cambios"
   git push origin main
   ```
3. El workflow se ejecutará automáticamente
4. Verifica en la pestaña "Actions" de GitHub

### Método 2: Despliegue Manual

Para desplegar manualmente:

1. Ve a la pestaña "Actions" en GitHub
2. Selecciona el workflow "Deploy Wiki"
3. Haz clic en "Run workflow"
4. Selecciona la rama y ejecuta

### Método 3: Edición Directa del Wiki

También puedes editar el wiki directamente en GitHub:

1. Ve a https://github.com/Daniel-atilano/EMBODY-Mapas-Corporales/wiki
2. Haz clic en "Edit" en cualquier página
3. Realiza los cambios y guarda

**Nota:** Los cambios directos en el wiki se sobrescribirán en el próximo despliegue automático.

## Crear Nuevas Páginas

### Estructura de Archivos

Cada página del wiki es un archivo Markdown en `wiki/`:

```
wiki/
├── Home.md                      # Página principal (obligatoria)
├── Instrucciones-de-Uso.md      # Página de instrucciones
├── Acceso-a-Datos.md            # Página de datos
├── Guia-Despliegue-Wiki.md      # Esta página
└── images/                      # Directorio opcional para imágenes
    └── ejemplo.png
```

### Crear una Nueva Página

1. Crea un nuevo archivo `.md` en `wiki/`:
   ```bash
   touch wiki/Nueva-Pagina.md
   ```

2. Añade contenido en formato Markdown:
   ```markdown
   # Título de la Nueva Página
   
   Contenido de la página...
   ```

3. Añade un enlace en `Home.md` o en otra página:
   ```markdown
   - [Nueva Página](Nueva-Pagina)
   ```

4. Commit y push:
   ```bash
   git add wiki/Nueva-Pagina.md
   git commit -m "Añadir nueva página al wiki"
   git push origin main
   ```

## Formato y Estilo

### Markdown Básico

```markdown
# Título 1
## Título 2
### Título 3

**Negrita**
*Cursiva*

- Lista con viñetas
- Otro elemento

1. Lista numerada
2. Otro elemento

[Texto del enlace](URL)

![Texto alternativo](ruta/imagen.png)

`código en línea`

```bash
bloque de código
```
```

### Enlaces Internos

Para enlazar entre páginas del wiki:

```markdown
[Instrucciones](Instrucciones-de-Uso)
[Datos](Acceso-a-Datos)
```

### Imágenes

Para añadir imágenes:

1. Guarda la imagen en `wiki/images/`
2. Referencia en el Markdown:
   ```markdown
   ![Descripción](images/nombre-imagen.png)
   ```

## Workflow de GitHub Actions

### Configuración

El workflow está en `.github/workflows/deploy-wiki.yml` y realiza:

1. **Checkout del repositorio principal**
2. **Checkout del repositorio wiki**
3. **Copia de archivos** del directorio `wiki/` al repositorio wiki
4. **Commit y push** de los cambios al wiki

### Triggers

El workflow se ejecuta cuando:
- Hay push a `main` o `master` con cambios en `wiki/**`
- Se ejecuta manualmente (`workflow_dispatch`)

### Permisos

El workflow usa `GITHUB_TOKEN` automático que tiene permisos para:
- Leer el repositorio principal
- Escribir en el repositorio wiki

No se requiere configuración adicional de secrets.

## Verificación del Despliegue

### Comprobar Estado

1. Ve a la pestaña "Actions" en GitHub
2. Busca el workflow "Deploy Wiki"
3. Verifica que el último run fue exitoso (✓ verde)

### Ver el Wiki Desplegado

- URL del Wiki: https://github.com/Daniel-atilano/EMBODY-Mapas-Corporales/wiki
- También accesible desde el repositorio principal, pestaña "Wiki"

### Logs del Workflow

Si hay problemas:

1. Ve a "Actions" → "Deploy Wiki"
2. Haz clic en el run fallido
3. Expande los pasos para ver los logs
4. Busca mensajes de error

## Solución de Problemas

### El Workflow No Se Ejecuta

**Problema:** Los cambios no activan el workflow

**Solución:**
- Verifica que los cambios están en el directorio `wiki/`
- Confirma que se hizo push a `main` o `master`
- Revisa los permisos de GitHub Actions en Settings → Actions

### Errores de Permisos

**Problema:** "Permission denied" en el workflow

**Solución:**
- Ve a Settings → Actions → General
- En "Workflow permissions", selecciona "Read and write permissions"
- Guarda los cambios

### El Wiki No Se Actualiza

**Problema:** El workflow se ejecuta pero el wiki no cambia

**Solución:**
- Limpia la caché del navegador
- Verifica que los archivos en `wiki/` tienen formato Markdown correcto
- Revisa los logs del workflow para errores

### Conflictos de Merge

**Problema:** Error al hacer push al wiki

**Solución:**
- Generalmente el workflow maneja esto automáticamente
- Si persiste, contacta al administrador del repositorio

## Mejores Prácticas

### 1. Mantén la Estructura

- Usa nombres de archivo descriptivos
- Sigue la convención de nombres con guiones: `Nombre-De-Pagina.md`
- Organiza las imágenes en `wiki/images/`

### 2. Contenido de Calidad

- Usa títulos claros y descriptivos
- Incluye enlaces de navegación
- Mantén las páginas concisas y enfocadas
- Actualiza la página Home con enlaces a nuevas páginas

### 3. Control de Versiones

- Escribe mensajes de commit descriptivos
- Revisa los cambios antes de hacer push
- Usa branches para cambios grandes

### 4. Revisión

- Previsualiza el Markdown localmente antes de hacer commit
- Verifica los enlaces internos
- Confirma que las imágenes se muestran correctamente

## Comandos Útiles

```bash
# Ver estado de archivos wiki
git status wiki/

# Ver cambios en wiki
git diff wiki/

# Añadir todos los cambios del wiki
git add wiki/

# Commit de cambios del wiki
git commit -m "Actualizar wiki: descripción"

# Push para desplegar
git push origin main

# Ver logs del último commit
git log -1 --oneline

# Previsualizar markdown localmente (requiere herramienta como grip)
grip wiki/Home.md
```

## Acceso Rápido

- **Repositorio Principal**: https://github.com/Daniel-atilano/EMBODY-Mapas-Corporales
- **Wiki**: https://github.com/Daniel-atilano/EMBODY-Mapas-Corporales/wiki
- **Actions**: https://github.com/Daniel-atilano/EMBODY-Mapas-Corporales/actions

## Recursos Adicionales

- [GitHub Wiki Documentation](https://docs.github.com/en/communities/documenting-your-project-with-wikis)
- [GitHub Actions Documentation](https://docs.github.com/en/actions)
- [Markdown Guide](https://www.markdownguide.org/)

## Soporte

Para preguntas sobre el despliegue del wiki:

1. Consulta esta guía primero
2. Revisa los logs del workflow en Actions
3. Abre un issue en el repositorio con detalles específicos
