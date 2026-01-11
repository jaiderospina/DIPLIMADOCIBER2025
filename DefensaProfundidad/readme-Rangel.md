## 1. Análisis de Amenazas y Vulnerabilidades

### Amenazas Identificadas:

* **Phishing dirigido (spear phishing)** que suplanta a la dirección de TI.
* **Explotación de vulnerabilidad de día cero** en software no actualizado en la DMZ.
* **Descarga de malware** desde redes sociales profesionales.
* **Movimiento lateral** interno para escanear y comprometer sistemas.
* **Escalada de privilegios** y persistencia con cuentas ocultas.
* **Exfiltración de datos y ransomware** en sistemas críticos.

### Vulnerabilidades Clave:

* Ausencia de protección contra phishing y concientización insuficiente.
* Sistemas obsoletos sin parches en la zona pública.
* Falta de segmentación interna efectiva.
* Insuficiente monitoreo y control de actividad de red y endpoints.
* Políticas de identidad y acceso mal definidas.
* Ausencia de protección avanzada contra ransomware.

---

## 2. Principios de Defensa en Profundidad

La estrategia se basa en establecer **múltiples capas de seguridad**, redundantes y complementarias, para dificultar el avance de los atacantes. Si una capa es vulnerada, otras deben mitigar el impacto. Las capas combinan controles físicos, técnicos y administrativos.

---

## 3. Capas de Defensa Propuestas

### Capa 1: Perímetro / Red Externa

* Firewalls de próxima generación (NGFW).
* Web Application Firewalls (WAF) para proteger aplicaciones públicas.
* Servicios anti-DDoS (nativos de AWS/Azure).
* Segmentación entre red corporativa y servicios en la nube.
* Geobloqueo y listas negras de IP.

### Capa 2: Red Interna / Segmentación

* VLANs por rol y departamento.
* Microsegmentación con SDN (Software-Defined Networking).
* Zero Trust Network Access (ZTNA).
* Monitoreo de tráfico este-oeste con Network Detection & Response (NDR).

### Capa 3: Endpoints / Dispositivos

* EDR (Endpoint Detection and Response) en todas las estaciones.
* Antivirus/antimalware con protección de comportamiento.
* Control de dispositivos USB.
* Parcheo automático y controlado.
* Aislamiento de navegadores para usuarios críticos.

### Capa 4: Aplicaciones

* Revisión continua del ciclo de vida del software (DevSecOps).
* Integración de escáneres de vulnerabilidades en CI/CD.
* Autenticación fuerte en accesos (OAuth2, SAML).
* Pruebas de pentesting periódicas.

### Capa 5: Datos

* Cifrado en reposo y en tránsito (TLS, AES-256).
* Data Loss Prevention (DLP) para detectar exfiltración.
* Clasificación de datos sensibles.
* Backups frecuentes, versionados y almacenados offline.

### Capa 6: Identidad y Acceso

* Autenticación multifactor (MFA) obligatoria.
* Políticas de mínimo privilegio (Least Privilege Access).
* Revisión y auditoría de roles de IAM (en nube y on-prem).
* Detectar y bloquear cuentas inactivas o sospechosas.

### Capa 7: Operaciones y Concientización

* Simulaciones de phishing y capacitación regular.
* Manuales de respuesta a incidentes y planes de continuidad.
* Implementación de SIEM + SOAR para orquestación de eventos.
* Auditorías y revisiones de cumplimiento (ISO 27001, NIST).

---

## 4. Respuesta al Incidente (Fases Inmediatas)

1. **Contención**

   * Aislar estaciones de trabajo afectadas.
   * Detener el tráfico hacia direcciones IP sospechosas.
   * Deshabilitar cuentas comprometidas y sesiones activas.

2. **Erradicación**

   * Ejecutar EDR para eliminar malware persistente.
   * Revocar credenciales comprometidas.
   * Verificar integridad de sistemas clave.

3. **Recuperación**

   * Restaurar backups verificando que estén libres de ransomware.
   * Aplicar parches pendientes y actualizar todo el software.
   * Validar integridad de la red antes de reconectar sistemas.

4. **Análisis Post-Incidente**

   * Análisis forense de logs y eventos.
   * Actualizar estrategias y controles basados en hallazgos.

---

## 5. Monitoreo y Mejora Continua

* Revisión mensual de logs y alertas de seguridad.
* Simulacros de ataque (red teaming/purple teaming).
* Evaluaciones de vulnerabilidad y pruebas de penetración trimestrales.
* Actualización de políticas y capacitaciones cada 6 meses.
* Auditorías externas de cumplimiento anuales.

---
