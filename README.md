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

(Sección en construcción...)


## El salto a ZFS

Siguiendo los consejos de un participante en un canal de Telegram, empecé de nuevo pero esta vez con la versión que lleva el sistema de archivos ZFS. 
Esto me permitiría sacar instantáneas del sistema antes de cada instalación arriesgada para recuperar el sistema en caso de fallar todo utilizando "Boot Environment".

Así pues: nuevo USB y nada más arrancar guardé la instantánea: 
nomad@NomadBSD ~> sudo bectl create recien-instalado


### El error de octopkg: c.upf-8

Cada vez que arranco Octokpg para administrar actualizaciones me sale un error referido al archivo de configuración local que asume C.UPF-8 en lugar del idioma que yo uso que es es_ES.utf-8. Intenté corregirlo modificando el archivo profile.conf pero al arrancar el sistema no pasaba de la pantalla de selección de usuario (desconozco el motivo) así que tocó acceder en modo usuario único y probar la recuperación de la imagen: 
nomad@NomadBSD ~> sudo bectl activate recien-instalado

He renunciado a continuar esta guerra. 

### Actualizar a octopkg-0.4.1 

La instalación base viene con octopkg-0.3.3 y él mismo te indica que está desactualizado. Si le ordenas actualizarse, renueva dos paquetes: 
el propio octophk y qt-sudo-2.0.1

Pero tras una supuesta instalación exitosa (con reinicio de por medio, que es cuando luego rompen las cosas), va el cabrito y no arranca.
Al intentar arrancarlo desde terminar obtienes un poco más de información: 
nomad@NomadBSD ~> octopkg 
ld-elf.so.1: /usr/local/lib/qt6/libQt6Core.so.6: version Qt_6.8 required by /usr/local/bin/octopkg not found

En el sistema viene instalado qt6-base-6.7.2 

Como tengo mi BE "recién-instalado" para revertir cagadas, me lanzo a actualizar esto. Son las 20:23.
así que:  sudo pkg upgrade -f qt6\* y a ver qué pasa... 
no funciona y recurro a: sudo pkg install qt6
Ahí sí me avisa de que se van a instalar y actualizar una cantidad obscena de paquetes.
Me pregunto si me vale la pena, porque esto ya lo he intentado anteriormente y se rompió todo tras una noche actualizando.
Finalmente decido que no porque actualizar qt6 implica actualizar Gimp y firefox y VLC y demasiadas cosas y es un cambio muy pesado.

Volvemos al principio: sudo bectl activate recien-instalado
(y salió mal, el equipo dejó de arrancar desde el USB despues de esta orden y tuve que crear el booteable de nuevo). 

### Actualizar Firefox a 140.0.2,2

No tengo muy claro qué pasó aquí: en un nuevo reinicio el USB sí arrancó pero resulta que en la instantánea que yo quería restaurar ahora tenía el octopkg actualizado. Por no sé qué idea loca dije: de perdidos al río, vamos a actualizar Firefox.
Y lo hice desde consola, claro.
Pues bien, fue rapidísimo, terminó exitosamente... y tras esta actualización el octopkg funcionó!!!
Y además mucho más rápido y fluido que cuando tenía instalada la versión anterior.


### Actualizar xfce4-desktop a 4.20.1

Trasteando por el octo veo que el gestor de escritorio y toda su familia están en la versión 4.18
Así que un poco a lo loco (pero desde la consola) lo mando actualizar antes de reiniciar. 
Lo hace rápido con algún mensaje de error.

Vamos a reiniciar, a ver qué pasa. 





