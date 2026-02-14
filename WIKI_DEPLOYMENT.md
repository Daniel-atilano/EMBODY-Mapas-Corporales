# Despliegue del Wiki - EMBODY Mapas Corporales

Esta guía proporciona instrucciones completas para desplegar y mantener el wiki del proyecto.

## 🚀 Inicio Rápido

El wiki se despliega automáticamente mediante GitHub Actions. Para actualizar el wiki:

1. Edita archivos en el directorio `wiki/`
2. Haz commit y push a `main` o `master`
3. ¡El wiki se actualiza automáticamente!

## 📋 Tabla de Contenidos

- [Introducción](#introducción)
- [Configuración Inicial](#configuración-inicial)
- [Cómo Desplegar el Wiki](#cómo-desplegar-el-wiki)
- [Estructura del Wiki](#estructura-del-wiki)
- [Workflow Automático](#workflow-automático)
- [Solución de Problemas](#solución-de-problemas)

## Introducción

Este repositorio incluye un sistema de despliegue automático para el wiki de GitHub. Los archivos fuente del wiki se mantienen en el directorio `wiki/` del repositorio principal, y GitHub Actions se encarga de sincronizarlos con el wiki público.

### Beneficios

- ✅ Control de versiones del contenido del wiki
- ✅ Despliegue automático mediante GitHub Actions
- ✅ Edición colaborativa usando pull requests
- ✅ Historial completo de cambios

## Configuración Inicial

### Prerrequisitos

- Repositorio en GitHub
- GitHub Actions habilitado
- Wiki del repositorio habilitado

### Habilitar el Wiki (si no está habilitado)

1. Ve a Settings del repositorio
2. En la sección "Features", marca "Wikis"
3. Guarda los cambios

### Configurar Permisos de GitHub Actions

1. Ve a Settings → Actions → General
2. En "Workflow permissions", selecciona "Read and write permissions"
3. Marca "Allow GitHub Actions to create and approve pull requests"
4. Guarda los cambios

## Cómo Desplegar el Wiki

### Opción 1: Despliegue Automático (Recomendado)

El método más simple es editar los archivos en `wiki/` y hacer push:

```bash
# 1. Edita un archivo del wiki
nano wiki/Home.md

# 2. Añade los cambios
git add wiki/

# 3. Haz commit
git commit -m "Actualizar página principal del wiki"

# 4. Push para desplegar automáticamente
git push origin main
```

El workflow de GitHub Actions detectará los cambios y desplegará el wiki automáticamente.

### Opción 2: Despliegue Manual desde GitHub

1. Ve a la pestaña "Actions" en tu repositorio
2. Selecciona "Deploy Wiki" en la lista de workflows
3. Haz clic en "Run workflow"
4. Selecciona la rama (main/master)
5. Haz clic en "Run workflow"

### Opción 3: Edición Directa del Wiki

Puedes editar el wiki directamente en GitHub:

1. Ve a https://github.com/Daniel-atilano/EMBODY-Mapas-Corporales/wiki
2. Haz clic en "Edit" en cualquier página
3. Realiza cambios y guarda

⚠️ **Advertencia**: Los cambios directos serán sobrescritos en el próximo despliegue automático desde el repositorio principal.

## Estructura del Wiki

```
wiki/
├── Home.md                      # Página principal (obligatoria)
├── Instrucciones-de-Uso.md      # Instrucciones de uso del proyecto
├── Acceso-a-Datos.md            # Guía de acceso a datos
├── Guia-Despliegue-Wiki.md      # Guía detallada de despliegue
└── images/                      # Imágenes del wiki (opcional)
    └── ejemplo.png
```

### Crear una Nueva Página

1. Crea un archivo `.md` en `wiki/`:
   ```bash
   touch wiki/Nueva-Pagina.md
   ```

2. Añade contenido Markdown:
   ```markdown
   # Mi Nueva Página
   
   Contenido aquí...
   ```

3. Añade un enlace en `Home.md`:
   ```markdown
   - [Nueva Página](Nueva-Pagina)
   ```

4. Commit y push:
   ```bash
   git add wiki/Nueva-Pagina.md wiki/Home.md
   git commit -m "Añadir nueva página al wiki"
   git push origin main
   ```

### Convenciones de Nombres

- Usa nombres descriptivos para archivos
- Separa palabras con guiones: `Mi-Pagina.md`
- La página principal debe llamarse `Home.md`
- Mantén consistencia con nombres en español

## Workflow Automático

### ¿Cómo Funciona?

El archivo `.github/workflows/deploy-wiki.yml` define un workflow que:

1. Se activa cuando hay cambios en `wiki/` en las ramas main/master
2. Hace checkout del repositorio principal
3. Hace checkout del repositorio wiki
4. Copia archivos de `wiki/` al repositorio wiki
5. Hace commit y push de los cambios

### Triggers del Workflow

El workflow se ejecuta cuando:

- Hay `push` a `main` o `master` con cambios en `wiki/**`
- Se ejecuta manualmente (`workflow_dispatch`)

### Verificar Ejecución

1. Ve a la pestaña "Actions" en GitHub
2. Busca el workflow "Deploy Wiki"
3. Verifica que tiene un ✓ verde (exitoso)

### Ver el Wiki Desplegado

- **URL del Wiki**: https://github.com/Daniel-atilano/EMBODY-Mapas-Corporales/wiki
- Accesible también desde la pestaña "Wiki" en el repositorio

## Solución de Problemas

### El Workflow No Se Ejecuta

**Síntomas**: No aparece ningún workflow en Actions después de hacer push

**Soluciones**:
1. Verifica que GitHub Actions esté habilitado en Settings → Actions
2. Confirma que los cambios están en el directorio `wiki/`
3. Asegúrate de hacer push a `main` o `master`

### Error de Permisos

**Síntomas**: Workflow falla con "Permission denied"

**Soluciones**:
1. Ve a Settings → Actions → General
2. En "Workflow permissions", selecciona "Read and write permissions"
3. Guarda y reintenta el workflow

### El Wiki No Se Actualiza

**Síntomas**: El workflow se ejecuta pero el wiki no cambia

**Soluciones**:
1. Limpia la caché del navegador (Ctrl+F5 o Cmd+Shift+R)
2. Verifica que los archivos en `wiki/` tienen extensión `.md`
3. Revisa los logs del workflow en Actions para errores
4. Confirma que los nombres de archivo no tienen espacios

### Conflictos de Contenido

**Síntomas**: Error de merge en el workflow

**Soluciones**:
1. El workflow intenta resolver conflictos automáticamente
2. Si persiste, puede ser necesario hacer pull del wiki manualmente:
   ```bash
   git clone https://github.com/Daniel-atilano/EMBODY-Mapas-Corporales.wiki.git
   # Resolver conflictos manualmente
   # Hacer commit y push
   ```

### Markdown No Se Renderiza Correctamente

**Síntomas**: El contenido se ve mal en el wiki

**Soluciones**:
1. Verifica la sintaxis Markdown con un editor o previsualizador
2. Confirma que los enlaces internos usan el formato correcto: `[Texto](Pagina-Sin-Extension)`
3. Asegúrate de que las imágenes están en `wiki/images/` y se referencian correctamente

## Mejores Prácticas

### 1. Control de Versiones

- Escribe mensajes de commit descriptivos
- Usa branches para cambios grandes
- Revisa cambios antes de hacer merge a main

### 2. Contenido

- Mantén páginas concisas y enfocadas
- Usa títulos y subtítulos claros
- Incluye enlaces de navegación entre páginas
- Actualiza `Home.md` con enlaces a nuevas páginas

### 3. Colaboración

- Usa pull requests para cambios importantes
- Solicita revisión de contenido técnico
- Documenta decisiones importantes en los commits

### 4. Mantenimiento

- Revisa enlaces rotos periódicamente
- Actualiza información obsoleta
- Mantén coherencia en estilo y formato

## Comandos Útiles

```bash
# Ver estado de archivos wiki
git status wiki/

# Ver diferencias en wiki
git diff wiki/

# Añadir todos los cambios del wiki
git add wiki/

# Commit con mensaje descriptivo
git commit -m "docs(wiki): actualizar página de instrucciones"

# Push para desplegar
git push origin main

# Ver historial de cambios del wiki
git log --oneline -- wiki/

# Crear nueva rama para cambios grandes
git checkout -b wiki/nueva-seccion
# ... hacer cambios ...
git push origin wiki/nueva-seccion
# Crear pull request en GitHub
```

## Recursos Adicionales

- **Wiki del Proyecto**: https://github.com/Daniel-atilano/EMBODY-Mapas-Corporales/wiki
- **GitHub Wiki Docs**: https://docs.github.com/en/communities/documenting-your-project-with-wikis
- **GitHub Actions Docs**: https://docs.github.com/en/actions
- **Markdown Guide**: https://www.markdownguide.org/basic-syntax/

## Contribuir

Para contribuir al wiki:

1. Fork el repositorio
2. Crea una rama para tus cambios: `git checkout -b wiki/mi-cambio`
3. Edita archivos en `wiki/`
4. Commit: `git commit -m "docs(wiki): descripción del cambio"`
5. Push: `git push origin wiki/mi-cambio`
6. Crea un Pull Request en GitHub

## Soporte

Si tienes problemas con el despliegue del wiki:

1. Consulta esta guía primero
2. Revisa la documentación en el wiki: [Guía de Despliegue](https://github.com/Daniel-atilano/EMBODY-Mapas-Corporales/wiki/Guia-Despliegue-Wiki)
3. Revisa los logs en la pestaña Actions
4. Abre un issue con detalles específicos:
   - Descripción del problema
   - Pasos para reproducir
   - Logs relevantes
   - Capturas de pantalla (si aplica)

---

**Licencia**: Este proyecto y su documentación están disponibles bajo los términos establecidos en el repositorio principal.

**Mantenedores**: Daniel Atilano y colaboradores
