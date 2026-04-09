# Servidor Correo Linux **iRedMail**

## Configuración Máquina virtual

### Red
- Nat
- Host-Only

### Nombre del sistema

![pics](pics/1.png)

Asignamos como hostname **m23** y en la carpeta de /etc/hosts **m23.serveis23.test**

## Instalación iRedMail

### Wget

![pics](pics/2.png)

Con la comanda **wget** instalamos la **última versión** del **iRedMail** 

### Tar

![pics](pics/3.png)

Con la comanda **tar** descomprimimos el archivo el cual se descomprimirá en la misma ruta en la que estemos en ese momento

### Bash

![pics](pics/6.png)

Con la comanda **bash** lo que hacemos es ejecutar el script el cual nos permitirá abrir iRedMail

## Configuración iRedMail

![pics](pics/7.png)
![pics](pics/8.png)
![pics](pics/9.png)

En las capturas que se muestran no hacemos ningún cambio

![pics](pics/10.png)

En cambio en esta captura, seleccionamos la segunda opción **MariaDB**

![pics](pics/11.png)

Asignamos una **contraseña**

![pics](pics/12.png)

Asignamos el correo del **dominio** que **NO** no puede ser igual al que tenemos como hostname en el Ubuntu Server

![pics](pics/13.png)

Asignamos una **contraseña**

![pics](pics/14.png)

Seleccionamos las **4** opciones marcadas

![pics](pics/15.png)

Esta captura nos muestra un **resumen** de la configuración que hemos hecho y nos da la opción de cambiar algo en el caso que haga falta

![pics](pics/16.png)

Nos pide que **reiniciemos** el sistema

## Login iRedMail

![pics](pics/17.png)

La URL para llegar a esta página es **https://192.168.56.107/iredadmin/** 

![pics](pics/18.png)

Este es el **panel** que se nos muestra al entrar

![pics](pics/19.png)

Para **crear** el usuario tendremos que ir a:
- +Add
  - User
Aquí se rellena con la información con la cual queramos poner

![pics](pics/1.png)

Como podemos ver se ha creado **exitosamente**

![pics](pics/21.png)

La URL oara llegar a esta página es **https://192.168.56.107/mail/** y logueamos con el usuario que hemos creado anteriormente

![pics](pics/22.png)

Hemos hecho una **prueba** de enviarnos a nosotros mismos un correo y podemos ver que funciona **exitosamente**