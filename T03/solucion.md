# AA1ServidorFitcherosWS


## Descripcion de la actividad

### La acticidad se divida en fitas que simulan el prceso de consultoria y implementación real

## 1. Preparación i Seguridad de Grupos (AD)

- **Administración**: Gestión de facturas i albaranes.
- **Transporte**: Chofers i jefes de flota.
- **Dirección**: Gerencia.

## 2. Implementación de Recursos Compartidos 

### A. Carpeta Public (Metodo: Explorador de archivos):
### - Compartirla para **todo el mundo**.
### - Configuración: Permisos SMB de "Lectura" y permisos NTFS de "Modificación". 

## B. Carpeta Operaciones (Metodo: Server Manager - FSSM):

### - Crear el recurso compartido.
### - Hacer que solo se muestre para los usuarios con acceso (Acces-Based Enumeration)
### - Restricción: NSolo el grupo de **Transporte**  puede acceder.
