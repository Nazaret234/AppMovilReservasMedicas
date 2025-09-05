# 📖 Estrategia de Versionamiento y Flujo de Ramas

## 🔹 Versionado Semántico
- **MAJOR** → Cambios incompatibles con versiones anteriores
- **MINOR** → Nuevas funcionalidades compatibles hacia atrás
- **PATCH** → Correcciones de errores y mejoras menores

### Ejemplo de flujo de versiones
- Versión inicial: `1.0.0`
- Nueva funcionalidad → `1.1.0`
- Corrección de bug → `1.1.1`
- Cambio incompatible → `2.0.0`

## 🔹 Estructura de GitFlow

### Ramas Principales
- **`main`** → Versión estable y lista para producción
- **`develop`** → Versión en desarrollo e integración continua

### Ramas de Soporte
- **`feature/*`** → Desarrollo de nuevas funcionalidades
- **`release/*`** → Preparación de versiones antes de producción
- **`hotfix/*`** → Correcciones urgentes en producción

## 🔹 Flujo de Trabajo

### 1. Desarrollo de Funcionalidades
```bash
# Crear nueva funcionalidad
git checkout -b feature/nueva-funcionalidad develop

# Después del desarrollo
git checkout develop
git merge --no-ff feature/nueva-funcionalidad
git branch -d feature/nueva-funcionalidad
```

### 2. Preparación de Release
```bash
# Crear rama de release
git checkout -b release/1.2.0 develop

# Finalizar release
git checkout main
git merge --no-ff release/1.2.0
git tag -a v1.2.0 -m "Release v1.2.0"

git checkout develop
git merge --no-ff release/1.2.0
git branch -d release/1.2.0
```

### 3. Correcciones Urgentes (Hotfix)
```bash
# Crear hotfix
git checkout -b hotfix/1.2.1 main

# Finalizar hotfix
git checkout main
git merge --no-ff hotfix/1.2.1
git tag -a v1.2.1 -m "Hotfix v1.2.1"

git checkout develop
git merge --no-ff hotfix/1.2.1
git branch -d hotfix/1.2.1
```

## 🔹 Reglas y Convenciones

- ✅ Cada **release** debe documentarse en `CHANGELOG.md`
- ✅ Uso obligatorio de **tags** para versiones:
  ```bash
  git tag -a v1.0.0 -m "Versión inicial"
  git push origin v1.0.0
  ```
- ✅ **Protección de ramas**: `main` y `develop` requieren pull requests
- ✅ **Nomenclatura consistente**: `feature/`, `release/`, `hotfix/`
- ✅ **Merge con --no-ff** para mantener historial de ramas
- ✅ **No commits directos** en `main` y `develop`

## 🔹 Comandos Útiles

```bash
# Sincronizar con remoto
git fetch origin
git checkout develop
git pull origin develop

# Limpiar ramas locales ya mergeadas
git branch --merged | grep -v "\*\|main\|develop" | xargs -n 1 git branch -d

# Ver historial de tags
git tag --sort=-version:refname

# Push de tags
git push origin --tags
```
