[](https://github.com/Karthikeyan-Appu/Ubuntu-Server-Config/assets/ubuntu.png)
# Ubuntu Server Configuration 
This repository documents the setup and configuration of an Ubuntu Server for hosting web applications. The project includes detailed instructions and best practices to create a secure and efficient server environment.

Ubuntu is a free and open-source Linux distribution based on Debian. Developed and maintained by Canonical Ltd., Ubuntu is designed to be user-friendly, stable, and secure, making it a popular choice for both newcomers and experienced users of Linux. Known for its ease of use, Ubuntu provides a comprehensive operating system suitable for desktops, servers, and even cloud environments.
## Prerequisites
- Ubuntu Server 20.04 or later
    https://ubuntu.com/download/server#release-notes-lts
- Use any tools like Ventoy / Power ISO / Linux Inbuilt service for creating a USB bootable device.
- AFter completion boot into the bootable device through bootmenu / changing the boot priority
- Go through basic installation procedure [ Language / Internet Access / Server name / User name and Password (Make sure to note these credentials ).
- Choose "Entire Disk " option - Storage allocation
- Select Install "Open SSH" - for secure remote acesss.
- Wait for the completion and reboot the system alongwith removing the bootable device.
- You will be directed to CLI of the server login.

Note : I am using the Minimal Version for installation.


## Basic Package Installation
1. Update and upgrade the package list:
   ```bash
   sudo apt update && sudo apt upgrade
2. Install basic packages
    ```bash
    sudo apt install nano wget curl net-tools rysylog
    
## 1. Secure Shell (SSH) 
> Is a cryptographic network protocol used for secure communication over an unsecured network. SSH is commonly used for remote login to a computer system, allowing users and system administrators to control and modify their servers and systems from afar.
[](https://github.com/Karthikeyan-Appu/Ubuntu-Server-Config/assets/ssh.jpg)

 **Key features include:**

 **Encryption:** SSH uses strong encryption techniques to ensure that the data transmitted between the client and server is secure.

 **Authentication:** Supports various authentication methods including passwords and public key authentication.

 **Port Forwarding:** Allows secure tunneling of other network services over SSH.

 **Secure File Transfer:** Protocols such as SCP (Secure Copy) and SFTP (SSH File Transfer Protocol) enable secure file transfer.

SSH is widely used in many applications, from system administration and network management to secure file transfers and more. Its ability to provide a secure communication channel makes it a fundamental tool in the world of IT.

[**Installation and Configuration**](ssh_installation.md)


## 2. File Transfer Protocol (FTP)  
is a standard network protocol used to transfer files between a client and a server over a network. It is one of the oldest protocols still in use and is widely employed for uploading and downloading files on the internet.

[](https://github.com/Karthikeyan-Appu/Ubuntu-Server-Config/assets/FTP.jpg)

**Key Features of FTP:**

**File Transfer:** Allows for the transfer of files in both directions—uploading and downloading.

**Authentication:** Supports both anonymous and authenticated access, typically using username and password.

**Directory Browsing:** Provides capabilities to browse directories and manage files on the remote server.

### VSFTPD (Very Secure FTP Daemon)
is an FTP server for Unix-like systems, including Linux. Known for its security, performance, and stability, VSFTPD is the preferred choice for many administrators to deploy FTP services.

**Key Features of VSFTPD:**

**Security:** Implements a variety of security measures, including chroot jails, SSL/TLS encryption, and more to ensure secure file transfers.

**Performance:** Designed to handle numerous connections efficiently, providing high performance and stability.

**Configurability:** Offers extensive configuration options to tailor the server to specific needs and requirements.

VSFTPD is trusted for its security and robustness, making it a reliable option for providing FTP services in both personal and professional settings.

[Installation and Configuration](ftp_installation.md)


## 3. Fail2Ban

Is an open-source tool designed to prevent brute-force attacks and unauthorized access to servers. It scans log files for suspicious behavior (like repeated failed login attempts) and temporarily bans offending IP addresses, typically by modifying firewall rules.
[](https://github.com/Karthikeyan-Appu/Ubuntu-Server-Config/assets/fail2ban.jpg)
**Key Features:**
**Automated Banning:** Bans IPs that exhibit suspicious activity, like failed logins.

**Customizable Filters:** Users can define custom patterns for suspicious behavior.

**Multi-Service Protection:** Supports services like SSH, FTP, and web servers.

**Flexible Ban Durations:** Allows temporary or permanent bans.

**Email Alerts:** Notifies administrators when an IP is banned.

**Whitelist/Blacklist:** Permanently allows or blocks specific IPs.

**Firewall Compatibility:** Works with iptables, UFW, and more for flexibility across systems.

Fail2Ban’s ease of configuration and built-in defaults make it a versatile, effective security tool for protecting server access.

[Installation And Configuration](fail2ban_installation.md)


## 4. Uncomplicated Firewall (UFW)
UFW, short for Uncomplicated Firewall, is a user-friendly front-end for managing iptables, which is a powerful and complex firewall utility built into Linux. UFW is designed to simplify the process of configuring and managing firewall rules, making it more accessible for users who may not be familiar with the intricacies of iptables.

[](https://github.com/Karthikeyan-Appu/Ubuntu-Server-Config/assets/1_gc5l0IPPu3m7dhcJtqPbHg.png)

**Key Features:**

**Ease of Use:** UFW provides a simple command-line interface with straightforward commands to enable, disable, and configure firewall rules.

**Default Deny Policy:** By default, UFW is configured with a "deny all" policy for incoming connections, providing a secure baseline from which to build.

**Pre-configured Profiles:** Includes pre-configured application profiles for common services like SSH, HTTP, and HTTPS, making it easy to allow or deny traffic for these services.

**IPv4 and IPv6 Support:** Fully supports both IPv4 and IPv6, ensuring that it can be used in modern network environments.

**Logging:** Provides logging capabilities to monitor and review traffic that is being blocked or allowed by the firewall rules.

[Installation and Configuration](ufw_installation.md)


## 5, SNORT






