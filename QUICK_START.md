# Quick Start: Desplegar el Wiki

Este documento proporciona una guía rápida para desplegar el wiki de EMBODY Mapas Corporales.

## ¿Qué se ha configurado?

✅ **GitHub Actions Workflow**: `.github/workflows/deploy-wiki.yml`  
✅ **Contenido del Wiki**: Directorio `wiki/` con 4 páginas  
✅ **Documentación Completa**: `WIKI_DEPLOYMENT.md`  
✅ **README Actualizado**: Con enlaces al wiki

## Cómo funciona

1. **Editas** archivos en `wiki/`
2. **Commit** y **push** a la rama `main` o `master`
3. **GitHub Actions** despliega automáticamente al wiki

## Páginas del Wiki Creadas

- `wiki/Home.md` - Página principal del wiki
- `wiki/Instrucciones-de-Uso.md` - Instrucciones de uso del proyecto
- `wiki/Acceso-a-Datos.md` - Guía de acceso a datos
- `wiki/Guia-Despliegue-Wiki.md` - Guía detallada de despliegue

## Próximos Pasos

### 1. Mergear este PR

Una vez que este PR sea mergeado a `main` o `master`, el workflow estará activo.

### 2. Verificar el Despliegue

Después del merge, el workflow se ejecutará automáticamente:

1. Ve a: https://github.com/Daniel-atilano/EMBODY-Mapas-Corporales/actions
2. Busca el workflow "Deploy Wiki"
3. Verifica que se ejecute exitosamente (✓ verde)

### 3. Ver el Wiki Desplegado

Accede al wiki en:
- https://github.com/Daniel-atilano/EMBODY-Mapas-Corporales/wiki

### 4. Actualizar el Wiki en el Futuro

```bash
# Edita el contenido
nano wiki/Home.md

# Commit y push
git add wiki/
git commit -m "Actualizar wiki"
git push origin main

# El workflow se ejecutará automáticamente
```

## Configuración de Permisos (Si es necesario)

Si el workflow falla con error de permisos:

1. Ve a Settings → Actions → General
2. En "Workflow permissions":
   - Selecciona "Read and write permissions"
   - Marca "Allow GitHub Actions to create and approve pull requests"
3. Guarda los cambios

## Ejecución Manual del Workflow

Para ejecutar el workflow manualmente:

1. Ve a Actions → Deploy Wiki
2. Haz clic en "Run workflow"
3. Selecciona la rama (main)
4. Haz clic en "Run workflow"

## Recursos

- **Documentación Completa**: Ver `WIKI_DEPLOYMENT.md`
- **Wiki del Proyecto**: https://github.com/Daniel-atilano/EMBODY-Mapas-Corporales/wiki
- **Workflow File**: `.github/workflows/deploy-wiki.yml`

## Solución Rápida de Problemas

**El workflow no se ejecuta:**
- ✅ Verifica que GitHub Actions está habilitado
- ✅ Confirma que hay cambios en `wiki/` en main/master

**Error de permisos:**
- ✅ Configura permisos de GitHub Actions (ver arriba)

**El wiki no se actualiza:**
- ✅ Limpia caché del navegador (Ctrl+F5)
- ✅ Revisa logs en Actions

## Contacto

Para más información, consulta `WIKI_DEPLOYMENT.md` o abre un issue en el repositorio.
