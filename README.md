Reporte Técnico de Laboratorio: Attacktive Directory
Plataforma: TryHackMe

Enfoque: Simulación de Adversario y Análisis de Detección (Blue Team)

1. Objetivo del Proyecto
El propósito de este laboratorio es identificar y explotar vulnerabilidades críticas en un entorno de Active Directory (AD) basado en Windows. El análisis se centra en el compromiso de la cadena de autenticación de Kerberos y la escalada de privilegios, proporcionando una visión desde la perspectiva del Analista SOC para identificar Indicadores de Compromiso (IoCs) y proponer medidas de mitigación efectivas.

2. Metodología de Seguridad
Se sigue un enfoque basado en el framework MITRE ATT&CK, cubriendo las fases de Reconocimiento, Acceso Inicial y Enumeración.

3. Fase 1: Reconocimiento y Análisis de Superficie de Ataque
Se ejecutó un escaneo de red exhaustivo para mapear los servicios del Controlador de Dominio (DC).

Evidencia Técnica:
<img width="1917" height="927" alt="image" src="https://github.com/user-attachments/assets/23a86298-e791-44ae-9147-f83eb83a9506" />

Análisis de Exposición (Visión SOC):
Vector de Ataque Identificado: La exposición de los puertos 88 (Kerberos) y 389 (LDAP) confirma que el activo es un Controlador de Dominio. Esto lo convierte en el objetivo de mayor prioridad (Tier 0).

Riesgo de Enumeración: El servicio LDAP permite obtener información sobre la estructura de objetos del dominio, mientras que Kerberos es susceptible a ataques de fuerza bruta de usuarios.

Detección: Un escaneo con --min-rate 5000 genera un volumen de paquetes por segundo que debería disparar una alerta de "Threshold-based Port Scan" en cualquier SIEM o IDS configurado correctamente.
