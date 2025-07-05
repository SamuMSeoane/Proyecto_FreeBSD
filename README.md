# Proyecto_FreeBSD
Conjunto de experiencias de un novato explorando un sistema Unix-like

## Introducción


Cuando los mensajes de actualización a Windows11 se pusieron especialmente pesados, y no dejaban de repetirme que mi equipo no era apto y que Windows 10 dejaría de tener soporte, decidí buscar alternativas en el mundo Linux.
Siempre he utilizado sistemas de Microsoft, desde el MS-DOS hasta el comienzo de Windows 3.1 y no precisamente por fidelidad a la marca sino por no buscar más allá.
En mis estudios recientes de Sistemas Informáticos probé un poco de Ubuntu, y luego intenté hacer operativos un par de ordenadores viejitos con Linux Mint y otras distribuciones cada vez más minimalistas. No tuve mucho éxito, pero eso fue más bien por culpa de las carencias de los equipos.
Como dependía de mi PC para estudiar, no me atreví a seguir explorando con un doble arranque. Sí probé a instalar Ubuntu en máquinas virtuales pero apenas para cumplir con las tareas académicas

No recuerdo a través de qué medio (un podcast, un video sugerido por Youtube) conocí la existencia de los sistemas herederos del BSD. Y ya ni recuerdo qué estaba buscando cuando en un foro leí sobre la existencia de una versión portable de FreeBSD llamada nomadBSD que ofrecía la posibilidad de llevártelo todo puesto en un USB. Me enamoró la idea. 

Aquí pretendo narrar mis descubrimientos, avances y fracasos. 


## Primeros pasos

Busqué la página y descargué la imagen de disco (todo esto desde Windows).
Después creé la memoria arrancable con la aplicación Rufus (muy recomendable).
Dediqué una memoria flash usb 3.0 (tener en cuenta esto para la velocidad de funcionamiento) a este experimento.
Fue todo tan fácil!

En el primer arranque tan sólo configuré idioma y contraseña de root y... a funcionar!




## El salto a ZFS

Siguiendo los consejos de un participante en un canal de Telegram, empecé de nuevo pero esta vez con la versión que lleva el sistema de archivos ZFS. 
Esto me permitiría sacar instantáneas del sistema antes de cada instalación arriesgada para recuperar el sistema en caso de fallar todo utilizando "Boot Environment".





