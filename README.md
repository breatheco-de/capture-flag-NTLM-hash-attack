# STARTUP - NTLM Hash Attack via Public SMB

In this lab, you will face a Windows machine configured with insecure shared resources. The goal is to gain access as **Administrator** using an exposed **NTLM hash**, without needing to know the password. In this lab, you will learn:

- SMB resource enumeration
- Identifying sensitive files in shared folders
- Using NTLM hashes for authentication (Pass-the-Hash)
- Remote access to Windows via WinRM
- Reading flags in Windows environments

<how-to-start>
   
## 🌱 How to Start This Lab

Follow these instructions to get started:

1. **Download the virtual machine** from this [link](https://storage.googleapis.com/cybersecurity-machines/startup-lab.ova).
2. **Import the machine** into your preferred virtualization manager (VirtualBox, VMware, etc.).
3. Once the machine is running, you can start the lab!

</how-to-start>

## 📄 Instructions

You are dealing with a startup's machine that has left some services misconfigured. Your mission is to analyze the exposed resources and compromise the system using the information obtained.

1. **Discover the IP address of the STARTUP machine.**: The machine is connected to the same network as you, but its IP has not been provided. Use tools like `nmap`, `netdiscover`, or `smbclient -L` to scan and detect services.

2. **Connect to the public SMB shared resource.**: Explore the shared resource.

3. **Analyze the content of the files you find.**

4. **Connect to the machine using the NTLM hash.**

5. **Search for the flag in the Administrator's files.**

   
**Remember:** You don't always need a password... sometimes, a hash is enough.

Good luck!