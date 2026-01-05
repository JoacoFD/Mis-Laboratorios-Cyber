<img width="1917" height="927" alt="image" src="https://github.com/user-attachments/assets/1b4b250a-71fc-4fe4-854e-53aacd7c3a0a" /># Informe de Laboratorio: Attacktive Directory

## 1. Fase de Reconocimiento
Se realizó un escaneo detallado de la red para identificar los servicios activos en el Controlador de Dominio.

**Comando utilizado:**
`nmap -p- --open -sS -sC -sV --min-rate 5000 -vvv -n -Pn -oN Escaneo 10.65.174.111`

### Análisis de Resultados:
* **Dominio:** `spookysec.local`
* **Hostname:** `ATTACKTIVEDIRECTORY`
* **Puertos Críticos:** 88 (Kerberos), 135/139/445 (RPC/SMB), 389/3268 (LDAP).

<img width="1917" height="927" alt="image" src="https://github.com/user-attachments/assets/ce7b2a23-640e-48d2-92a6-d44ced31bdf6" />


### Perspectiva SOC (Detección):
Desde el punto de vista de monitoreo, este escaneo es altamente agresivo (`--min-rate 5000`).
1. **Detección:** Un sistema IDS/IPS detectaría el barrido de puertos TCP SYN.
2. **Evento de Windows:** La enumeración LDAP (puerto 389) generaría logs de búsqueda masiva en el Directorio Activo, lo cual es un indicador de reconocimiento (Reconnaissance).
