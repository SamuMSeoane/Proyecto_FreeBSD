Empezado el 25/07/2025

Tras varios intentos infructuosos anteriores instalo de nuevo el sistema en un USB de 32GB, desde windows y mediante Rufus.

Sigo los pasos probados:
* Guardo una imagen de BE inicial
* Creo un usuario samu le cambio la configuración de pantalla para distinguirlo
* Actualizo el gestor de paquetes con
  ```
  samu@NomadBSD ~> doas pkg upgrade
  ```
  pero NO actualizo todo, sólo pkg

* Instalo el navegador Vivaldi a través de la opción Internet > Linux Browser Installer GUI  
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
