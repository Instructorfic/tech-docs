# Buenas prácticas de confirmaciones y versionamiento semántico

Este documento describe las **buenas prácticas de confirmaciones (commits)** y **versionamiento semántico (SemVer)** para todos los repositorios de proyectos de desarrollo de software.

Su objetivo es establecer un estándar profesional que permita mantener **historial de cambios claro, versionado coherente y releases predecibles**, facilitando colaboración, integración continua y preparación para entornos empresariales. 

Se basa en la especificación de **Conventional Commits 1.0.0** y en los principios de **Semantic Versioning (SemVer)**.


## Definición de conventional commits

**Conventional Commits** es un estándar para estructurar mensajes de confirmación de forma **humana y legible por máquina**, que facilita:

- Generación automática de **CHANGELOG**  
- Determinación de **versiones SemVer** según tipo de commit  
- Comunicación clara de la naturaleza de los cambios  
- Mejora de colaboración en proyectos con múltiples desarrolladores  

## Definición de confirmaciones (commits)

Una confirmación(commit) es una **unidad de cambio lógico en el código**, que debe describir de forma clara y concisa **qué se cambió y por qué**.  

Cada commit debe ser pequeño, enfocado y descriptivo, evitando mensajes genéricos como "update" o "arreglos varios".


## Estructura formal de una confirmación(commit)

<tipo>[alcance opcional][!]: <descripción breve>

[cuerpo opcional]

[pies de página opcionales]

### Componentes

- **tipo**: tipo de commit (`feat`, `fix`, `docs`, etc.)
- **alcance** *(opcional)*: módulo o área afectada entre paréntesis, ej.: `feat(ui): ...`
- **!** *(opcional)*: indica **cambio incompatible (breaking change)**
- **descripción breve**: resumen del cambio en presente, sin punto final
- **cuerpo** *(opcional)*: explicación detallada, puede ocupar varias líneas
- **pies de página** *(opcional)*: referencias, metadatos o BREAKING CHANGE

---

## Tipos de confirmaciones(commits) permitidas

| Tipo       | Descripción                                                                 | Impacto SemVer |
|------------|----------------------------------------------------------------------------|----------------|
| feat       | Nueva funcionalidad                                                        | MINOR          |
| fix        | Corrección de errores                                                      | PATCH          |
| docs       | Cambios en documentación                                                   | Ninguno        |
| style      | Cambios de formato o estilo que no afectan la lógica                        | Ninguno        |
| refactor   | Cambios internos que no modifican el comportamiento                        | Ninguno        |
| perf       | Optimización de rendimiento                                                | Ninguno        |
| test       | Agrega o modifica pruebas                                                  | Ninguno        |
| build      | Cambios en sistema de compilación o dependencias                            | Ninguno        |
| ci         | Cambios en integración continua / pipelines                                | Ninguno        |
| chore      | Tareas de mantenimiento o administrativas                                  | Ninguno        |
| revert     | Reversión de commits anteriores                                            | Ninguno        |

---

## Cambios incompatibles (Breaking Changes)

Se indican de **dos formas**:

1. Con `!` antes de `:` en el encabezado:

feat(api)!: cambia estructura de respuesta del servicio

2. En pie de página con `BREAKING CHANGE:`:

BREAKING CHANGE: la API ahora devuelve objetos completos en lugar de IDs

> Los cambios incompatibles corresponden a un incremento **MAJOR** en SemVer.

---

## Alcance (Scope) recomendado

- Indicar el módulo o paquete afectado.
- Ejemplos:

feat(login): agrega validación de campos  
fix(navigation): corrige crash al regresar pantalla  
refactor(viewmodel): optimiza manejo de estado

---

## Pies de página y metadatos

Permite incluir referencias y anotaciones importantes:

Refs: #123, #456  
Revisado-por: Profesor  
BREAKING CHANGE: ...

> Todos los pies de página deben ir **después de una línea en blanco** tras el cuerpo del commit.

---

## Buenas prácticas profesionales de confirmaciones

✔ Commits pequeños y frecuentes  
✔ Mensajes claros, consistentes y en presente  
✔ Un solo propósito por commit  
✔ Revisar que compile antes de commitear  
✔ Mínimo 4 commits por práctica  
✔ Cada commit debe ser **una unidad lógica de cambio**

---

## Ejemplos que siguen buenas prácticas de confirmaciones

feat(ui): agrega pantalla de login con Jetpack Compose  
fix(counter): corrige reinicio de estado al rotar pantalla  
docs: agrega guía de buenas prácticas de commits  
refactor(viewmodel): separa lógica de validación  
perf(images): optimiza carga de recursos  
build(gradle): actualiza versión Compose a 1.5  
feat(api)!: cambia estructura de respuesta JSON  
BREAKING CHANGE: la API ya no devuelve IDs sueltos, sino objetos completos

---

## Ejemplos que no siguen buenas prácticas de confirmaciones

update proyecto  
arreglos varios  
version final  
subiendo tarea

- Mensajes genéricos  
- Sin tipo válido  
- Sin alcance ni descripción clara  

---

## Flujo recomendado de trabajo (ejemplo)

1. Crear rama desde `main`:

git checkout -b practica-3-navegacion

2. Realizar commits siguiendo estas buenas prácticas  
3. Sincronizar con el repositorio remoto (push)  
4. Integrar cambios con la rama objetivo (pull / merge request) 
5. Revisar con checklist  
6. Merge → `CHANGELOG` y versión SemVer actualizados automáticamente

---

## Versionamiento semántico (SemVer)

SemVer sigue el formato **MAJOR.MINOR.PATCH**, donde:

- **MAJOR** → Cambios incompatibles con versiones anteriores (breaking changes)  
- **MINOR** → Nuevas funcionalidades compatibles con versiones anteriores  
- **PATCH** → Correcciones de errores y mejoras menores sin romper compatibilidad

### Relación con los Commits

| Tipo de commit | Impacto en versión |
|----------------|------------------|
| feat            | MINOR           |
| fix             | PATCH           |
| BREAKING CHANGE | MAJOR           |

> El uso correcto de Conventional Commits permite **generar CHANGELOG y determinar la versión automáticamente**.

---

## Buenas prácticas profesionales de versionado

✔ Definir claramente la política de commits antes de empezar un proyecto  
✔ Evitar commits que rompan compatibilidad sin marcar `BREAKING CHANGE`  
✔ Realizar releases frecuentes siguiendo SemVer  
✔ Generar changelog automático a partir de commits  
✔ Mantener consistencia en nombres de ramas y merges

---

## Ejemplo de flujo integrado de commits y versionado

feat(auth): agrega login con Google  
fix(ui): corrige alineación de botones  
feat(api)!: cambia endpoint de autenticación  
BREAKING CHANGE: endpoint antiguo ya no responde

- Primer commit → MINOR  
- Segundo commit → PATCH  
- Tercer commit → MAJOR  

> Al generar la release, la versión SemVer se incrementa automáticamente según los commits.