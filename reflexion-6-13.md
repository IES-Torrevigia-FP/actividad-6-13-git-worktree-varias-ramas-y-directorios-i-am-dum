# 🧠 Reflexión sobre Git Worktree

### 1. Ventajas de Worktree
Frente a cambiar de rama en el mismo directorio (`git checkout`), la principal ventaja es **no tener que lidiar con archivos modificados o sin commitear** (evitamos el uso constante de `git stash`). Puedes tener un servidor corriendo en una rama mientras editas otra en un directorio distinto.

Frente a clonar el repositorio varias veces, la ventaja es el **ahorro de espacio y la sincronización**. Todos los worktrees comparten el mismo directorio `.git`, por lo que si haces un `fetch` en uno, los objetos están disponibles para todos inmediatamente, sin duplicar el peso del historial.

### 2. Situaciones reales de uso
1. **Revisión de Pull Requests (PRs):** Estás en medio de una funcionalidad compleja y un compañero te pide que revises su código. En lugar de guardar tus cambios y cambiar de rama, abres un worktree en una carpeta temporal, revisas el código, lo pruebas y luego lo borras, sin tocar tu entorno de desarrollo actual.
2. **Hotfixes urgentes:** Si surge un error crítico en producción (`main`) mientras trabajas en una rama de larga duración, puedes crear un worktree de `main`, aplicar el fix, subirlo y volver a tu tarea original de forma instantánea.

### 3. Buenas prácticas
- **Nomenclatura:** Usar un prefijo claro para los directorios de worktree (como `wt-` o `.worktrees/`) para que sean fáciles de identificar y excluir en el `.gitignore` si fuera necesario.
- **Limpieza:** Ejecutar `git worktree list` periódicamente para ver qué carpetas siguen activas y usar `git worktree prune` para limpiar referencias si hemos borrado carpetas a mano.
- **Ubicación:** Crear los worktrees fuera del directorio principal (en el nivel superior) para evitar anidamientos accidentales.
