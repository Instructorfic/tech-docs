# Buenas Prácticas de Versionamiento Semántico – SemVer

Este documento describe las **buenas prácticas de versionamiento semántico (Semantic Versioning, SemVer)** para proyectos de desarrollo de software. 

El objetivo es establecer un estándar profesional que permita **versiones predecibles, coherentes y claras**, facilitando la colaboración, pruebas, automatización de releases y preparación para entornos empresariales.

Referencia oficial: [https://semver.org](https://semver.org)

---

## Definición y objetivo

**Versionamiento semántico (SemVer)** es un sistema de numeración de versiones que comunica claramente la magnitud de los cambios en el software.  

Permite:

- Identificar fácilmente cambios incompatibles, nuevas funcionalidades o correcciones  
- Integrar con herramientas de automatización (generación de `CHANGELOG.md`, tags, CI/CD)  
- Prevenir conflictos y errores en despliegues  
- Preparar a los estudiantes para flujos profesionales de desarrollo

---

## Formato de versión

El formato estándar es:

MAJOR.MINOR.PATCH


- **MAJOR** → Cambios incompatibles con versiones anteriores (**breaking changes**)  
- **MINOR** → Nuevas funcionalidades compatibles (`feat`)  
- **PATCH** → Corrección de errores (`fix`)  

Opcionalmente, se pueden incluir versiones preliminares o metadata:

- 1.2.0-alpha.1
- 1.2.0-beta.2
- 1.2.0+build.123


- `-alpha`, `-beta` → versiones preliminares  
- `+build` → información de compilación o CI/CD

---

## Relación con buenas prácticas de confirmaciones (Conventional Commits)

El versionamiento semántico se integra directamente con la política de commits (`buenas-practicas-commits.md`):

| Tipo de Commit         | Impacto en SemVer | Ejemplo |
|------------------------|-----------------|---------|
| feat                   | MINOR           | `feat(ui): agrega pantalla de login` |
| fix                    | PATCH           | `fix(api): corrige null pointer en login` |
| feat + BREAKING CHANGE | MAJOR           | `feat(api)!: elimina endpoint antiguo` |
| fix + BREAKING CHANGE  | MAJOR           | `fix(auth)!: cambia token de validación` |
| Otros (docs, style…)   | Ninguno         | `docs: actualiza README` |

> Todos los commits deben seguir la política de `buenas-practicas-commits.md` para que el versionado automático funcione correctamente.

---

## Flujo recomendado de versionamiento

1. Crear rama de feature o fix desde `main`.  
2. Realizar commits siguiendo la política de commits.  
3. Push a GitHub y crear Pull Request.  
4. Merge → La herramienta de versionado automático analiza los commits.  
5. Calcula nueva versión SemVer, genera `CHANGELOG.md` y crea tags en GitHub.  

**Herramientas recomendadas:**

- `standard-version`  
- `semantic-release`  

> Este flujo simula un entorno profesional y prepara a los estudiantes para prácticas empresariales.

---

## Ejemplos de evolución de versiones

### Escenario 1: Nueva funcionalidad compatible

- feat(ui): agrega botón de compartir
- Versión actual: `1.3.0`  
- Commit tipo `feat` → incrementa MINOR  
- Nueva versión: `1.4.0`

### Escenario 2: Corrección de bug

- fix(api): corrige manejo de null en login
- Versión actual: `1.4.0`  
- Commit tipo `fix` → incrementa PATCH  
- Nueva versión: `1.4.1`

### Escenario 3: Cambio incompatible (breaking change)

- feat(api)!: elimina endpoint antiguo
- BREAKING CHANGE: la API ahora requiere autenticación OAuth2
- Versión actual: `1.4.1`  
- Commit con `!` o `BREAKING CHANGE` → incrementa MAJOR  
- Nueva versión: `2.0.0`

### Escenario 4: Pre-release
- feat(ui): nueva pantalla beta
- Versión base: `2.0.0`  
- Versión pre-release: `2.1.0-beta.1`  
- Luego de validación: `2.1.0`  

---

## Consideraciones importantes

- No incrementar **MAJOR** sin documentar claramente el breaking change  
- Cada **MINOR** debe ser compatible con versiones anteriores  
- Cada **PATCH** no debe romper funcionalidad existente  
- Versionar solo desde ramas estables (`main`/`master`)  
- Mantener consistencia entre versión en código, tags y CHANGELOG  
- Documentar claramente todos los breaking changes y funcionalidades nuevas

---

## Buenas prácticas de integración con CI/CD

✔ Configurar workflows en GitHub Actions o Azure Pipelines que:  

- Detecten commits válidos según `buenas-practicas-commits.md`  
- Ejecuten `standard-version` o `semantic-release` al merge de PR  
- Actualicen automáticamente `CHANGELOG.md` y la versión del proyecto  
- Creen tags de release en GitHub automáticamente  

✔ Revisar el CHANGELOG generado para coherencia y claridad  
✔ Mantener documentación de breaking changes detallada  
✔ Simular un flujo profesional de desarrollo empresarial

---

## Referencias

- [Semantic Versioning 2.0.0](https://semver.org/)  
- [Conventional Commits 1.0.0](https://www.conventionalcommits.org/)  
- [Guía práctica de versionamiento en proyectos de software](https://semver.org/spec/v2.0.0.html)
