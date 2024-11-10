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
    sudo apt install nano wget curl net-tools 
    
