# Captura de Requisitos Software

**Asignatura:** Ingeniería del Software (Grado en Inteligencia Artificial) · **Grupo:** IS-P1-G1 · **Curso:** 2026-2027

Este documento recoge los requisitos funcionales (RF) y los requisitos de dominio/tecnológicos (RD) extraídos del caso de estudio de monitorización y detección predictiva de incidencias en infraestructuras ferroviarias.

## Requisitos funcionales (RF)

| Identificador | Nombre | Descripción |
|---|---|---|
| RF1 | Leer datos de las vías | El sistema debe incorporar un elemento que lea los valores de voltaje de las vías desde un fichero CSV (RD3). |
| RF1.1 | Leer registros del fichero | El sistema debe extraer de cada registro del fichero la hora (RD4), el identificador del dispositivo, el estado (RD5) y el voltaje (RD6). |
| RF1.2 | Interpretar estado de la vía | El sistema debe interpretar el estado de cada registro y mostrarlo como "ocupada" o "libre" según la codificación de RD5. |
| RF2 | Gestionar dispositivos de vía | El sistema debe permitir que cada vía de tren tenga múltiples dispositivos, separados entre sí según la distancia definida en RD7. |
| RF2.1 | Identificar dispositivo | El sistema debe asignar a cada dispositivo un identificador único, que se usa para asociarle sus lecturas e incidencias. |
| RF3 | Detectar y predecir incidencias | El sistema debe incorporar un módulo inteligente (RD8) que detecte y prediga incidencias a partir de los valores. Solo se consideran los tipos de RF3.1 y RF3.2; los otros 7 de los 9 tipos posibles quedan fuera del alcance. |
| RF3.1 | Detectar ausencia de datos | El sistema debe detectar la incidencia "ausencia de datos por bloqueo prolongado" cuando un dispositivo de vía no emita datos durante un periodo superior a 2 minutos. |
| RF3.2 | Detectar salto de voltaje | El sistema debe detectar la incidencia "salto de frecuencia" cuando el voltaje de un dispositivo varíe al menos 0.5 V entre dos lecturas consecutivas. |
| RF3.3 | Predecir incidencias | El sistema debe predecir la aparición de incidencias de los tipos RF3.1 y RF3.2 a partir de los valores de las lecturas. |
| RF4 | Gestionar suscripción a incidencias | El sistema debe incorporar un módulo de publicación y suscripción de incidencias. |
| RF4.1 | Publicar incidencia | Los usuarios del sistema deben poder publicar incidencias de los diferentes tipos considerados (RF3.1 y RF3.2). |
| RF4.2 | Suscribirse a incidencias | Los gestores del sistema deben poder suscribirse a los diferentes tipos de incidencias. |
| RF5 | Visualizar incidencias | El sistema debe incorporar un módulo de visualización que muestre gráficamente las incidencias en función de los valores de voltaje. |
| RF5.1 | Mostrar datos por minuto | La gráfica debe mostrar la información con resolución de un minuto. |
| RF5.2 | Mostrar estados | La gráfica debe mostrar el estado (0 o 1) de cada dato, según la codificación de RD5. |
| RF5.3 | Mostrar voltajes | La gráfica debe mostrar el valor de voltaje de cada dato, en voltios (RD6). |
| RF5.4 | Marcar incidencias | La gráfica debe indicar cuándo se produce una incidencia y de qué tipo. |

## Requisitos de dominio / tecnológicos (RD)

| Identificador | Nombre | Descripción |
|---|---|---|
| RD1 | Aplicación Web | El software debe desarrollarse como una aplicación Web. |
| RD2 | Protocolos HTTP/REST | La comunicación entre cliente y servidor debe basarse en los protocolos HTTP/REST. |
| RD3 | Formato de entrada CSV | Los datos de las vías deben recibirse en un fichero en formato CSV. |
| RD4 | Formato de hora | La hora de cada registro debe tener el formato HH:MM:SS:MS. |
| RD5 | Codificación del estado | El estado de la vía es un valor binario: 0 indica ocupado (hay tren en la vía) y 1 indica libre (no hay tren en la vía). |
| RD6 | Unidad de voltaje | Las señales eléctricas de los dispositivos se expresan en voltios (V). |
| RD7 | Separación de dispositivos | Los dispositivos de una misma vía deben estar separados entre sí por una distancia de 200 o de 500 metros. |
| RD8 | Algoritmo de Machine Learning | La detección y predicción de incidencias debe basarse en un algoritmo de Machine Learning. |
