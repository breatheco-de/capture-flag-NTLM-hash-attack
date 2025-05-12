# Laboratorio STARTUP

Este laboratorio pone a prueba la capacidad del alumno para detectar configuraciones inseguras en servicios de red y explotar la exposición de un hash NTLM en un recurso SMB público. De esta forma, los alumnos lograrán comprender:

- Enumeración y acceso a recursos SMB sin autenticación.
- Identificación de archivos sensibles en sistemas compartidos.
- Uso de hashes NTLM para autenticación (Pass-the-Hash).
- Acceso remoto a sistemas Windows mediante WinRM.
- Lectura de flags en entornos Windows sin necesidad de escalar privilegios.

## Especificaciones de la máquina 🖥️

- **Sistema:** Windows Server 2019 o 2022
- **Hostname:** STARTUP
- **Servicios activos:**
  - 139 (NetBIOS)
  - 445 (SMB)
  - 5985 (WinRM)
  - 3389 (RDP) *(opcional, no utilizado en este reto)*

- **Carpeta compartida pública:** `\\STARTUP\share`
- **Contenido del recurso compartido:**
  - `alice_creds.txt`: contiene credenciales simples de usuario sin privilegios.
  - `todo.txt`: contiene una pista que sugiere revisar un archivo de backup.
  - `backup.zip`: contiene un hash NTLM válido del usuario `Administrator`.

## 🏁 Flag

- **Ubicación:** `C:\Users\Administrator\Desktop\flag.txt` 


### Credenciales de la máquina

```bash
hostname: startup-lab
username: Administrator
password: 4geeks-lab
```

## Pasos esperados por el alumno

1. **Descubrir la IP de la máquina STARTUP.**
   - Utiliza herramientas como `nmap`, `netdiscover` o `smbclient -L`.

2. **Conectarse al recurso compartido SMB sin autenticación.**
   - Comando de ejemplo:
     ```bash
     smbclient //startup/share -N
     ```

3. **Revisar el contenido de los archivos en el recurso compartido.**
   - `alice_creds.txt` y `todo.txt` aportan contexto, pero el foco está en `backup.zip`.

4. **Extraer el hash NTLM del archivo `backup.zip`.**
   - El alumno debe descomprimir y leer el hash desde `admin_hash.txt`.

5. **Acceder al sistema mediante Pass-the-Hash con Evil-WinRM.**
   - Comando:
     ```bash
     evil-winrm -i <IP> -u Administrator -H <HASH>
     ```

6. **Encontrar y leer la flag.**
   - Navegar al escritorio del administrador:
     ```powershell
     cd C:\Users\Administrator\Desktop
     type flag.txt
     ```

