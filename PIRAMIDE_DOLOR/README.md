
La **Pirámide del Dolor** en ciberseguridad es un modelo conceptual creado por David J. Bianco que clasifica diferentes tipos de indicadores de compromiso (**IOCs, Indicators of Compromise**) según el nivel de dificultad (o "dolor") que supone para un atacante si un defensor los detecta y actúa sobre ellos.

El objetivo de esta pirámide es ayudar a los analistas de seguridad a centrarse en los indicadores que realmente afectan las capacidades del atacante, no solo en los más fáciles de identificar.

---

### Estructura de la Pirámide del Dolor (de menor a mayor dolor para el atacante):

| Nivel | Indicador                                      | Dolor para el atacante | Descripción                                                                                                                   |
| ----- | ---------------------------------------------- | ---------------------- | ----------------------------------------------------------------------------------------------------------------------------- |
| 1     | **Hash de archivo**                            | Muy bajo               | Identificador único de un archivo malicioso. Muy fácil de cambiar.                                                            |
| 2     | **Dirección IP**                               | Bajo                   | Los atacantes pueden cambiar fácilmente de IP (por proxies, VPN, etc.).                                                       |
| 3     | **Nombre de dominio**                          | Moderado               | Algo más costoso de reemplazar que una IP, pero sigue siendo fácil.                                                           |
| 4     | **URL**                                        | Moderado-Alto          | Cambiarla implica modificar infraestructura o enlaces maliciosos.                                                             |
| 5     | **Dirección de correo / Artefactos**           | Alto                   | Cambiar herramientas específicas o direcciones usadas implica rediseño.                                                       |
| 6     | **TTPs (Tácticas, Técnicas y Procedimientos)** | Muy alto               | Representan el comportamiento del atacante. Cambiarlas requiere esfuerzo, reentrenamiento y rediseño profundo de operaciones. |

---

### Ejemplos para cada nivel

1. **Hash de archivo**

   * Ejemplo: `d41d8cd98f00b204e9800998ecf8427e`
   * Significado: Hash MD5 de un ejecutable malicioso. Si se detecta y bloquea, el atacante solo cambia el archivo y genera un nuevo hash.

2. **Dirección IP**

   * Ejemplo: `185.234.219.10`
   * Significado: IP de un servidor de comando y control. Al ser detectado, el atacante cambia de IP y sigue operando.

3. **Dominio**

   * Ejemplo: `malicioso-c2.example.com`
   * Significado: Dominio que aloja malware o sirve como centro de comando. Más complejo de reemplazar (requiere configuración y registro), pero factible.

4. **URL**

   * Ejemplo: `http://malware.site/downloads/payload.exe`
   * Significado: Ruta específica usada para descargar un malware. Si se bloquea, se debe crear una nueva URL y actualizar el malware.

5. **Correo / Artefactos**

   * Ejemplo: Dirección usada para phishing: `hr@fakecorp.com` o herramientas como `Mimikatz`, `Cobalt Strike`.
   * Significado: Cambiar direcciones o reconfigurar herramientas es más costoso que solo cambiar IPs o hashes.

6. **TTPs (Tactics, Techniques, and Procedures)**

   * Ejemplo: Uso de **movimiento lateral con PsExec**, **exfiltración vía DNS tunneling**, **persistencia mediante Run keys**.
   * Significado: Cambiar comportamientos o metodologías implica alterar la forma de operar del atacante, lo cual consume tiempo, recursos y experiencia.

---

### Conclusión

* Los indicadores en la **base de la pirámide** (hashes, IPs) son fáciles de recolectar pero también fáciles de evadir.
* Los indicadores en la **cima de la pirámide** (TTPs) son más difíciles de recolectar, pero si se detectan, **realmente interrumpen y frustran** al atacante.
* **Objetivo del defensor:** centrar esfuerzos en identificar y entender los TTPs, y no depender exclusivamente de listas de IOCs básicos.


## Ejemplos de Uso.
---

### 🔍 **Caso 1: APT29 (Cozy Bear) – Campaña contra el gobierno de EE. UU.**

#### Contexto:

APT29 es un grupo de amenazas persistentes avanzadas (APT) atribuido al servicio de inteligencia ruso. Fue famoso por su participación en el **hackeo del DNC en 2016** y múltiples campañas dirigidas a agencias gubernamentales de EE. UU.

#### Indicadores en juego:

* **Hash de archivo**: Las muestras de malware (`WellMess`, `WellMail`) usadas eran detectadas y bloqueadas por firmas, pero fácilmente reemplazables.

  * ➤ Poco dolor para el atacante.

* **IPs y dominios**: Se bloquearon las IPs y dominios de los C2 (Comando y Control), pero APT29 rotaba estas rápidamente.

  * ➤ Dolor bajo a moderado.

* **TTPs**: APT29 usaba tácticas como:

  * Spear-phishing con archivos Excel y macros,
  * Uso de credenciales legítimas robadas para moverse lateralmente,
  * Persistencia mediante servicios legítimos como Microsoft Azure y GitHub.

  Cuando se detectaron **estos comportamientos**, muchas agencias gubernamentales y empresas privadas configuraron **detecciones basadas en comportamiento** y no en indicadores fijos.

  * ➤ Esto **forzó a APT29 a rediseñar su cadena de ataque**, cambiar herramientas y modificar su modo de operar.

#### Conclusión:

El cambio de foco desde IOCs simples a TTPs representó **una gran pérdida de eficiencia** para APT29. Algunos analistas reportaron una pausa operativa de semanas mientras cambiaban su infraestructura y procedimientos.

---

### 🔍 **Caso 2: SolarWinds (SUNBURST backdoor)**

#### Contexto:

En 2020, se descubrió que atacantes habían comprometido la cadena de suministro del software **SolarWinds Orion**, inyectando un backdoor llamado **SUNBURST**. El ataque afectó a agencias del gobierno de EE. UU. y empresas como Microsoft, FireEye, entre otras.

#### Indicadores en juego:

* **Hash de archivo**: Inicialmente, las versiones comprometidas de `Orion.dll` fueron identificadas por hash.

  * ➤ Fácil de cambiar, pero útil para detección rápida.

* **Dominios**: El dominio principal de C2 era `avsvmcloud[.]com`. Al ser descubierto y sinkholeado por Microsoft y FireEye, los atacantes perdieron control sobre muchas víctimas.

  * ➤ Dolor moderado.

* **Artefactos y herramientas**:

  * El backdoor SUNBURST estaba oculto y diseñado para parecer tráfico legítimo.
  * El atacante usó técnicas de evasión avanzadas (por ejemplo, comunicación retardada, DNS-based beaconing).
  * Las herramientas de post-explotación usaban certificados válidos para parecer legítimas.

* **TTPs**:

  * Persistencia en procesos legítimos,
  * Múltiples capas de evasión de EDR,
  * Uso de redes internas para escalar privilegios.

  Cuando los investigadores identificaron estos patrones, se implementaron reglas de comportamiento (detecciones basadas en técnicas, no archivos) en plataformas como **MITRE ATT\&CK**, y herramientas como **Sigma**, **YARA** y **EDR** comenzaron a detectar estos comportamientos.

  * ➤ Esto obligó al actor a **abandonar SUNBURST y no reutilizar las mismas técnicas**.

#### Conclusión:

La respuesta basada en TTPs (en lugar de solo bloquear hashes) resultó **mucho más efectiva**, generando **costos operacionales y de rediseño** para los atacantes.

---

### Conclusión General

Estos casos reales demuestran que:

* Reaccionar solo con indicadores técnicos como IPs o hashes **tiene impacto limitado**.
* Detectar y responder a TTPs **aumenta el "dolor" del atacante**, forzándolo a modificar su infraestructura, herramientas y metodología.

Por eso, las organizaciones maduras en ciberseguridad integran frameworks como **MITRE ATT\&CK**, **detección basada en comportamiento**, y **threat hunting proactivo** para ir más allá de los indicadores simples.

**Pirámide del Dolor aplicada al caso SolarWinds (SUNBURST)**, donde se ilustran los indicadores utilizados durante la respuesta al incidente y el nivel de "dolor" que causaron al atacante:

---

### **Pirámide del Dolor – Caso SolarWinds (SUNBURST)**

| Nivel | Tipo de Indicador                              | Ejemplo Real                                                                                 | Dolor para el atacante | Impacto operativo                                                                                      |
| ----- | ---------------------------------------------- | -------------------------------------------------------------------------------------------- | ---------------------- | ------------------------------------------------------------------------------------------------------ |
| 1     | **Hash de archivo**                            | `32519c8131d8b36c8b1852d11e8ef1e7` (SUNBURST DLL)                                            | Muy bajo               | Los atacantes pueden recompilar el código fácilmente.                                                  |
| 2     | **Dirección IP**                               | `13.59.205.66` (C2 IP inicial)                                                               | Bajo                   | Reemplazable con otra IP o infraestructura cloud.                                                      |
| 3     | **Nombre de dominio**                          | `avsvmcloud[.]com`                                                                           | Moderado               | Requiere configuración y evasión de reputación DNS. Fue tomado por Microsoft (sinkholed).              |
| 4     | **URL específica**                             | `https://api.solarwinds.com/Orion/Activity`                                                  | Moderado-Alto          | Cambiarla implica modificar el malware y volver a distribuirlo.                                        |
| 5     | **Artefactos y herramientas**                  | `SUNBURST`, `TEARDROP`, certificados firmados                                                | Alto                   | Herramientas muy sofisticadas, personalizadas y difíciles de reemplazar sin perder capacidad ofensiva. |
| 6     | **TTPs (tácticas, técnicas y procedimientos)** | Uso de DLL sideloading, comunicación encubierta vía DNS, persistencia en servicios legítimos | Muy alto               | Al ser detectadas las TTPs, perdieron su vector sigiloso. Requiere rediseño operativo y táctico.       |

---

### Análisis:

* Mientras los **hashes y direcciones IP** ayudaron en la **detección rápida**, los atacantes **siguieron operando sin grandes obstáculos**.
* Pero cuando los defensores detectaron las **herramientas personalizadas y patrones de comportamiento**, se generó una **respuesta coordinada** que obligó a los atacantes a:

  * Detener sus operaciones activas.
  * Abandonar SUNBURST.
  * Rediseñar su conjunto de herramientas (toolset).
  * Cambiar tácticas de infiltración y persistencia.

---

### Conclusión:

Este caso reafirma que **apuntar a los niveles superiores de la Pirámide del Dolor es clave para neutralizar amenazas APT sofisticadas**. Las organizaciones que integraron detecciones de TTPs (como detección de uso anómalo de DNS, comportamiento de procesos firmados, y tráfico irregular desde Orion) **lograron mitigaciones más efectivas** que aquellas que solo aplicaron listas de hashes o dominios.


**Referencias**

- https://www.picussecurity.com/resource/glossary/what-is-pyramid-of-pain
- 
