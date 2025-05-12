# STARTUP Lab

This lab tests the student's ability to detect insecure configurations in network services and exploit the exposure of an NTLM hash in a public SMB resource. Students will learn to:

- Enumerate and access SMB resources without authentication.
- Identify sensitive files in shared systems.
- Use NTLM hashes for authentication (Pass-the-Hash).
- Remotely access Windows systems via WinRM.
- Read flags in Windows environments without privilege escalation.

## Machine Specifications 🖥️

- **System:** Windows Server 2019 or 2022
- **Hostname:** STARTUP
- **Active Services:**
    - 139 (NetBIOS)
    - 445 (SMB)
    - 5985 (WinRM)
    - 3389 (RDP) *(optional, not used in this challenge)*

- **Public Shared Folder:** `\\STARTUP\share`
- **Shared Resource Content:**
    - `alice_creds.txt`: contains simple non-privileged user credentials.
    - `todo.txt`: contains a hint suggesting to check a backup file.
    - `backup.zip`: contains a valid NTLM hash for the `Administrator` user.

## 🏁 Flag

- **Location:** `C:\Users\Administrator\Desktop\flag.txt` 

### Machine Credentials

```bash
hostname: startup-lab
username: Administrator
password: 4geeks-lab
```

## Expected Steps for the Student

1. **Discover the IP of the STARTUP machine.**
     - Use tools like `nmap`, `netdiscover`, or `smbclient -L`.

2. **Connect to the SMB shared resource without authentication.**
     - Example command:
         ```bash
         smbclient //startup/share -N
         ```

3. **Review the content of the files in the shared resource.**
     - `alice_creds.txt` and `todo.txt` provide context, but the focus is on `backup.zip`.

4. **Extract the NTLM hash from the `backup.zip` file.**
     - The student should unzip and read the hash from `admin_hash.txt`.

5. **Access the system using Pass-the-Hash with Evil-WinRM.**
     - Command:
         ```bash
         evil-winrm -i <IP> -u Administrator -H <HASH>
         ```

6. **Find and read the flag.**
     - Navigate to the administrator's desktop:
         ```powershell
         cd C:\Users\Administrator\Desktop
         type flag.txt
         ```
