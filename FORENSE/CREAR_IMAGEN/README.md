# README.md

# Cómo crear una Imagen Forense de una MicroSD con FTK Imager

Este documento explica paso a paso el proceso para generar una imagen forense de una tarjeta MicroSD empleando **FTK Imager 4.5.0.3**, siguiendo el manual detallado en [Behacker.pro][1].

## Material y Requisitos

- FTK Imager 4.5.0.3 instalado en una máquina virtual Windows 10  
- Tarjeta MicroSD (ejemplo: 32GB)
- Adaptador MicroSD con protección contra escritura

## Precauciones Iniciales

- **Asegúrese de que la MicroSD esté bloqueada contra escritura** antes de conectarla. Esto previene la alteración de la evidencia digital.

![Adaptador y MicroSD Bloqueados](unnamed(1).png)

### 1. Verificar el Dispositivo

- Introduzca la MicroSD (locked/solo lectura) en el adaptador y, luego, en la estación forense.
- Verifique mediante la administración de discos que la MicroSD está en modo "sólo lectura".

![Administración de Discos](images/imagen5.pngir FTK Imager y Seleccionar Fuente

1. Ejecute FTK Imager.  
2. Vaya a **File > Create Disk Image**.

![FTK Imager: Create Disk Image](images/imagen7.pngPhysical Drive** como tipo de fuente de la evidencia.

![Seleccionar Physical Drive Seleccione la MicroSD de la lista de dispositivos.

![Seleccionar Micro Haga clic en **Finish**.

### 3. Configurar Destino de Imagen

1. En "Image Destination(s)", haga clic en **Add**.

![Agregar Destino de Imagen Seleccione el formato de imagen deseado:
   - Raw (dd)
   - SMART
   - **E01**
   - AFF (utilizado en el ejemplo)

![Seleccionar Formato de Imagen](images/imagen12.png información del caso:  
   - Número de caso  
   - Número de evidencia  
   - Descripción única  
   - Nombre del examinador  
   - Notas pertinentes  

![Entrada de Información de Evidencia](images/imagenccione la carpeta para guardar la imagen y el nombre del archivo.

![Seleccionar Carp 4. Opciones Finales y Creación

- Marque la opción **"Create directory listings of all files in the image after they are created"** para generar un listado de directorios.

![Seleccionar Opciones Finalaga clic en **Start** para iniciar el proceso.

![Progreso de Creación de Imagen 5. Verificación y Resultados

- El proceso puede tomar varios minutos según el tamaño de la MicroSD (ejemplo: 34 minutos para la creación, 8 minutos para verificación).
- Se mostrarán los hashes MD5 y SHA1, confirmando que los valores computados coinciden con los reportados.

![Verificación MDificación SHA generan archivos de salida:
  - Archivo de imagen (AFF)
  - Listado de directorios (CSV)
  - Resumen del procedimiento (TXT)

![Archivos Generados](images/imagen30.png Archivo TXT](images/imagen CSV](images/imagen32.png Evidencia

Se recomienda obtener al menos dos copias forenses del dispositivo de almacenamiento con posible evidencia digital.
