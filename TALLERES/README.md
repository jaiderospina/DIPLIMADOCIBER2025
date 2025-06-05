# Taller  No 1 en grupo.

**Introdución**

Como se ha desarrollado en clase el Cyber Kill Chain fue desarrollada por Lockheed Martin como una analogía del modelo militar conocido como **Kill chain  F2T2EA**, aplicada al ciclo de vida de un ciberataque. Es útil para entender cómo operan los atacantes y cómo interrumpir sus acciones en cada fase.

A continuación realizar la siguiente lectura e identificar (si aplica) cada una de las fases del modelo propuesto por Lockheed Martin.

- Realizar una discusión y concertación como grupo y presentar al resto de la clase.

---

### **"La Simetría del Espejo"**

Las luces de neón destellaban sobre las avenidas de Cristaluna, una ciudad que parecía viva, conectada por una red invisible de datos, personas y decisiones. En el piso 23 de la torre GlassNet, una joven ingeniera llamada Maia revisaba la rutina de la red interna, ajena al juego de sombras que se movía tras los cables de fibra óptica.

Al otro lado del mundo, en una habitación sin ventanas, un hombre encapuchado sonreía frente a tres monitores. La habitación estaba repleta de calor silencioso: racks pequeños, routers modificados, discos rotulados con fechas y nombres de empresas que ya no existían. Un perfil se abría ante él, uno que había estado observando durante semanas. La empleada de GlassNet, Maia Torres. Ingeniera de seguridad con acceso al backend de la infraestructura de red. Exalumna de la Universidad de Antioquía. Activa en foros de código abierto. Recientemente interesada en soluciones de automatización de backups.

—Perfecto... —murmuró el hombre.

En la pantalla apareció un listado de suscripciones, correos, publicaciones en foros. La máscara digital ya estaba casi completa.

Horas después, Maia recibió un mensaje en su bandeja de entrada personal, no el institucional. Provenía de un remitente que reconoció: una comunidad de desarrolladores colombianos que solía consultar. El mensaje era claro, directo: *“Concurso de soluciones de backup en AWS. Gana visibilidad y premios.”* Había un PDF con instrucciones, links a documentación y un script en Python adjunto. Lo escaneó rápidamente, parecía limpio.

Lo abrió. Ejecutó la parte del código que analizaba conexiones S3. Nada sucedió. Supuso que era un error de su configuración y lo dejó para más tarde.

La terminal seguía abierta. Lo que Maia no sabía era que, en segundo plano, una pequeña carga de datos ya estaba corriendo, introducida en su sistema como una capa oculta dentro del script. Un troyano disfrazado de utilitario inofensivo que ahora escuchaba. Y aprendía.

---

En los días siguientes, la rutina de Maia siguió como siempre. Pero alguien más la seguía en silencio. Cada comando que escribía, cada puerta que abría, cada cambio que hacía en la infraestructura, era replicado en un archivo binario oculto y enviado, lentamente, comprimido y cifrado, hacia un servidor intermediario.

Los registros del sistema empezaron a alterarse mínimamente. Paquetes extraños cruzaban puertos poco comunes. Nadie en GlassNet parecía notarlo. O más bien, nadie estaba buscando eso.

Desde su guarida digital, el atacante estableció un canal oculto entre el servidor de Maia y una red de control alojada en un contenedor en la dark web. Los comandos eran pequeños, cuidadosamente ofuscados: permisos que se elevaban, procesos que se iniciaban al arranque, y conexiones que fingían ser parte del tráfico regular de monitoreo.

Los días pasaron, y un nuevo ciclo de actualizaciones de seguridad estaba por lanzarse. GlassNet estaba en plena migración a una plataforma híbrida, y Maia era la encargada de la integración. Durante una madrugada de pruebas, un archivo comprimido y firmado fue subido al repositorio interno como parte del proceso de sincronización. Era legítimo, pero contenía algo más: una réplica modificada por alguien que ya conocía los flujos internos.

El paquete fue desplegado automáticamente.

Y con él, se activó un módulo que liberó procesos ocultos en los servidores de balanceo de carga. Una vez dentro, el atacante accedió a bases de datos internas, tokens API y certificados válidos. Era un acceso total, quirúrgico, sin ruido.

---

A la mañana siguiente, los indicadores seguían verdes. Maia revisó los reportes de la noche anterior: todo parecía en orden. Sin embargo, un patrón en los logs la inquietó. Cadenas repetidas, llamadas fuera de hora. Consultó con el equipo, pero nadie parecía alarmado.

Esa noche, decidió rastrear las anomalías por su cuenta.

Mientras tanto, al otro lado de la conexión, el atacante iniciaba la fase final: el movimiento de datos hacia un depósito oculto. Miles de registros de clientes, diagramas de red, configuraciones de routers, todo comprimido y enviado en lotes de 50 MB. Un algoritmo de retardo permitía que el tráfico se distribuyera en patrones aleatorios para evitar detección.

Sin embargo, Maia estaba observando ahora. Y su mirada no era la de una usuaria promedio. Mientras navegaba entre flujos de red y encabezados IP, empezó a ver la simetría. Algo replicaba sus acciones, como un espejo. Cada intento suyo por acceder a ciertos segmentos iba acompañado de un eco, una sombra. Lo que comenzó como sospecha pronto se volvió certeza.

Activó manualmente un protocolo de cuarentena sobre los nodos que servían de pivote. Pero era tarde.

En los servidores comprometidos, los procesos comenzaron a autodestruirse. El código malicioso fue diseñado para cubrir sus huellas. Quedaban rastros, sí, pero eran difusos. Un patrón roto. Un rompecabezas sin piezas claves.

---

Días después, una investigación interna confirmaría lo que Maia ya sabía: la infraestructura de GlassNet había sido comprometida. El informe hablaba de una “intrusión compleja”, sin especificar los métodos. Pero Maia entendía la lógica detrás del ataque. Era como si alguien hubiera seguido un manual de guerra silenciosa.

Pensó en cada fase. El acercamiento inicial, la forma en que se plantó la semilla, la conexión con su curiosidad como ingeniera. La progresión metódica. El silencio del ataque.

Y entonces recordó las palabras de su mentor: *"Los mejores ataques son simétricos. Reflejan tus hábitos, tus pasos. No luchan contra ti. Caminan contigo."*

Desde entonces, Maia ya no confiaba en los espejos.

---

### Epílogo

En una red lateral, una cuenta que no aparecía en ningún inventario seguía activa. No hacía nada. Solo existía. Como una cicatriz invisible. Como un mensaje para quien supiera mirar.

**---**
**---**
---
### Taller No 2.

De mnera individual investigar que es **Virus Total** e identificas casos de uso.
- **Virus Total** (https://www.virustotal.com/learn/)
