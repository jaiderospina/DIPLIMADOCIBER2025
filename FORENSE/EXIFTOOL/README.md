## Manual ExifTool para Windows

### ¿Qué es ExifTool?

ExifTool es una biblioteca Perl multiplataforma y una aplicación de línea de comandos para **leer, escribir y editar información de metadatos** en una gran variedad de formatos de archivos, incluyendo imágenes (JPEG, RAW, TIFF, etc.), videos (MP4, AVI), audio, documentos PDF, y más[10].

### Instalación en Windows

1. **Descarga:**
   - Ve a la página oficial de ExifTool: [exiftool.org](https://exiftool.org/)
   - Descarga la versión para Windows, que incluye un ejecutable independiente:
     - 32-bit: `exiftool-13.33_32.zip` (~11 MB)
     - 64-bit: `exiftool-13.33_64.zip` (~10.8 MB)

2. **Descompresión:**
   - Extrae el contenido del archivo ZIP en una carpeta de tu preferencia. Dentro encontrarás:
     - `exiftool(-k).exe`
     - Carpeta llamada `exiftool_files`

3. **Uso directo:**
   - Puedes usar el ejecutable directamente haciendo doble clic en `exiftool(-k).exe` para abrir una ventana del símbolo del sistema con documentación y arrastrar archivos para ver metadatos[10].
   - Para usarlo por línea de comandos (cmd):
     - Renombra `exiftool(-k).exe` a `exiftool.exe` para facilitar su llamada.
     - Importante: si mueves el `.exe` a otra carpeta, mueve también la carpeta `exiftool_files` a esa ubicación.
     - Añade la carpeta al PATH Windows para ejecutarlo desde cualquier ubicación (opcional).

4. **Requisitos:**
   - Esta versión para Windows ya incluye Perl embebido, por lo que no necesitas instalar nada más. Sin embargo, si deseas usar la versión Perl pura, puedes instalar un intérprete Perl como Strawberry Perl o ActivePerl[10].

### Uso básico en Windows CMD

Abre una ventana de comando (cmd.exe) y navega a la carpeta donde está `exiftool.exe`. Algunos comandos comunes:

- **Ver todos los metadatos de un archivo:**
  ```cmd
  exiftool archivo.jpg
  ```

- **Extraer solo etiquetas específicas:**
  ```cmd
  exiftool -Make -Model -ExposureTime archivo.jpg
  ```

- **Guardar metadatos en un archivo texto:**
  ```cmd
  exiftool archivo.jpg > metadatos.txt
  ```

- **Extraer metadatos en varios archivos a la vez:**
  ```cmd
  exiftool *.jpg
  ```

- **Copiar metadatos de un archivo a otro:**
  ```cmd
  exiftool -tagsFromFile origen.jpg destino.jpg
  ```

- **Eliminar metadatos específicos (p.ej. GPS):**
  ```cmd
  exiftool -gps:all= archivo.jpg
  ```

- **Cambiar o añadir etiquetas:**
  ```cmd
  exiftool -Artist="Tu Nombre" archivo.jpg
  ```

- **Ver todas las etiquetas con su nombre real (no descripción):**
  ```cmd
  exiftool -s archivo.jpg
  ```

- **Mostrar diferencias entre dos archivos:**
  ```cmd
  exiftool -diff archivo1.jpg archivo2.jpg --system:all -e
  ```

### Ejemplos prácticos detallados

1. **Mostrar fecha y hora original cuando se tomó la foto:**
   ```cmd
   exiftool -DateTimeOriginal imagen.jpg
   ```

2. **Cambiar la fecha de creación de un lote de fotos:**
   ```cmd
   exiftool -AllDates="2024:07:29 17:00:00" *.jpg
   ```

3. **Extraer la información del modelo de cámara y número de serie:**
   ```cmd
   exiftool -Model -SerialNumber imagen.jpg
   ```

4. **Copiar etiquetas XMP de un archivo a otro:**
   ```cmd
   exiftool -tagsFromFile fuente.jpg -xmp:all destino.jpg
   ```

5. **Eliminar todos los metadatos para protección de privacidad:**
   ```cmd
   exiftool -all= imagen.jpg
   ```

6. **Crear archivos sidecar `.xmp` con los metadatos:**
   ```cmd
   exiftool -o %d%f.xmp *.jpg
   ```

### Opciones útiles para Windows

- Usar doble comillas en lugar de simples para valores y etiquetas por la sintaxis cmd.exe:
  ```cmd
  exiftool -Artist="Nombre Artista" imagen.jpg
  ```
  
- Para ver la lista completa de opciones y ejemplos, ejecuta:
  ```cmd
  exiftool -h
  ```

- Para listar todos los nombres de etiquetas disponibles:
  ```cmd
  exiftool -list
  ```
  
- Para listar etiquetas escribibles:
  ```cmd
  exiftool -listw
  ```

### Recursos adicionales

- Manual oficial y detalles de las etiquetas: [ExifTool Documentation](https://exiftool.org/)
- Foro para ayuda avanzada y versiones: [ExifTool Forum](https://exiftool.org/forum/)
- Tutoriales en video para principiantes y usos avanzados: Busca "ExifTool tutorial" en YouTube para guías visuales [1][2][4]


- https://exiftool.org
- https://www.youtube.com/watch?v=LDtYKxvge7M
- https://www.youtube.com/watch?v=_rOapdXVcM0
- https://www.youtube.com/watch?v=7sZa8m5OpsA
- https://www.ecured.cu/ExifTool
- https://fwhibbit.es/los-secretos-que-esconde-el-cafe-vistos-con-exiftool