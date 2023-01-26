# #### Tipos de kernel
- ## Kernel monolítico:
El núcleo monolítico gestiona los recursos del sistema entre la aplicación y el hardware del sistema. Pero a diferencia de microkernel, los servicios de usuario y los servicios de kernel se implementan en el mismo espacio de direcciones. Esto aumenta el tamaño del kernel además aumenta el tamaño del sistema operativo.
El núcleo monolítico proporciona programación de CPU, administración de memoria, administración de archivos y otras funciones del sistema operativo a través de llamadas al sistema. Como los servicios de usuario y los servicios del kernel residen en el mismo espacio de direcciones, esto da como resultado un sistema operativo de rápida ejecución.
Uno de los inconvenientes del kernel monolítico es que si falla algún servicio, se bloquea el sistema. Si se va a agregar un nuevo servicio en el núcleo monolítico, se debe modificar todo el sistema operativo.

- ## Kernel microkernel:
Microkernel es un núcleo que gestiona todos los recursos del sistema. Pero en un microkernel, los servicios de usuario y los servicios de kernel se implementan en diferentes espacios de direcciones. Los servicios de usuario se mantienen en el espacio de direcciones de usuario y los servicios de kernel se mantienen bajo el espacio de direcciones de kernel . Esto reduce el tamaño del núcleo y reduce aún más el tamaño del sistema operativo.
Además de la comunicación entre la aplicación y el hardware del sistema, el microkernel proporciona servicios mínimos de gestión de procesos y memoria. La comunicación entre el programa / aplicación cliente y los servicios que se ejecutan en el espacio de direcciones del usuario se establece mediante el paso de mensajes. Nunca interactúan directamente. Esto reduce la velocidad de ejecución de microkernel.
En un microkernel, los servicios de usuario están aislados de los servicios del kernel, por lo que si algún servicio de usuario falla, no afecta al servicio del kernel y, por lo tanto, el sistema operativo no se ve afectado . Esta es una de las ventajas en el microkernel. El microkernel es fácilmente extensible . Si se van a agregar los nuevos servicios, se agregan al espacio de direcciones del usuario y, por lo tanto, el espacio del kernel no requiere ninguna modificación. El microkernel también es fácilmente portátil, seguro y confiable.

- ## Kernel híbrido:
La combinación del kernel monolítico y el microkernel se denomina kernel híbrido. En este caso, el kernel grande se hace más compacto y modulable. Otras partes del kernel pueden cargarse dinámicamente. Esto ya ocurre en cierta medida en Linux y OS X.
En computación, un núcleo híbrido es un tipo de núcleo de un sistema operativo. Básicamente, es un micronúcleo que tienen algo de código «no esencial» en espacio de núcleo, para que este se ejecute más rápido de lo que lo haría si estuviera en espacio de usuario.
Este fue un compromiso que muchos desarrolladores de los primeros sistemas operativos, con arquitectura basada en micronúcleo, adoptaron antes de que se mostrara que los micronúcleos pueden tener también muy buen rendimiento.
Se tiende a confundir erróneamente a los núcleos híbridos con los núcleos monolíticos que pueden dinámicamente cargar módulos después del arranque. El concepto de núcleo híbrido se refiere a que el núcleo en cuestión usa mecanismos o conceptos de arquitectura tanto del diseño monolítico como del micronúcleo, específicamente el paso de mensajes y la migración de código «no esencial» hacia el espacio de usuario (manteniendo a su vez cierto código «no esencial» en el propio núcleo por razones de rendimiento).

- ## Kernel exokernel:
Desarrollado con fines de investigación por el grupo de Sistemas Operativos y Paralelos y Distribuidos del MIT.
Reduce su función a la multiplexación segura de los recursos físicos 
En general los diseños de kernel ocultan los recursos de hardware requiriendo que los programas accedan a los mismos a través de algún modelo conceptual o abstracción (file systems, memoria virtual, schedulers, sockets, etc.) Las abstracciones predefinidas facilitan el desarrollo de programas, pero limitan la performance y reprimen la experimentación de nuevas abstracciones 
El concepto de exokernel es un compromiso: “dejar que el kernel administre los recursos físicos de hardware básicos para múltiples aplicaciones y dejar que las mismas decidan que hacer con estos recursos”
A pesar de su reducida funcionalidad, la asignación y revocación de recursos está implementada en el mismo núcleo, aunque las aplicaciones pueden participar en las políticas de asignación y revocación


## Diferencias:
La diferencia principal entre kernel molítico, kernel híbrido y microkernel radica en que los monolíticos facilitan abstracciones del hardware  subyacente potente y variada, tiene todas las funcionalidades integradas en el sistema, mientras que los microkernels proporcionan un pequeño conjunto de abstracciones simples del hardware y usan las aplicaciones o servidores para para ofrecer mayor funcionalidad, su objetivo es reducir los kernel a su máxima expresión, y los kernels híbridos incluyen un código adicional en el espacio kernel para que se ejecute mas rápidamente.


| MONOLITICOS  | MICROKERNELS  |
| ------------ | ------------ |
| Facilitan abstracciones del hardware subyacente realmente potentes y variadas.  | Proporcionan un pequeño conjunto de abstracciones simples del hardware y usan las aplicaciones llamadas servidores para ofrecer mayor funcionalidad.  |

| HÍBRIDOS  |  EXOKERNELS |
| ------------ | ------------ |
|  Son muy parecidos a los microkernels puros, excepto porque incluyen código adicional en el espacio de kernel para que se ejecute más rápidamente. | No facilitan ninguna abstracción, pero permiten el uso de bibliotecas que proporcionan mayor funcionalidad gracias al acceso casi directo al hardware.  |

## User vs kernel mode:

| Criterios  | Modo kernel  | Modo de usuario  |
| ------------ | ------------ | ------------ |
| **modo kernel vs modo usuario**  | En modo kernel, el programa tiene acceso directo y sin restricciones a los recursos del sistema.  | En modo usuario, el programa de aplicación se ejecuta y se inicia.  |
|** Interrupciones ** | En el modo Kernel, todo el sistema operativo puede dejar de funcionar si se produce una interrupción  | En el modo de usuario, un solo proceso falla si ocurre una interrupción.    |
| **Modos ** | El modo kernel también se conoce como modo maestro, modo privilegiado o modo de sistema.  | El modo de usuario también se conoce como modo sin privilegios, modo restringido o modo esclavo.  |
| **Espacio de direcciones virtuales**  | En modo kernel, todos los procesos comparten un único espacio de direcciones virtuales.  | En el modo de usuario, todos los procesos obtienen un espacio de direcciones virtuales separado.  |
| **Nivel de privilegio**  | En el modo kernel, las aplicaciones tienen más privilegios que en el modo usuario.  | Mientras está en modo usuario, las aplicaciones tienen menos privilegios.  |
|** Restricciones ** | Como el modo kernel puede acceder tanto a los programas del usuario como a los programas del kernel, no hay restricciones.  | Mientras que el modo de usuario necesita acceder a los programas del kernel, ya que no puede acceder a ellos directamente.  |
|** Fallo del sistema ** | Un bloqueo del sistema en modo kernel es grave y complica las cosas.  | En el modo de usuario, se puede recuperar un bloqueo del sistema simplemente reanudando la sesión.  |
| **Funcionalidad**  | El modo kernel puede hacer referencia a cualquier bloque de memoria en el sistema y también puede dirigir la CPU para la ejecución de una instrucción, lo que lo convierte en un modo muy potente y significativo.  | El modo usuario es un modo de visualización estándar y típico, lo que implica que la información no puede ejecutarse por sí sola ni hacer referencia a ningún bloque de memoria; necesita una interfaz de protocolo de aplicación (API) para lograr estas cosas.  |



