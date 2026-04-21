# AA1ServidorFitcherosWS

## Descripcion de la actividad

### La acticidad se divida en fitas que simulan el prceso de consultoria y implementación real

![pics](pics/1.png)

![pics](pics/2.png)

Aqui desplegamos el dominio y como podemos ver se llamará **FOODLOGISTIC**

## 1. Preparación i Seguridad de Grupos (AD)

![pics](pics/3.png)

Aquí podemos observar los grupos que hemos creado: 

- **Administración**: Gestión de facturas i albaranes.
- **Transporte**: Chofers i jefes de flota.
- **Dirección**: Gerencia.

## 2. Implementación de Recursos Compartidos 


![pics](pics/42.png)

Creamos la carpeta **public**

![pics](pics/43.png)
![pics](pics/44.png)

Permisos SMB de "Lectura"

![pics](pics/7.png)

Vamos a **new share** para compartir la carpeta que hemos creado

![pics](pics/8.png)

Seleccionamos la opción **SMB Share - Quick**

![pics](pics/9.png)

Seleccionamos la **ruta**

![pics](pics/10.png)
![pics](pics/11.png)

Dejamos seleccionada la opción que viene por **defecto**

![pics](pics/12.png)

Nos aparece los **permisos** que están asignados a esa carpeta

![pics](pics/13.png)

Aquí nos aparecerá el **resumen** de lo que hemos hecho


## B. Carpeta Operaciones (Metodo: Server Manager - FSSM):

![pics](pics/45.png)

Creamos la carpeta **operaciones**

![pics](pics/46.png)

Asignamos los siguientes permisos el cual solo **Transporte** pueda acceder

![pics](pics/7.png)

Vamos a **new share** para compartir la carpeta que hemos creado

![pics](pics/14.png)

Seleccionamos la opción **SMB Share - Quick**

![pics](pics/15.png)

Seleccionamos la **ruta**

![pics](pics/16.png)
![pics](pics/17.png)

Dejamos seleccionada la opción por **defecto** y además seleccionamos la primera que activa el "**Acces-Based Enumeration**

![pics](pics/18.png)

Aquí nos aparecerá el **resumen** de lo que hemos hecho

### - Crear el recurso compartido.
### - Hacer que solo se muestre para los usuarios con acceso (Acces-Based Enumeration)
### - Restricción: NSolo el grupo de **Transporte**  puede acceder.

## C. Carpeta Confidencial (Metodo: PowerShell básico):

![pics](pics/19.png)

Añadimos el signdo de **$** para que sea invisible

![pics](pics/20.png)

```bash
New-SmbShare -Name Confidencial -Path C:\Confidencial -FullACcess Direccion
```

![pics](pics/21.png)

Aquí estamos haciendo el **mapeo de la carpeta** y seleccionamos la opción de **Show this drive**

![pics](pics/22.png)
![pics](pics/23.png)
![pics](pics/24.png)

### - Crear la carpeta Direccion$ (recurso ocult).
### - Restricción: solo puede acceder el grupo de Dirección
### - Utilizad el cmdlet New-SmbShare para compartirla.
### - Configurar una GPO para que esta carpeta aparezca automáticamente como unidad Z: solo los usuarios de Dirección.

## D. Carpeta Confidencial (Metodo: PowerShell avanzaso):

![pics](pics/25.png)
![pics](pics/26.png)
![pics](pics/27.png)

```bash
New-SmbShare -Name Direccion -Path C:\Confidencial -FullACcess Direccion
```

![pics](pics/28.png)

```bash
Get-SmbSHare -Name "Direccion" | Set-SmbShare -FolderEnumerationMode AccessBased
```

### Crear la carpeta Dirección.
### Restricción: solo puede acceder el grupo de Dirección.
### Utilizad el cmdlet New-SmbShare para compartirla y habilitad por PowerShell el Access-Based Enumeration.
### Configurad una GPO para que esta carpeta aparezca automáticamente como la unidad Z: solo los usuarios de Dirección.

## 3. Control de Almacenaje (FSRM y Cuotas NTFS)

### El cliente se queja de que los usuarios guardan fotos personales y llenan el disco.

### Cuotas NTFS (Control por Volumen):
### A la unidad de datos, activad las cuotas NTFS desde las propiedades del volumen

### Estableced un límite de 500 MB por defecto para cualquier usuario nuevo.

![pics](pics/33.png)

### FSRM (Control por Carpeta):

### Instalad el rol File Server Resource Manager.

![pics](pics/27.png)

### Cuota de Carpeta: A la carpeta Public, aplicad una cuota de 200 MB (Hard Cuota). Configurad un aviso al 90% que envie un mensaje personalizado: "Compte! FoodLogístic t'informa que estàs a punt d'esgotar l'espai compartit."

![pics](pics/34.png)

Establecemos el límite de **200 MB por usuario**

![pics](pics/35.png)

Personalizamos el mensaje personalizado que le aparecerá al **usuario** cuando haya utilizado el 90% de espacio del disco

![pics](pics/36.png)

Le damos a la opción de **Create Quota from Template**, lo cual hará que utilizemos la plantilla que hemos creado anteriormente para asignarlo a la carpeta que queramos, en nuestro caso la carpeta **Public**

![pics](pics/37.png)

Le asignamos la **ruta** de la carpeta que queremos asignar los límites establecidos anteriormente

### Filtrado por Ficheros: A la carpeta Operaciones, cread un filtro que impida guardar archivos ejecutables (.exe, .msi) y ficheros de audio y video.

![pics](pics/38.png)

Como podemos ver el el apartado de **Files to exclude** hemos añadido los siguientes:

- .msi
- .exe

![pics](pics/39.png)

Tambíen exluimos que pueda poner:

- Audio and Video Files

![pics](pics/40.png)

Hacemos lo mismo que anteriormente, de utilizar la plantilla con las configuraciones que hemos puesto
