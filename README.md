# Ubuntu Server Configuration 
This repository documents the setup and configuration of an Ubuntu Server for hosting web applications. The project includes detailed instructions and best practices to create a secure and efficient server environment.

## Prerequisites
- Ubuntu Server 20.04 or later
    https://ubuntu.com/download/server#release-notes-lts
- Use any tools like Ventoy / Power ISO / Linux Inbuilt service for creating a USB bootable device.
- AFter completion boot into the bootable device through bootmenu / changing the boot priority
- Go through basic installation procedure [ Language / Internet Access / Server name / User name and Password (Make sure to note these credentials ).
- Choose "Entire Disk Option" - Storage allocation
- Select Install "Open SSH" - for secure remote acesss.
- Wait for the completion and reboot the system alongwith removing the bootable device.
- You will be directed to CLI of the server login.

Note : I am using the Minimal Version for installation.


## Installation Instructions
1. Update and upgrade the package list:
   ```bash
   sudo apt update && sudo apt upgrade
2. 
