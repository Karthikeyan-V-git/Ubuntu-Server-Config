# Setting Up FTP Server with VSFTPD and SSL

This guide will help you set up a secure **FTP server** using **vsftpd** with SSL encryption.

## Step 1: Install VSFTPD

Install the VSFTPD package using the following command:

```
sudo apt install vsftpd
```

## Step 2: Create FTP User and Directories
```
#Create a new user (ftpuser) for the FTP service:

sudo adduser ftpuser

#Provide any required details asked 
```

### Provide necessary permissions for the directories
```
# Create the main directory for the FTP user
mkdir /home/ftpuser/ftp

# Change ownership of the directory to 'nobody' and 'nogroup' to restrict access
chown nobody:nogroup /home/ftpuser/ftp

# Remove write permissions from the main FTP directory for everyone for security reasons
chmod a-w /home/ftpuser/ftp

# Create an 'uploads' subdirectory inside the FTP user's directory for file uploads
mkdir /home/ftpuser/ftp/uploads

# Change ownership of the 'uploads' directory to the 'ftpuser' for read/write access
chown ftpuser:ftpuser /home/ftpuser/ftp/uploads
```

## Step 3 : Generate SSL certificate for secure connection 
```
sudo openssl req -x509 -nodes -days 3650 -newkey rsa:2048 -keyout /etc/ssl/certs/vsftpd.crt -out /etc/ssl/private/vsftpd.key
# Note down the path 
```
## Step 4 : Add the user to the ftpusers list
```
echo "ftpuser" | sudo tee -a /etc/vsftpd.userlist
```

## Step 5: Configure VSFTPD

**Edit the VSFTPD configuration file:**
```
sudo nano /etc/vsftpd.conf
```
**Make the below changes for secuirty**
```
# Disable anonymous FTP access.
anonymous_enable=NO

# Allow local users to log in.
local_enable=YES

# Enable write access for local users.
write_enable=YES

# Chroot local users to their home directories.
chroot_local_user=YES

# Specify SSL certificate and private key.
rsa_cert_file=/etc/ssl/certs/vsftpd.crt
rsa_private_key_file=/etc/ssl/private/vsftpd.key
ssl_enable=YES

# Set the local root directory for the FTP user.
user_sub_token=$USER
local_root=/home/$USER/ftp

# Enable user list for access control.
userlist_enable=YES
userlist_file=/etc/vsftpd.userlist
userlist_deny=NO

# Force SSL encryption for data and login.
allow_anon_ssl=no
force_local_data_ssl=YES
force_local_logins_ssl=YES
```

## Step 5: Restart VSFTPD Service
```
sudo systemctl daemon-reload
sudo systemctl restart vsftpd
sudo systemctl enable vsftpd
```

## Step 6: Connect to FTP Server
You can now use an FTP client like FileZilla or lftp to connect to your server. Here are the connection details:

**Host:** [Your Server IP Address]
**Username:** ftpuser
**Password:** [Password for ftpuser]
**Port: 21** (Standard FTP port)
Make sure to select the SSL/TLS option for secure connection during the setup in your FTP client.


## Conclusion

By following the steps outlined above, you have successfully set up a secure FTP server using **vsftpd** with SSL encryption. The FTP server is configured to allow secure file transfers, while restricting access to local users and ensuring their data is encrypted during transmission.

**Key security measures were taken, such as:**
**- Disabling anonymous access to prevent unauthorized users from connecting.**
**- Restricting FTP write access to the necessary directories.**
**- Configuring SSL encryption to secure the communication between the FTP server and clients.**

Your FTP server is now ready for use, and you can connect to it using FTP clients like **FileZilla** or **lftp**, ensuring that your files are transferred securely.

Remember to regularly review and update your configuration for enhanced security, and monitor the server logs to detect any potential issues.

