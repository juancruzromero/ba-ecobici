# 📋 Requerimientos

> Qué tiene que poder hacer cada persona con el producto y con qué calidad. Cada issue `type:feat` referencia un FR con la label `req:FR-XXX`. La fase es orientativa y se revisa al arrancar cada una (ver [`plan.md`](plan.md)).

## Contexto

Producto de datos sobre Ecobici para entender cómo se mueve Buenos Aires en bici y anticipar la disponibilidad de cada estación. Sirve para quien va y vuelve del trabajo en bici y para quien analiza la movilidad de la ciudad.

## Requerimientos funcionales

| Código | Historia | Requiere | Fase | Estado |
|---|---|---|---|---|
| FR-001 | Como analista, quiero ver la cantidad de viajes por mes de todo el histórico (2010–2026), para entender cómo evolucionó el uso del sistema. | — | F1 | Aprobado |
| FR-002 | Como analista, quiero ver las estaciones en un mapa con sus salidas y llegadas, para identificar las más usadas. | FR-001 | F1 | Aprobado |
| FR-003 | Como analista, quiero ver en qué comunas y barrios empiezan y terminan los viajes, para saber de dónde sale y adónde llega la gente. | FR-002 | F2 | Aprobado |
| FR-004 | Como analista, quiero ver el perfil de los usuarios (edad, género, antigüedad) y cuánto viajan, para entender quién usa el sistema. | FR-001 | F1 | Aprobado |
| FR-005 | Como analista, quiero ver los flujos de viajes entre comunas y barrios por franja horaria, para entender los movimientos pendulares (al centro a la mañana, a la periferia a la tarde). | FR-003 | F2 | Aprobado |
| FR-006 | Como analista, quiero ver qué estaciones se vacían y cuáles se llenan en cada momento del día, para entender el desbalance del sistema. | FR-002 | F2 | Aprobado |
| FR-007 | Como analista, quiero ver cuántos usuarios siguen viajando en los meses posteriores a su alta, para entender la retención. | FR-004 | F2 | Aprobado |
| FR-008 | Como analista, quiero ver las estaciones agrupadas por su patrón de uso horario (residencial, oficinas, recreativa), para entender el rol de cada zona. | FR-002 | F2 | Aprobado |
| FR-009 | Como analista, quiero ver cómo cambia el uso según el clima y los feriados, para entender qué lo hace subir o bajar. | FR-001 | F6 | Aprobado |
| FR-010 | Como ciclista, quiero ver cuántas bicis y lugares libres hay ahora en cada estación, para decidir si salgo en bici. | — | F4 | Aprobado |
| FR-011 | Como ciclista, quiero consultar en una app web el mapa de estaciones con su disponibilidad y los principales insights, sin entrar a una herramienta de análisis. | FR-010 | F5 | Aprobado |
| FR-012 | Como ciclista, quiero ver cuántas bicis se espera que se retiren de una estación en las próximas horas, para anticipar si va a quedar alguna. | FR-011 | F6–F7 | Aprobado |
| FR-013 | Como analista, quiero comparar las predicciones con lo que pasó realmente, para saber cuánto confiar en ellas. | FR-012 | F7 | Aprobado |
| FR-014 | Como ciclista, quiero ver cuántas bicis y lugares libres va a tener una estación en las próximas horas, para planificar la ida y la vuelta del trabajo. | FR-010, FR-012 | F8 | Aprobado |
| FR-015 | Como ciclista, quiero acceder a la app desde internet, para usarla en cualquier momento. | FR-011 | F9 | Aprobado |

## Requerimientos no funcionales

| Código | Requisito | Estado |
|---|---|---|
| NFR-001 | Todo el entorno se levanta con un solo comando en una laptop, sin pasos manuales. | Aprobado |
| NFR-002 | Los números concilian: cada viaje del archivo original está en el modelo o en rechazados con su motivo (diferencia 0). | Aprobado |
| NFR-003 | Volver a correr una carga no duplica datos. | Aprobado |
| NFR-004 | Los dashboards responden en menos de 2 s. | Aprobado |
| NFR-005 | Los datos históricos se actualizan solos, dentro de los 7 días posteriores a que la Ciudad publique un mes nuevo. | Aprobado |
| NFR-006 | La disponibilidad actual tiene como máximo 10 minutos de atraso. | Aprobado |
| NFR-007 | Una predicción se publica solo si supera a un baseline ingenuo (por ejemplo, "lo mismo que la semana pasada a esa hora"). | Aprobado |
| NFR-008 | Si la calidad de las predicciones se degrada, el modelo se reentrena, y el nuevo reemplaza al vigente solo si es mejor. | Aprobado |
| NFR-009 | Sin secretos ni datos personales en el repo. | Aprobado |
| NFR-010 | La app y los dashboards citan la fuente de los datos, como pide la licencia CC-BY-2.5-AR. | Aprobado |
| NFR-011 | La app se usa cómodamente en el celular, en pantallas desde 360 px de ancho. | Aprobado |
| NFR-012 | Tenerlo en internet cuesta 20 USD por mes o menos. | Aprobado |

## Decisiones caras de cambiar

Cada decisión aceptada se documenta con un ADR en `docs/adr/`.

| Código | Decisión | Estado |
|---|---|---|
| DEC-001 | Se predicen primero los **retiros** por estación, aprendidos del histórico de viajes (FR-012). La **disponibilidad** (FR-014) llega cuando haya suficientes datos en tiempo real. | Aceptada |
| DEC-002 | Cómo identificar una estación en el tiempo cuando un mismo ID corresponde a estaciones distintas en distintos años. | Propuesta |
| DEC-003 | Qué ventana de datos usar para predecir: todo el histórico o solo los años recientes. | Propuesta |
| DEC-004 | La app es pública y sin cuentas. Las cuentas recién aparecen si llegan las funciones personales. | Propuesta |

## Para más adelante

Ideas fuera del backlog actual. Se convierten en historias cuando llegue su momento.

- **Funciones personales**, al final del desarrollo: guardar las estaciones de casa y trabajo, y recibir un aviso si no va a haber bici o lugar.
- **Más insights con modelos:** regresiones lineales y clasificaciones.
- **Dónde poner nuevas estaciones:** demanda sin cubrir, huecos de cobertura y población por zona.
- **Estado de la flota:** bicis y anclajes fuera de servicio por estación, si el feed lo publica. A nivel de bici individual, solo si aparece un ID de bicicleta en los datos.
