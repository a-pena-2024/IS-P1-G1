**Práctica 1 · Ingeniería del Software · Grupo IS-P1-G1 · Semana 2**
 
## Estilo arquitectónico
 
Hemos elegido un estilo **cliente/servidor en tres capas** (Cliente, Lógica de Negocio y Acceso a Datos), con una capa de nivel inferior, el **Dominio**, que contiene las clases del problema y que importan las otras dos. Los requisitos RD1 y RD2 piden separar la parte web del servidor. Cada capa solo usa a la que tiene debajo.
 
| Capa | Qué hace | Requisitos |
|---|---|---|
| **Cliente** | Aplicación web: gráficas y panel de incidencias y suscripciones | RF4.1, RF4.2, RF5, RD1, RD2 |
| **Lógica de Negocio** | Servidor REST que coordina el sistema. Incluye la detección de incidencias y el módulo de Machine Learning | RF3, RF4, RF5, RD2, RD8 |
| **Acceso a Datos** | Lee el CSV, normaliza los datos y guarda lecturas e incidencias | RF1, RD3–RD6 |
| **Dominio** | Clases del problema: vía, dispositivo, lectura, incidencia, usuario y gestor | RF2, RD7 |
 
El Dominio es un paquete independiente para que la lógica y el acceso a datos usen las mismas clases sin depender entre sí.
 
**Estilo descartado: Tuberías y Filtros.** Sirve para procesar datos paso a paso, como en una cadena. Solo encajaría en la lectura del CSV, pero el resto del sistema (consultar gráficas, publicar incidencias, suscribirse) no funciona así.
