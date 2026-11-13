# Patrones de diseño aplicados

**Práctica 1 · Ingeniería del Software · Grupo IS-P1-G1**

## Patrones aplicados

| Patrón | Clases | Requisitos | Para qué sirve |
|---|---|---|---|
| **Strategy** | `DetectorIncidencia` (clase abstracta), `DetectorAusenciaDatos`, `DetectorSaltoVoltaje`, `ModeloML` | RF3, RF3.1, RF3.2, RD8 | Cada tipo de incidencia se detecta a su manera. `ServicioDeteccion` usa la clase abstracta sin saber qué detector concreto tiene delante. Para añadir otro tipo de incidencia solo hay que crear una clase nueva. Los detectores usan el `ModeloML` para clasificar y predecir |
| **Observer** (publicación-suscripción) | `GestorSuscripciones` (sujeto), `Suscriptor` (clase abstracta), `Gestor` | RF4, RF4.1, RF4.2, RF3 | `GestorSuscripciones` guarda qué gestores están suscritos a cada tipo de incidencia. Cuando se publica una incidencia (la registra un usuario o la detecta el sistema), avisa a los gestores suscritos a ese tipo. Quien detecta no necesita saber a quién avisar |
| **Adapter** | `LectorDatos` (clase abstracta), `LectorCSV` | RF1, RD3, RD4–RD6 | El sistema trabaja con `LectorDatos`, y `LectorCSV` adapta el fichero CSV a lecturas con hora, estado y voltaje. Si los datos llegan en otro formato, solo hay que crear otra clase lectora |

## Patrón descartado

**Facade (fachada):** no creamos una clase única por la que pasen todas las peticiones. La Lógica de Negocio ya tiene un `ControladorREST` y servicios específicos (`ServicioIngesta`, `ServicioDeteccion`, `ServicioVisualizacion`, `GestorSuscripciones`). Una fachada sería una clase más sin ventaja y acumularía demasiadas responsabilidades.
