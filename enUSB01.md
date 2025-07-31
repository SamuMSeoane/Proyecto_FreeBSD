# Empezado el 25/07/2025

Tras varios intentos infructuosos anteriores instalo de nuevo el sistema en un USB de 32GB, desde windows y mediante Rufus.

Sigo los pasos probados:
* Guardo una imagen de BE inicial
* Creo un usuario samu y le cambio la configuración de pantalla para distinguirlo
* Actualizo el gestor de paquetes con
  ```
  samu@NomadBSD ~> doas pkg upgrade
  ```
  pero NO actualizo todo, sólo pkg

* Instalo el navegador Vivaldi a través de la opción Internet > Linux Browser Installer GUI  
  La instalación funciona, pero por lo que sea en varios momentos observo este error: 
  ```
  perl: warning: Setting locale failed.
  perl: warning: Please check that your locale settings:
	    LANGUAGE = (unset),
	    LC_ALL = (unset),
	    LANG = "es_ES.UTF-8"
    are supported and installed on your system.
  perl: warning: Falling back to the standard locale ("C").
  locale: Cannot set LC_CTYPE to default locale: No such file or directory
  locale: Cannot set LC_MESSAGES to default locale: No such file or directory
  locale: Cannot set LC_ALL to default locale: No such file or directory
  ```
  He intentado investigar de qué va o cómo solventarlo (editando un archivo de configuración) pero nada pareció funcionar.

# 31/07/2025 Situación estable para probar cosas

He intentado instalar el VSCode para programar pero la instalación como paquete ha roto la interfaz gráfica una vez más.
Tras comentarlo en el foro de NomadBSD me han sugerido seguir los pasos de este artículo: 
(https://freebsdfoundation.org/resource/how-to-use-vs-code-on-freebsd/)

y tratar de instalarlo desde los ports.

Antes de hacerlo, gestión de Boot Environments: 
* recupero el último entorno funcional  (bectl __activate__ entorno_funcional) y reinicio.
* borro el entorno de pruebas donde hice la instalación defectuosa (bectl __destroy__ entorno_pruebas).
* creo un entorno copia del funcional (bectl __create__ entorno_pruebas) y lo activo para trabajar sobre él desde el siguiente reinicio.
De esta manera siempre trabajo sobre un entorno de pruebas y voy salvando los avances exitosos.


	
