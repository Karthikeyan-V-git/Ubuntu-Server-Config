# Securing FTP Server with Fail2ban

Fail2ban is a tool that helps protect your server from brute-force attacks by monitoring log files and temporarily banning IPs that show suspicious behavior. This is especially useful for securing your FTP server.

## Step 1: Install Fail2ban

Install Fail2ban using the following command:
```
sudo apt install fail2ban
```
## Step 2: Configure Fail2ban
Create a local copy of the main configuration file for custom settings, Because if when an update on the packages of Fail2ban ocuurs it will overwrite the configuration files.

```
sudo cp /etc/fail2ban/jail.conf /etc/fail2ban/jail.local
```

Edit the jail.local file to configure Fail2ban:
```
sudo nano /etc/fail2ban/jail.local
```
In this file, you can configure global settings such as the ban time, find time, and max retry settings:

**bantime:** Duration for which an IP will be banned (e.g., 10m for 10 minutes).
**findtime:** Time window during which multiple failed login attempts must occur to trigger a ban (e.g., 10m).
**maxretry:** Number of failed login attempts allowed before an IP is banned.

```
#[DEFAULT]
bantime = 10m
findtime = 10m
maxretry = 5
```
## Step 3: Configure Fail2ban for VSFTPD
Add a specific jail configuration for vsftpd by adding the following section to your jail.local file:
```
[vsftpd]
enabled  = true
port     = ftp,ftp-data,ftps,ftps-data
logpath  = /var/log/vsftpd.log
maxretry = 3
```
**enabled:** Set to true to enable Fail2ban for VSFTPD.
**port:** Ports associated with FTP services.
**logpath:** Path to the VSFTPD log file (ensure this matches your VSFTPD log path).
**maxretry:** Number of allowed failed login attempts before banning an IP.

## Step 4: Configure Fail2Ban for SSH
Add a specific jail configuration for SSH by adding the following section to your jail.local file:
```
[sshd]
enable = true
port    = ssh
logpath = /var/log/auth.log
backend = %(sshd_backend)s
maxretry = 5
```

## Step 5: Restart Fail2Ban service and check status
```
sudo systemctl restart fail2ban
sudo fail2ban-client status
```

Unban an IP (Optional)
```
sudo fail2ban-client unban IP_ADDRESS
#Replace with an IP address
```
##Fail2ban is a versatile tool that can be configured to protect not only SSH and FTP but also other services vulnerable to brute-force attacks, such as Apache, Nginx, and Postfix. By checking the jail.conf or jail.local file, you can find preconfigured jails for a variety of services supported by Fail2ban. Simply enable the relevant jail and customize its settings to add an additional layer of security to those services as well.
