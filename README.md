### 🔹 Definiciones
- **MAJOR** → Cambios incompatibles con versiones anteriores.
- **MINOR** → Nuevas funcionalidades compatibles hacia atrás.
- **PATCH** → Correcciones de errores y mejoras menores.

### 🔹 Ejemplo de flujo
- Versión inicial: `1.0.0`
- Nueva funcionalidad → `1.1.0`
- Corrección de bug → `1.1.1`
- Cambio incompatible → `2.0.0`

### 🔹 Reglas adicionales
- Cada **release** debe documentarse en `CHANGELOG.md`.
- Uso de **tags en Git** para versiones:
  ```bash
  git tag -a v1.0.0 -m "Versión inicial"
  git push origin v1.0.0
