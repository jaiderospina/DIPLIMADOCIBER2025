## DATA CAVING

El **Data Carving** es una técnica esencial en informática forense y recuperación de datos que permite extraer archivos e información de dispositivos de almacenamiento, incluso cuando los sistemas de archivos están dañados, han sido eliminados o formateados. A diferencia de los métodos tradicionales de recuperación de archivos, que se basan en la información de los metadatos del sistema de archivos (como la tabla de asignación de archivos o la tabla de particiones), el data carving **ignora estas estructuras y analiza directamente los datos brutos** del dispositivo.

Su propósito principal es recuperar información que de otra manera sería inaccesible, identificando y reconstruyendo archivos a partir de sus **firmas únicas** (conocidas como encabezados y pies de archivo) o patrones de contenido específicos.

**¿Para qué sirve el Data Carving?**

* **Recuperación de archivos eliminados:** Cuando un archivo se elimina, sus metadatos suelen borrarse, pero los datos reales pueden permanecer en el disco hasta que sean sobrescritos. El data carving permite "desenterrar" estos datos.
* **Investigaciones forenses:** Es crucial para extraer pruebas de dispositivos dañados, formateados o manipulados, ayudando a reconstruir la línea de tiempo de eventos y a identificar actividades delictivas.
* **Recuperación de datos de sistemas de archivos dañados o corruptos:** Cuando la estructura del sistema de archivos está comprometida, los métodos tradicionales fallan. El data carving puede operar directamente sobre los datos físicos.
* **Recuperación de datos de particiones perdidas o eliminadas:** Similar a los archivos, las particiones pueden ser eliminadas, pero sus datos pueden seguir siendo recuperables.

**¿Cómo funciona el Data Carving?**

El proceso generalmente implica:

1.  **Escaneo del medio de almacenamiento:** Se realiza un escaneo exhaustivo del disco duro, tarjeta de memoria, etc., a nivel de bits y bytes, sin tener en cuenta la estructura del sistema de archivos.
2.  **Identificación de firmas de archivo:** Se buscan patrones específicos de bytes que indican el inicio (encabezado) y, a veces, el final (pie de página) de un tipo de archivo conocido (por ejemplo, `FF D8` para un archivo JPEG).
3.  **Extracción y reconstrucción:** Una vez que se identifican estas firmas, los datos entre el encabezado y el pie de página (o un tamaño predefinido) se extraen y se intentan ensamblar para reconstruir el archivo original.

**Tipos de Data Carving:**

* **Header/Footer Carving:** El método más común, que busca firmas de encabezado y pie de página conocidas para delimitar los archivos.
* **Content-Based Carving:** Utiliza patrones de contenido o firmas dentro del archivo para identificar y recuperar archivos, útil cuando los encabezados/pies no son claros o el archivo está fragmentado.
* **Fragmented File Carving:** Técnicas más avanzadas que intentan reensamblar bloques de datos fragmentados que pertenecen al mismo archivo.
* **Object-Based Carving:** Se enfoca en reconstruir objetos más complejos como bases de datos o archivos comprimidos.

**Herramientas de Data Carving:**

Existen diversas herramientas, tanto gratuitas como comerciales, que implementan técnicas de data carving. Algunas de las más conocidas en el ámbito forense incluyen:

* **Foremost**
* **Scalpel**
* **PhotoRec**
* **Autopsy/Sleuth Kit**
* **EnCase**
* **X-Ways Forensics**
* **Wondershare Recoverit**

Es importante destacar que el data carving no siempre recupera el nombre original del archivo ni su estructura de directorios, ya que esta información se almacena en los metadatos del sistema de archivos, los cuales pueden estar corruptos o eliminados. Sin embargo, es una herramienta poderosa para la recuperación de datos en situaciones críticas.