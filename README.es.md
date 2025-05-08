# STARTUP - Ataque con Hash NTLM vía SMB Público

En este laboratorio vas a enfrentarte a una máquina Windows configurada con recursos compartidos inseguros. El objetivo es obtener acceso como **Administrator** utilizando un **hash NTLM** expuesto, sin necesidad de conocer la contraseña. En este laboratorio aprenderás:

- Enumeración de recursos SMB
- Reconocimiento de archivos sensibles en carpetas compartidas
- Uso de hashes NTLM para autenticación (Pass-the-Hash)
- Acceso remoto a Windows vía WinRM
- Lectura de flags en entornos Windows

<how-to-start>
   
## 🌱 Cómo iniciar este laboratorio

Sigue las siguientes instrucciones para comenzar:

1. **Descarga la máquina virtual** desde este [enlace](https://storage.googleapis.com/cybersecurity-machines/startup-lab.ova).
2. **Importa la máquina** en tu gestor de virtualización preferido (VirtualBox, VMware, etc.).
3. Una vez iniciada la máquina, ¡ya puedes comenzar con el laboratorio!
</how-to-start>


## 📄 Instrucciones

Estás frente a una máquina de una startup que ha dejado algunos servicios mal configurados. Tu misión es analizar los recursos expuestos y comprometer el sistema a través de la información obtenida.

1. **Descubre la dirección IP de la máquina STARTUP.**: La máquina está conectada a la misma red que tú, pero su IP no ha sido proporcionada. Utiliza herramientas como `nmap`, `netdiscover` o `smbclient -L` para escanear y detectar servicios.

2. **Conéctate al recurso compartido SMB público.**: Explora el recurso compartido

3. **Analiza el contenido de los archivos que encuentres**

4. **Conéctate a la máquina usando el hash NTLM.**

5. **Busca la flag en los archivos del Administrador**

   
**Recuerda:** No siempre necesitás una contraseña... a veces, un hash es suficiente.

¡Buena suerte!
