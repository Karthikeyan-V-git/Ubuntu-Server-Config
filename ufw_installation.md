# Securing Your Server with UFW (Uncomplicated Firewall)

UFW is a user-friendly command-line interface for managing firewall rules. It allows you to control incoming and outgoing traffic to secure your server against unauthorized access.

## Step 1: Install UFW (if not already installed)

On most Debian-based systems, UFW comes pre-installed. To install or ensure it’s updated, run:
```
sudo apt install ufw
```

## Step 2: Remove default settings
Resetting and customizing the default UFW settings is essential to ensure that your firewall rules match your specific security requirements and usage patterns. While the default settings offer a basic level of protection, they might not cover all your needs. Customizing UFW allows you to permit only necessary services and block everything else, enhancing security and performance according to your unique environment.
```
# Check the status of UFW, including the current rules and whether it is active or inactive.
sudo ufw status

# Disable UFW, turning off the firewall and allowing all traffic.
sudo ufw disable

# Reset UFW to its default state, removing all existing rules.
sudo ufw reset

# Deny all incoming connections by default, providing a basic level of security by blocking unsolicited access.
sudo ufw default deny incoming

# Allow all outgoing connections by default, ensuring that your system can communicate with external services.
sudo ufw default allow outgoing

# Stop the UFW service, which effectively disables the firewall.
sudo systemctl stop ufw

```

## Step 3: Adding custom rules

Format for adding 
```
sudo ufw allow <service> or <port_number>
```

```
# Allow incoming SSH connections to ensure remote management and access.
sudo ufw allow ssh

# Allow incoming connections for the VSFTPD service, enabling FTP access.
sudo ufw allow vsftpd

# Allow incoming connections from a specific IP address, enhancing security by restricting access to trusted sources.
sudo ufw allow from <IP_Address>
```

If you want to allow only a particular IP to access a particular service
```
# Allow incoming connections from a specific IP address to port 22 (SSH), ensuring that only the trusted IP can access SSH on your server.
sudo ufw allow from <IP_Address> to any port 22
```

## Step 4: Restart the service and enable on startup
```
sudo systemctl start ufw
sudo ufw enable
sudo ufw status
```
## Step 5: Delete any unwanted rules
```
sudo ufw status numbered
sudo ufw delete <no>
```





