# Trabajando en máquina virtual

## Instalación: 

Harto de encender y apagar el equipo, pincho USB sí, pincho USB no (y sobre todo de hacer consultas en el momento a través del móvil) me decido a probar una nueva instalación pero utilizando una máquina virtual en el VirtualBox de Oracle.
Desde la propia página de nomadBSD.org te dan indicaciones para hacerlo sin inconvenientes.
* Descargar y descomprimir la imagen
* Crear un disco duro virtual (VDI) a partir de la imagen
* Configurar una máquina y asignarle el disco duro (VDI)

```
Abrir cmd desde la ubicación 
C:\Program Files\Oracle\VirtualBox

Dos opciones:  
VBoxManage convertfromraw "rutaArchivo.img" "rutaDiscoVirtual.vdi" --format VDI
VBoxManage.exe convertdd "C:\FreeBSD\nomadbsd-141R-20240711.amd64.zfs.img" "C:\FreeBSD\nomadbsd.zfs.vdi"
Han funcionado las dos. 

Aumentamos la capacidad  
VBoxManage modifyhd "C:\FreeBSD\nomadbsd.zfs.vdi" --resize 10000

Más info:  
https://www.infodark.net/windows/53-convertir-img-bin-a-vdi-para-crear-maquina-virtual-con-virtualbox  
[https://nomadbsd.org/handbook/handbook.html#reset_limits](https://nomadbsd.org/handbook/handbook.html#vbox)
```

Arrancar la máquina y ya todo lo demás se parece muchísimo a cuando lo haces en la máquina real desde la memoria USB.

## Probando actualizaciones.

Mi primer paso, es crear un usuario básico.

El siguiente paso (desde línea de comandos) es guardar un  Boot Environment antes de hacer nuevos cambios.


### Instalando y actualizando

#### Procedimiento

Aprovechándome de la capacidad de guardar Boot Environments, trabajo sobre un BE principal (_current_), pero tras cada actuación:
* Si funciona, guardo un nuevo BE con el hito exitoso (aunque me mantengo en el _current_).
* Si no funciona, activo el último BE exitoso, reinicio con él, borro el _current_ con el fallo, creo un nuevo _current_, lo activo y reinicio con él. 

#### Actualizo pkg

Lo primero que se actualiza al pedir un upgrade es el propio paquete pkg:
```
New version of pkg detected; it needs to be installed first.
The following 1 package(s) will be affected (of 0 checked):

Installed packages to be UPGRADED:
	pkg: 1.21.3 -> 2.2.0

Number of packages to be upgraded: 1

12 MiB to be downloaded.
```
El sistema se mantiene ok. 


#### Actualizo Firefox (Falla)
```
sudo IGNORE_OSVERSION=yes pkg upgrade firefox-esr
```

Tras una actualización bastante grande, al reiniciar se ha roto.


#### Instalo Vivaldi

A través de la opción _"Linux Browser Installer GUI"_ en el menú Internet, se pueden instalar varios navegadores basados en Chromium.
Hago la prueba instalando Vivaldi (instala la versión 7.5.3735.44). Tras un cambio de usuario y un reinicio constato que sigue funcionando.
Según comenta otro usuario del [canal de Telegram](https://t.me/NomadBSD), con Brave la instalación también funciona. 
