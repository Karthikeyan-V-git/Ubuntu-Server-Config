# SSH Server Configuration Guide

This guide provides steps to configure an SSH server on Ubuntu. The SSH configuration file is located at `/etc/ssh/sshd_config`. You can modify this file to adjust SSH settings such as the port, allowed authentication methods, and more.

## Editing SSH Configuration

Open the SSH configuration file using a text editor like `nano`:

    ```
    sudo nano /etc/ssh/sshd_config

# Make the below changes for secuirty measures

```
#Change the default port
Port 2222

#Disable root login for security purposes
PermitRootLogin no

#Limit the number of authentication attempts
MaxAuthTries 3

#Enable public key authentication
PubkeyAuthentication yes

#Allow password-based authentication
PasswordAuthentication yes

#Disallow empty passwords
PermitEmptyPasswords no

```
Save the file and restart the SSH service and make SSH start on booting

```
sudo systemctl daemon-reload
sudo systemctl restart ssh
sudo systemctl enable ssh
```
