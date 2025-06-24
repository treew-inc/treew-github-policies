# Workflows Centralizados – TreeW

Este repositorio contiene los flujos de trabajo reutilizables de GitHub Actions para garantizar el cumplimiento institucional de la [Directiva TW-DO-2025-01](https://github.com/...) sobre convenciones de mensajes de commits en los repositorios de TreeW.


## Objetivo

Establecer un punto único de mantenimiento y configuración para validar y controlar los Pull Requests en todos los proyectos de la organización, garantizando que los mensajes de commits cumplan con la estructura definida institucionalmente.


## Workflows disponibles

### ✅ `validate-commits.yml`
- **Función**: Verifica que todos los commits incluidos en un Pull Request cumplan con la convención `type: subject` (como `feat:`, `fix:`, etc.).
- **Uso recomendado**: Activación en todos los repositorios, vinculando mediante `workflow_call`.


## Cómo usar estos workflows

Cada repositorio debe incluir un archivo (contenido en la plantilla treew-repo-template) `.github/workflows/validate.yml` con el siguiente contenido para invocar el flujo centralizado:

```yaml
name: Validar commits (centralizado)

on:
  pull_request:
    types: [opened, synchronize, reopened]

jobs:
  validar:
    uses: treew-inc/treew-github-policies/.github/workflows/validate-commits.yml@main
```

## Ventajas del enfoque centralizado

- ✅ Una única fuente de verdad para toda la organización
- 🔄 Fácil mantenimiento y actualización global
- 📈 Asegura cumplimiento continuo sin depender del entorno local
- 🔐 Refuerza el control de calidad antes del merge


## Mantenimiento

Este repositorio debe ser actualizado únicamente por el equipo de calidad. Cualquier ajuste a las reglas de validación o comportamiento de los workflows se propagará automáticamente a todos los proyectos que lo referencien.
