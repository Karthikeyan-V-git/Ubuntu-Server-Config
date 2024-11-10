# SSH Server Configuration Guide

This guide provides steps to configure an SSH server on Ubuntu. The SSH configuration file is located at `/etc/ssh/sshd_config`. You can modify this file to adjust SSH settings such as the port, allowed authentication methods, and more.

## Editing SSH Configuration

Open the SSH configuration file using a text editor like `nano`:

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

# Generating SSH Keys ( Client )
To use public key authentication, generate an SSH key pair on the client computer:

```ssh-keygen -t rsa -b 4096 -C "any_name_to_identity"
```
This command generates a new RSA key pair with a length of 4096 bits. Follow the prompts to save the keys to the default location **(~/.ssh/id_rsa)**.

## Copying the Public Key to the Server
Copy the generated public key to the server using ssh-copy-id. This will add your public key to the **~/.ssh/authorized_keys** file on the server, allowing you to log in without a password.

```
ssh-copy-id -i ~/.ssh/id_rsa.pub username@server_ip -p <port_no>
```
Alternatively, you can manually copy the public key to the server:
```
echo "your_copied_public_key" >> ~/.ssh/authorized_keys
chmod 600 ~/.ssh/authorized_keys
```

## Connecting to the Server
To connect to the SSH server from the client using the newly configured settings, use the following command:
```
ssh -p 2222 your_username@your_server_ip
#Replace your_username and your_server_ip with your actual username and server IP address.
```






































