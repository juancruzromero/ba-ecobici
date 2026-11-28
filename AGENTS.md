# AGENTS.md — ba-ecobici

Instrucciones para cualquier persona o agente que trabaje en este repo. Todo el trabajo vive en GitHub: issues, PRs, milestones y un Project.

## 🧾 Proyecto

- **Qué es:** plataforma de datos y ML sobre Ecobici (bicis públicas de Buenos Aires): todo el histórico, near real time y predicción de disponibilidad por estación. Vitrina de data engineering, data science y MLOps.
- **Plan y fases:** [`docs/plan.md`](docs/plan.md).
- **Requerimientos:** [`docs/requerimientos.md`](docs/requerimientos.md) (FR/NFR).
- **Contexto corto y vara de calidad:** [`cerebro/`](cerebro/).
- **Perfiles:** `data-pipelines`, `analytics`, `data-science`, `ml` y, desde F5, `web`.
- **Gestión:** issues, milestones (uno por fase) y un único Project en GitHub (`juancruzromero/ba-ecobici`).

## 📏 Reglas

- **Idioma:** código en inglés (nombres, comentarios, tablas y columnas). Todo lo demás en español rioplatense: docs, issues, PRs, commits y ADRs.
- **Los commits son del usuario:** sin `Co-Authored-By` ni firmas de IA. Commit, push, merge, release y deploy, solo con su OK explícito.
- **No hay issue sin requerimiento** (salvo `type:bug` y `type:chore`). Todo PR cierra un issue con `Closes #N`.
- **TDD:** un test en rojo → código mínimo → verde. Frenar ante decisiones de diseño, dependencias nuevas o dos intentos fallidos.
- **Nada de secretos:** no leer ni escribir `.env` reales; solo `.env.example`.
- **Diseño simple:** sumar una herramienta solo cuando el problema existe, y con un ADR si es cara de cambiar.
- **PRs chicos:** diff de hasta ~400 líneas (sin generados ni lockfiles).

## 🏷️ Convenciones

- **Ramas:** `<tipo>/<issue>-<slug>` (por ejemplo, `feat/12-load-trips-bronze`).
- **Commits:** Conventional Commits, `feat(FR-001): … (#12)`. Merge solo con rebase.
- **Labels:** `req:FR-XXX`, `type:feat|bug|chore|exp`.
- **Área (campo del Project):** indica el perfil del issue y, con eso, con qué criterios se revisa. Un área por issue, la que domina el trabajo; si hay dos de peso parecido, probablemente haya que partirlo.

  | Área | Qué entra | Ejemplos |
  |---|---|---|
  | `data-pipelines` | Ingesta y transformación: que los datos lleguen, se limpien y concilien | carga a bronze, modelos de silver, reconciliación, Dagster, GBFS |
  | `analytics` | Métricas, marts y dashboards que responden una pregunta | flujos pendulares por comuna, mart origen-destino, dashboards de Metabase |
  | `data-science` | Análisis y experimentos cuyo resultado es conocimiento | EDA, clustering de estaciones, efecto de la lluvia, comparar baselines |
  | `ml` | Modelos que corren en producción y su ciclo de vida | entrenamiento, MLflow, champion/challenger, predicción batch, Evidently |
  | `web` | API y frontend | FastAPI, React, mapas con MapLibre, Metabase embebido |
  | `infra` | Lo que hace correr todo | compose, imágenes Docker, CI/CD, Terraform, backups |
  | `docs` | Documentación y proceso, sin código | plan, ADRs, `AGENTS.md`, requerimientos |
- **Versiones:** SemVer 0.x; tag anotado `vX.Y.Z` sobre `main` al cerrar cada fase.
- **ADRs:** `docs/adr/NNNN-<titulo>.md`, formato MADR resumido.

## 📚 Documentación

Un solo lugar para cada cosa: el plan en `docs/plan.md`, los requerimientos en `docs/requerimientos.md`, las decisiones en `docs/adr/` y la arquitectura en `docs/arquitectura.md`.
