##    Ejercicio 1A: Completa los flujos que faltan

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


##  Bug a corregir

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


EJERCICIO 2A: Generalización de ActoresRespuestas a la Guía¿Hacia dónde apunta el triángulo vacío y por qué?Respuesta: Apunta hacia el actor Jugador (el actor padre o general). En UML, la flecha de generalización con punta de triángulo hueco/vacío siempre señala desde el elemento hijo (específico) hacia el elemento padre (general), indicando la relación de herencia.¿Por qué el Jugador Premium NO necesita líneas a CU-01 … CU-10?Respuesta: Porque gracias a la generalización, el Jugador Premium hereda implícitamente todas las relaciones y asociaciones a los casos de uso que ya posee el actor Jugador. Crear líneas hacia los mismos casos de uso sería redundante e incorrecto en UML.BUG A CORREGIR: Identificación de los 4 ErroresErrorDescripción del BugExplicación / SoluciónError 1Uso de "Inventario" como Caso de Uso.Un caso de uso representa un proceso o funcionalidad, por lo que debe ser un verbo en infinitivo (ej. CU-14 Gestionar inventario), no un sustantivo/entidad.Error 2Actor Game Master dentro del sistema.Los actores representan entidades o roles externos que interactúan con la aplicación. Todos los actores deben dibujarse fuera del rectángulo del límite del sistema.Error 3Dirección invertida en la relación «include».La flecha de inclusión fue trazada de CU-04 a CU-03. Debe apuntar del caso de uso base al incluido (CU-03 Crear personaje $\rightarrow$ CU-04 Elegir clase).Error 4Asociación directa entre Jugador y Game Master.En los diagramas de casos de uso UML, los actores nunca se conectan entre sí. La comunicación siempre ocurre a través de los casos de uso del sistema.Diagrama Corregido y Completo (Mermaid)Nota: GitHub renderiza la siguiente sintaxis mermaid directamente como un diagrama gráfico.graph TD
    %% Definición de Actores (Fuera del Sistema)
    subgraph Actores ["Actores Externos"]
        direction TB
        J["Jugador"]
        JP["Jugador Premium"]
        GM["Game Master"]
    end

Especificaciones Técnicas del Diseño CorregidoJerarquía de Actores: Jugador Premium $\rightarrow$ Jugador mediante herencia vacía.Límite del Sistema (System Boundary): Define formalmente qué partes son internas de la aplicación y separa a todos los actores fuera de este contenedor.Estándares de Asociación: Líneas simples sin punta para asociaciones actor-caso de uso, y líneas punteadas dirigidas únicamente para estereotipos «include» o «extend».
