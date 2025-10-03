---
applyTo: '**'
---
# Guía de Commits — Conventional Commits

**Note:** All commit messages must be written in **English**.

Esta guía sigue el estándar **[Conventional Commits v1.0.0](https://www.conventionalcommits.org/en/v1.0.0/)**.
Escribe mensajes **cortos**, en **tiempo presente** (modo imperativo) y **claros**.

---

## 1) Estructura del mensaje

```
<tipo>(<alcance opcional>)!?: <descripción breve>

<cuerpo opcional>

<pié opcional: referencias, BREAKING CHANGE, co-autores>
```

- **tipo**: categoría del cambio (ver sección Tipos)
- **alcance**: módulo/área afectada (`api`, `ui`, `db`, `build`, `deps`, `infra`, etc.)
- **!**: indica **breaking change**
- **descripción**: máx. ~50–72 caracteres, sin punto final, en presente
- **cuerpo**: qué y por qué (si aporta claridad); líneas de máx. 72 caracteres
- **pié**: referencias a issues, notas de ruptura, co-autores

> **Regla de oro:** La línea del encabezado debe explicar **qué hace** el cambio, no **cómo**.

---

## 2) Tipos de commit (comunes)

- `feat`: agrega funcionalidad
- `fix`: corrige un bug
- `docs`: actualiza documentación
- `style`: cambios de formato (espacios, comas) sin lógica
- `refactor`: mejora código sin cambiar comportamiento
- `perf`: mejora rendimiento
- `test`: agrega/actualiza pruebas
- `build`: cambios en build, dependencias, empaquetado
- `ci`: cambios en pipelines de CI/CD
- `chore`: tareas varias (sin afectar src ni tests)
- `revert`: revierte un commit anterior

---

## 3) Ejemplos (cortos y en presente)

**Encabezados simples**

- `feat(api): add search endpoint`
- `fix(ui): fix modal focus`
- `docs(readme): update usage example`
- `style: format code with Prettier`
- `refactor(core): extract email validator`
- `perf(db): reduce duplicate queries`
- `test(auth): add expiration tests`
- `build(deps): bump axios to v1`
- `ci: add npm cache`
- `chore: clean temporary files`
- `revert: revert feat(api): add search endpoint`

**Con cuerpo y pié**

```
fix(auth): fix signature verification

Adjust validation order to avoid false negatives.

Refs #456
```

```
feat(auth)!: replace JWT with PASETO

Simplifies validation and improves token security.

BREAKING CHANGE: JWT tokens are no longer valid. Clients must
migrate to PASETO.
Closes #123
```

```
refactor(core): extract conversion logic

Extract a pure function to ease testing and reuse.

Co-authored-by: Ana Pérez <ana@example.com>
```

---

## 4) Breaking changes

Decláralos de **una** de estas formas:

1. Añade `!` en el encabezado: `feat(api)!: cambia contrato de respuesta`
2. O usa un pié con `BREAKING CHANGE:` (mayúsculas), seguido de la nota

> Siempre explica **qué rompe** y **qué acción** debe tomar quien consume tu cambio.

---

## 5) Referencias a issues y PRs

En el **pié** del commit:

- `Closes #123`, `Fixes #123`, `Resolves #123` para cerrar
- `Refs #456` para referenciar sin cerrar
- `Co-authored-by: Nombre <email>` para coautoría

---

## 6) Buenas prácticas

- Escribe en **presente** e **imperativo**: "add", "fix", "update"
- Sé **específico** y **breve** en el encabezado; detalla en el cuerpo si es necesario
- **No** termines el encabezado con punto
- Limita el encabezado a ~50–72 caracteres
- Usa el **alcance** cuando aporte contexto
- Un commit debe tener **un propósito** (pequeño y coherente)
- Incluye `test` cuando agregas `feat` o `fix`
- Documenta en `docs` si cambia el comportamiento
- Usa `revert` en lugar de commits que "deshacen" sin contexto
- Evita emojis en el encabezado (no forman parte del estándar)

---

## 7) Checklist antes de commitear

- [ ] El tipo refleja el cambio
- [ ] El encabezado es corto, en presente y sin punto final
- [ ] Alcance añadido si ayuda
- [ ] Cuerpo (opcional) explica **por qué**
- [ ] Referencias/`BREAKING CHANGE` (si aplica)
- [ ] Pruebas y docs actualizadas (si aplica)

---

## 8) Plantillas rápidas

```
feat(<scope>): <what it adds>

<why / details>

Closes #<id>
```

```
fix(<scope>): <what it fixes>

<root cause / how it is validated>

Refs #<id>
```

```
<type>(<scope>)!: <what changes>

<explain the impact>

BREAKING CHANGE: <what breaks and migration steps>
```

---

> Más detalles en la especificación oficial: https://www.conventionalcommits.org/en/v1.0.0/
