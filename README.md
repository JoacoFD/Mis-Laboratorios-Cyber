# Reporte Técnico de Laboratorio: Attacktive Directory
**Plataforma:** TryHackMe  
**Enfoque:** Simulación de Adversario y Análisis de Detección (Blue Team)

---

## 1. Objetivo del Proyecto
El propósito de este laboratorio es identificar y explotar vulnerabilidades críticas en un entorno de **Active Directory (AD)** basado en Windows. El análisis se centra en el compromiso de la cadena de autenticación de Kerberos y la escalada de privilegios, proporcionando una visión desde la perspectiva del **Analista SOC** para identificar Indicadores de Compromiso (IoCs) y proponer medidas de mitigación efectivas.

## 2. Metodología de Seguridad
Se sigue un enfoque basado en el framework **MITRE ATT&CK**, cubriendo las fases de Reconocimiento, Acceso Inicial y Enumeración de privilegios.

---

## 3. Fase 1: Reconocimiento y Análisis de Superficie de Ataque
Se ejecutó un escaneo de red exhaustivo para mapear los servicios del Controlador de Dominio (DC).

### Evidencia Técnica:
**Comando ejecutado:**
`nmap -p- --open -sS -sC -sV --min-rate 5000 -vvv -n -Pn 10.65.152.175`

![Resultado de Nmap](nmap_result.png)

### Análisis de Exposición (Visión SOC):
* **Identificación de Activos:** La exposición de los puertos **88 (Kerberos)**, **389 (LDAP)** y **445 (SMB)** confirma que el activo es un Controlador de Dominio (Tier 0) para el dominio `spookysec.local`.
* **Vulnerabilidad de Enumeración:** El servicio LDAP y SMB permiten obtener información sobre la estructura de objetos del dominio, mientras que Kerberos permite validar usuarios mediante ataques de fuerza bruta.
* **Detección de Intrusos:** Un escaneo con `--min-rate 5000` es altamente ruidoso y dispararía alertas de **"Port Scanning"** en un sistema de monitoreo. Como analista SOC, este es el primer IoC (Indicador de Compromiso) a investigar.

---

## 4. Fase 2: Enumeración de Usuarios (Kerberos Brute Force)
*(Próximamente: Documentación de la fase de Kerbrute y análisis de Event IDs 4768/4771)*
