# Criptoanálisis.

El **criptoanálisis** es la rama de la criptología (el estudio de los sistemas de seguridad de la información) que se ocupa de **estudiar y encontrar debilidades en los sistemas criptográficos y los algoritmos para romperlos o eludirlos**. Su objetivo principal es descubrir información oculta sin tener la clave secreta o los medios autorizados para acceder a ella.

En esencia, mientras que la **criptografía** se encarga de diseñar y construir sistemas seguros para proteger la información (cifrado, firmas digitales, etc.), el **criptoanálisis** se dedica a desmantelar, analizar y atacar esos sistemas para revelar sus vulnerabilidades. Es una especie de "prueba de estrés" constante para los métodos criptográficos.

### Propósito del Criptoanálisis:

1.  **Evaluación de la Seguridad:** Su función más importante es evaluar la fortaleza y la seguridad de los algoritmos y protocolos criptográficos existentes. Un algoritmo que resiste los mejores ataques criptoanalíticos se considera robusto.
2.  **Descubrimiento de Debilidades:** Identificar fallas matemáticas, lógicas o de implementación en los sistemas que podrían permitir a un atacante acceder a la información confidencial.
3.  **Recuperación de Información:** En contextos legítimos (como la forense digital o la recuperación de datos), el criptoanálisis puede ser utilizado para acceder a información protegida cuando las claves se han perdido o en investigaciones criminales.
4.  **Desarrollo de Mejores Algoritmos:** Los descubrimientos del criptoanálisis impulsan la mejora y el desarrollo de nuevos algoritmos y protocolos criptográficos más seguros. Es una carrera armamentista constante entre quienes crean los cifrados y quienes intentan romperlos.

### Técnicas Comunes de Criptoanálisis:

Las técnicas varían ampliamente dependiendo del tipo de sistema criptográfico que se ataque (cifrados simétricos, asimétricos, funciones hash, etc.), pero algunas de las más conocidas incluyen:

* **Ataque de Fuerza Bruta:** Probar sistemáticamente todas las posibles claves o combinaciones hasta encontrar la correcta. Es efectivo pero computacionalmente intensivo para claves largas.
* **Ataque de Diccionario:** Similar a la fuerza bruta, pero limitado a una lista predefinida de palabras o frases comunes que son probables candidatos a contraseña o clave.
* **Ataque de Tablas Arcoíris (Rainbow Tables):** Para funciones hash, implica el uso de bases de datos precalculadas que mapean hashes a sus entradas originales, acelerando significativamente la búsqueda. (Como usa CrackStation).
* **Ataque de Texto Plano Conocido:** El atacante tiene acceso tanto al texto plano original como a su correspondiente texto cifrado, lo que puede ayudar a deducir la clave.
* **Ataque de Texto Plano Elegido:** El atacante puede elegir el texto plano que se cifrará y obtener el texto cifrado resultante, lo que proporciona más control y datos para el análisis.
* **Análisis de Frecuencias:** Históricamente usado en cifrados clásicos (como el cifrado César o Vigenère), analiza la frecuencia de aparición de letras o caracteres en el texto cifrado para deducir patrones y la clave.
* **Ataque de Canal Lateral (Side-Channel Attack):** No ataca el algoritmo criptográfico directamente, sino que explota información física "filtrada" durante la operación, como el consumo de energía del dispositivo, el tiempo de ejecución, las emisiones electromagnéticas o incluso el sonido, para deducir la clave.
* **Ataque de Criptoanálisis Diferencial:** Estudia cómo los cambios en el texto plano de entrada afectan los cambios en el texto cifrado de salida.
* **Ataque de Criptoanálisis Lineal:** Busca aproximaciones lineales en un cifrado por bloques.

En resumen, el criptoanálisis es el arte y la ciencia de romper códigos y sistemas de seguridad. Es una disciplina crucial que garantiza que los sistemas criptográficos que utilizamos sean verdaderamente seguros frente a las amenazas existentes.

---

# CrackStation

**CrackStation.net** es un servicio en línea popular y una herramienta de criptoanálisis que se utiliza principalmente para **romper hashes de contraseñas**. Su función principal es revertir funciones hash comunes (como MD5, SHA1, etc.) a sus contraseñas originales en texto plano, utilizando una gran base de datos de "rainbow tables" y otras técnicas de descifrado.

### ¿Para qué sirve CrackStation?

* **Recuperación de Contraseñas:** Permite a los usuarios intentar recuperar contraseñas de las que solo se tiene el valor hash. Esto puede ser útil en escenarios legítimos, como la recuperación de una contraseña olvidada de un sistema propio, o en escenarios de seguridad, para auditar la fortaleza de las contraseñas.
* **Auditoría de Seguridad:** Los profesionales de la seguridad y los pentesters utilizan CrackStation para probar la robustez de los hashes de contraseñas y determinar si las contraseñas utilizadas son débiles y fácilmente descifrables. Si un hash puede ser craqueado por CrackStation, indica que la contraseña asociada es vulnerable.
* **Análisis Forense:** En el ámbito forense, puede ser utilizado para intentar descifrar hashes de contraseñas encontrados en sistemas comprometidos, ayudando en la investigación de incidentes de seguridad.

### ¿Cómo funciona (de forma general)?

Cuando se ingresa un hash en CrackStation, el servicio lo compara con su vasta base de datos de hashes precalculados (rainbow tables) que mapean hashes a sus contraseñas originales. Si se encuentra una coincidencia, se devuelve la contraseña en texto plano. También se pueden emplear técnicas de fuerza bruta o ataques de diccionario si el hash no se encuentra directamente en sus tablas.

### Ejemplo de uso

Un administrador de sistemas podría imaginar que encuentra un hash de contraseña en un archivo de configuración antiguo y necesita saber cuál era la contraseña original para una cuenta de prueba creada hace mucho tiempo. El hash es `21232f297a57a5a743894a0e4a801fc3` y se sabe que es un hash MD5.

1.  **Acceso a CrackStation:** Se abre el navegador web y se navega a `https://crackstation.net/`.
2.  **Identificación del tipo de hash:** En la interfaz de CrackStation, se observa una lista de tipos de hash soportados (MD5, SHA1, SHA256, NTLM, etc.). Para este ejemplo, se debe asegurar que el tipo de hash MD5 esté seleccionado (o el que corresponda al hash).
3.  **Introducción del hash:** En el campo de texto provisto, se introduce el hash que se desea descifrar: `21232f297a57a5a743894a0e4a801fc3`.
4.  **Resolución del Captcha (si es necesario):** Para evitar el uso automatizado, CrackStation puede solicitar la resolución de un CAPTCHA.
5.  **Envío del hash:** Se hace clic en el botón "Crack Hashes" o similar para iniciar el proceso de descifrado.

**Resultado:**

Si el hash `21232f297a57a5a743894a0e4a801fc3` corresponde a una contraseña común o ha sido precalculado en las tablas de CrackStation, la herramienta mostrará la contraseña original en texto plano. En este caso, el hash `21232f297a57a5a743894a0e4a801fc3` corresponde a la contraseña `admin`.

### Consideraciones importantes

* **Legalidad y Ética:** El uso de herramientas de cracking de contraseñas debe realizarse siempre de manera legal y ética, con el consentimiento explícito del propietario del sistema o de la información. Su uso no autorizado para acceder a sistemas ajenos es ilegal.
* **Contraseñas Complejas:** CrackStation, como cualquier herramienta de cracking, es más efectiva contra contraseñas débiles, cortas o comunes. Contraseñas largas, complejas y aleatorias son mucho más difíciles, si no imposibles, de descifrar con este tipo de servicios.
* **Rainbow Tables:** Las "rainbow tables" son colecciones masivas de hashes precalculados. Cuanto más grande y completa sea la tabla, mayor será la probabilidad de encontrar una coincidencia.

CrackStation es una herramienta valiosa para entender las vulnerabilidades de las contraseñas y promover el uso de credenciales más seguras.
