## ✏️ Ejercicio 1A: Completa los flujos que faltan

El sistema todavía tiene dos flujos sin dibujar. Se escriben en la tabla y se agregan al diagrama:

1. Cuando el Jugador inicia sesión, ¿qué dato envía?
2. Cuando el Servicio de Respaldo devuelve una partida guardada, ¿qué dato viaja y en qué dirección?

| #   | Origen                          | Flujo de datos                                              | Destino      |
|-----|---------------------------------|-------------------------------------------------------------|--------------|
| F10 | Jugador                         | credenciales de acceso (usuario/correo y contraseña)        | RPG Manager  |
| F11 | Servicio de Respaldo en la Nube | copia de partida guardada (datos de la partida recuperada)  | RPG Manager  |

### Justificación

- **F10:** el Jugador es quien inicia sesión, por lo que es el origen. Envía sus credenciales al RPG Manager, que las recibe para validarlas contra los datos que ya tiene guardados.
- **F11:** el Servicio de Respaldo devuelve la partida guardada, por lo que el flujo sale del servicio externo y llega al RPG Manager. Es el sentido contrario de F9, donde el RPG Manager enviaba la copia de seguridad a la nube.


## 🐛 Bug a corregir

Un compañero entregó un diagrama de contexto con estos elementos. Se identifican los tres errores:

- Un rectángulo "Base de datos de Personajes" conectado al círculo como entidad externa.
- Una flecha de Jugador al círculo con la etiqueta "Crear Personaje".
- Una flecha directa de Jugador a Game Master con la etiqueta "mensaje".

| #       | Elemento                                              | Error                                                                 | Corrección                                                                                          |
|---------|-------------------------------------------------------|-----------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------|
| Error 1 | Rectángulo "Base de datos de Personajes" como entidad externa | Una base de datos es un almacén de datos interno del sistema, no una entidad externa. En un diagrama de contexto no se dibujan almacenes. | Eliminarla del diagrama de contexto. Aparecería después, como almacén, en el DFD de nivel 1. |
| Error 2 | Flecha "Crear Personaje"                              | La etiqueta es un verbo (una acción o proceso), no un dato. Los flujos deben nombrar los datos que viajan. | Renombrarla como **"datos del personaje (nombre, clase)"** (F2). |
| Error 3 | Flecha directa Jugador → Game Master "mensaje"        | Un flujo entre dos entidades externas queda fuera del sistema. Todo flujo debe entrar o salir del proceso central. | Eliminar la flecha, o hacer que el mensaje pase por el RPG Manager (Jugador → RPG Manager → Game Master). |

### Respuestas

- **Error 1:** La "Base de datos de Personajes" es un almacén de datos interno, no una entidad externa, y no debe aparecer en un diagrama de contexto.
- **Error 2:** "Crear Personaje" es una acción, no un dato. El flujo debe llamarse "datos del personaje (nombre, clase)".
- **Error 3:** La flecha Jugador → Game Master conecta dos entidades externas entre sí. Todo flujo debe pasar por el sistema (RPG Manager).
