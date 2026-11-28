# 🎯 Qué es "bien" en ba-ecobici

Un issue está terminado cuando cumple sus criterios de aceptación, la Definition of Done y los criterios del área a la que pertenece.

## ✅ Definition of Done

**Lo verifica la CI o los hooks:**

- [ ] Lint, tests y build en verde.
- [ ] El cambio trae tests que fallarían sin él.
- [ ] No hay secretos ni datos personales en el diff.
- [ ] El PR es chico: unas 400 líneas como máximo, sin contar archivos generados ni lockfiles.
- [ ] Los commits siguen Conventional Commits.

**Lo verifica el code review:**

- [ ] Cada criterio de aceptación del issue se cumple, con evidencia.
- [ ] No hay cambios que el issue no pidió.
- [ ] Si cambió un contrato (esquema, modelo de dbt, API), se actualizó sin romper a quien lo usa.
- [ ] El diseño es el más simple que resuelve el problema.
- [ ] Las dependencias nuevas estaban previstas en el plan del issue.

## 📐 Criterios por área

**`data-pipelines` y `analytics`**

- Correr la carga dos veces no duplica filas.
- Los números concilian: bronze = silver + rechazados, y los marts suman lo mismo que `fct_trips`.
- Cada métrica está definida y documentada, y cada dashboard responde una pregunta concreta.

**`data-science` y `ml`**

- Cada experimento parte de una hipótesis y se compara contra un baseline.
- Sin leakage: validación temporal y features calculadas solo con información del pasado.
- Es reproducible: el run queda registrado en MLflow con datos, parámetros y métricas.

## 📏 NFR del proyecto

Se suman desde [`docs/requerimientos.md`](../docs/requerimientos.md) cuando estén aprobados.
