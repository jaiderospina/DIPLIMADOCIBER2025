# Recovering Deleted Files - Forensics :detective:

* Did you know that even deleting a file from a device, it remains accessible? Did you know that we can recover this data? With this concept of file recovery, we can also mention the problems of leakage and unauthorized data access when a **HD/SSD/PENDRIVE** is discarded incorrectly. The people who may be looking for this data are called **Dumpster Diving**.

> [!IMPORTANT]
The **Dumpster diving** is looking for treasure in someone else's trash. In the world of information technology (IT), dumpster diving is a technique used to retrieve information that could be used to carry out an attack or gain access to a computer network from disposed items.

<p align="center">
  <img width="400" height="400" src="./img/1.png">
</p>

* In this document we will use one of the forensic techniques used to recover and analyze system files. For the study, we will **Create** and **Remove** files on drive 'E:', below.

<p align="center">
  <img width="400" height="180" src="./img/5.png">
</p>

# What will we use :question:

* In our study we will use 2 programs, one to create an image of the target disk and the other to analyze this data.

    * **FTK Imager** - FTK Imager es una herramienta gratuita de análisis forense digital. Cuenta con funciones específicas para la adquisición de evidencia derivada de unidades de almacenamiento. En este caso, utilizaremos la versión para Windows, disponible en[FTK Imager](https://www.exterro.com/ftk-product-downloads/ftk-imager-version-4-7-1)

    <p align="center">
        <img width="110" height="120" src="./img/2.png">
    </p>

    * **Autopsy** -Autopsy es una herramienta para el personal de primera respuesta cibernética en casos de intrusiones, escenas de crímenes y zonas de guerra. Se utilizará junto con FTK para analizar los datos generados. Está disponible para Windows.e [Autopsy](https://www.autopsy.com/download/)

    <p align="center">
        <img width="400" height="100" src="./img/3.png">
    </p>
    
# Disk Image :cd:

* Un archivo de imagen de disco contiene una copia bit a bit de una unidad de disco. Una copia bit a bit guarda todos los datos de un archivo de imagen de disco, incluidos los metadatos, en un solo archivo. Para este paso, usaremos **FTK Imager**.

1. Vaya a 'Archivo -> Crear imagen de disco'.

<p align="center">
    <img width="500" height="200" src="./img/4.png">
</p>

2. SetSeleccionar 'Logical Driver'.
 <p align="center">
    <img width="500" height="300" src="./img/6.png">
</p>

3. Selecionar el Drive.
 <p align="center">
    <img width="500" height="300" src="./img/7.png">
</p>

4. Selecione  type 'E01', this type will be imported into autopsy.
 <p align="center">
    <img width="500" height="300" src="./img/8.png">
</p>

5. Registrar la evidencia; esta información no es necesaria. En Destino, se indica dónde se guardará el registro.
 <p align="center">
    <img width="600" height="300" src="./img/9.png">
</p>

6. Generación de la imágen **forense.E01**.
 <p align="center">
    <img width="420" height="300" src="./img/10.png">
</p>

# Recovering the Files :floppy_disk:

* Después de generar los archivos de evidencia con FTK Imager, podemos analizar y recuperar los archivos eliminados con Autopsy. ¡Vamos!

1. Crear un nuevo caso'new case'.
 <p align="center">
    <img width="420" height="260" src="./img/11.png">
</p>

2.Generar datos solicitados sobre el caso.
 <p align="center">
    <img width="500" height="300" src="./img/12.png">
</p>

3. Aquí seleccionaremos una imagen de disco..
 <p align="center">
    <img width="700" height="300" src="./img/13.png">
</p>

4. Selecionar el archivo E01.
 <p align="center">
    <img width="600" height="200" src="./img/14.png">
</p>

5. Aquí podemos ver todos nuestros archivos eliminados.
 <p align="center">
    <img width="800" height="450" src="./img/15.png">
</p>

6. Al extraer los archivos pudimos acceder nuevamente a todos los archivos.
 <p align="center">
    <img width="800" height="250" src="./img/16.png">
</p>

# Evidencia Final :mag:

* Below we were able to open all the files that were deleted on our disk E:.

 <p align="center">
    <img width="800" height="400" src="./img/17.png">
</p>

