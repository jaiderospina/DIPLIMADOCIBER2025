# **HxD --  Editor Decimal**

### **Índice**
1. Introducción
2. Instalación
3. Interfaz del programa
4. Funciones básicas
   - Abrir un archivo
   - Navegar por el contenido hexadecimal
   - Editar datos
5. Herramientas avanzadas
   - Buscar y reemplazar
   - Comparación de archivos
   - Inserción y eliminación de bytes
6. Configuración
7. Precauciones al usar HxD
8. Ejemplos prácticos

---

## **1. Introducción**
**HxD** es un editor hexadecimal gratuito que permite visualizar, modificar y analizar datos binarios. Es ideal para tareas como la edición de archivos, análisis forense y modificación de código en sistemas de bajo nivel.

---

## **2. Instalación**
1. Descarga HxD desde su [sitio oficial](https://mh-nexus.de/en/hxd/).
2. Ejecute el instalador y siga las instrucciones.
3. Abra HxD tras la instalación.

---

## **3. Interfaz del Programa**
- **Barra de herramientas**: Contiene accesos rápidos para abrir, guardar y herramientas de búsqueda.
- **Ventana principal**: Muestra los datos en dos columnas:
  - **Columna izquierda**: Dirección de memoria o desplazamiento (offset).
  - **Columna central**: Representación hexadecimal de los datos.
  - **Columna derecha**: Representación en texto ASCII (si es legible).
- **Barra de estado**: Proporciona información como posición del cursor y tamaño del archivo.

---

## **4. Funciones Básicas**

### **Abrir un archivo**
1. Seleccione **Archivo > Abrir** o use el atajo `Ctrl+O`.
2. Busque el archivo que desea editar.
3. HxD mostrará el archivo en formato hexadecimal.

### **Navegar por el contenido hexadecimal**
- Use las teclas de flecha o el scroll del ratón para desplazarse.
- La barra inferior muestra la dirección (offset) actual del cursor.

### **Editar datos**
1. Seleccione la posición donde desea editar.
2. Escriba los nuevos valores en hexadecimal en la columna central.
   - Ejemplo: Cambie `4F` por `5A`.
3. Los cambios se reflejan automáticamente en la columna ASCII, si son caracteres legibles.

**Nota**: Los datos se sobrescriben de forma predeterminada.

---

## **5. Herramientas Avanzadas**

### **Buscar y reemplazar**
1. Haga clic en **Buscar > Buscar** (`Ctrl+F`) para localizar valores.
   - Introduzca el valor en hexadecimal o ASCII.
2. Use **Buscar > Reemplazar** (`Ctrl+R`) para cambiar valores específicos.
   - Ejemplo: Reemplace todas las ocurrencias de `41` con `42`.

### **Comparación de archivos**
1. Abra dos archivos simultáneamente.
2. Use **Análisis > Comparar archivos** para encontrar diferencias.

### **Inserción y eliminación de bytes**
- **Insertar**: Coloque el cursor en la posición deseada y use **Editar > Insertar bytes**.
- **Eliminar**: Seleccione el rango de bytes y presione `Supr` o use **Editar > Borrar**.

---

## **6. Configuración**
1. Acceda a **Extras > Opciones** para personalizar HxD.
2. Ajustes recomendados:
   - **Modo de edición**: Activa/desactiva sobrescritura.
   - **Colores**: Cambia el esquema de colores para facilitar la lectura.

---

## **7. Precauciones al Usar HxD**
1. **Respaldar siempre**: Haga una copia de seguridad del archivo antes de modificarlo.
2. Evite cambios en archivos críticos del sistema, ya que pueden causar fallos.
3. Compruebe que los cambios realizados sean válidos para el formato del archivo.

---

## **8. Ejemplos Prácticos**

### **Modificar el contenido de un archivo de texto**
1. Abra un archivo `.txt` en HxD.
2. Localice el texto que desea cambiar en la columna ASCII.
3. Sobrescriba el texto con los valores deseados.
4. Guarde los cambios.

### **Cambiar el encabezado de un archivo binario**
1. Abra un archivo `.bin`.
2. Identifique la firma del archivo en los primeros bytes (p. ej., `50 4B` para ZIP).
3. Modifique la firma si es necesario y guarde los cambios.

---

Aquí tienes ejemplos prácticos de cómo identificar y verificar las firmas (encabezados) de archivos en **HxD**. Estas firmas son conocidas como *magic numbers* y ayudan a determinar el tipo de archivo.

---

## **Ejemplos de Firmas de Encabezado**

| **Tipo de Archivo** | **Firma Hexadecimal (Magic Number)** | **Representación ASCII** |
|----------------------|-------------------------------------|--------------------------|
| JPEG (imagen)       | `FF D8 FF E0` o `FF D8 FF DB`      | ....                    |
| PNG (imagen)        | `89 50 4E 47 0D 0A 1A 0A`          | `.PNG....`              |
| GIF (imagen)        | `47 49 46 38 37 61` o `47 49 46 38 39 61` | `GIF87a` o `GIF89a` |
| PDF (documento)     | `25 50 44 46 2D`                   | `%PDF-`                 |
| ZIP (comprimido)    | `50 4B 03 04`                      | `PK..`                  |
| EXE (ejecutable)    | `4D 5A`                            | `MZ`                    |
| MP3 (audio)         | `FF FB`                            | ....                    |
| MP4 (video)         | `00 00 00 20 66 74 79 70`          | .. ftyp                |

---

### **Ejemplo 1: Identificar un archivo JPEG**
1. Abra un archivo sospechoso en **HxD**.
2. Busque los primeros bytes del archivo:
   ```
   FF D8 FF E0 00 10 4A 46 49 46
   ```
   - La firma `FF D8 FF E0` indica que es un archivo JPEG.
   - En la columna ASCII puede aparecer texto relacionado como `JFIF`.

3. Si los valores no coinciden con la firma esperada, es posible que el archivo esté corrupto o sea de otro tipo.

---

### **Ejemplo 2: Identificar un archivo PNG**
1. Abra un archivo con extensión desconocida.
2. Verifique los primeros 8 bytes:
   ```
   89 50 4E 47 0D 0A 1A 0A
   ```
   - Esto corresponde a un archivo PNG.
   - La representación ASCII mostrará algo como `.PNG....`.

---

### **Ejemplo 3: Verificar un archivo PDF**
1. Abra un archivo PDF en **HxD**.
2. Los primeros bytes deben ser:
   ```
   25 50 44 46 2D
   ```
   - Esto equivale a `%PDF-` en ASCII, lo que confirma que es un archivo PDF.
3. Si el encabezado no coincide, el archivo podría haber sido modificado o renombrado incorrectamente.

---

### **Ejemplo 4: Reconocer un archivo ZIP**
1. Abra un archivo `.zip` en HxD.
2. Inspeccione los primeros bytes:
   ```
   50 4B 03 04
   ```
   - La firma `PK..` confirma que es un archivo comprimido en formato ZIP.

---

### **Ejemplo 5: Identificar un archivo EXE**
1. Abra un archivo ejecutable (.exe).
2. Los primeros bytes deberían ser:
   ```
   4D 5A 90 00
   ```
   - La firma `MZ` es típica de archivos ejecutables en sistemas Windows.

---

### **Ejemplo 6: Detectar un archivo MP4**
1. Abra un archivo de video sospechoso.
2. Verifique si comienza con:
   ```
   00 00 00 20 66 74 79 70 69 73 6F 6D
   ```
   - La firma `ftypisom` en ASCII indica un archivo MP4.

---

### **Ejemplo Práctico: Detectar Manipulación**
Si un archivo PNG tiene una extensión `.jpg`, puede abrirlo en HxD para verificar el encabezado:
1. Si los primeros bytes son:
   ```
   89 50 4E 47 0D 0A 1A 0A
   ```
   - Esto confirma que el archivo es un PNG, aunque tenga extensión incorrecta.

---

