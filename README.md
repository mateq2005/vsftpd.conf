# vsFTPd

### Step 1 — Installing vsftpd

```
sudo apt update
sudo apt install vsftpd
sudo cp /etc/vsftpd.conf /etc/vsftpd.conf.orig
```

### Step 2 — Opening the Firewall

```
sudo ufw status
sudo ufw allow 20,21,990/tcp
sudo ufw allow 40000:50000/tcp
sudo ufw status
```

### Step 3 — Preparing the User Directory

```
sudo mkdir /srv/ftp/directory_name
sudo chown -R nobody:nogroup /srv/ftp/directory_name
sudo chmod -R 755 /srv/ftp/directory_name
echo "Hello!" > /srv/ftp/directory_name/message
```

### Step 4 — Configuring FTP Access

```
sudo nano /etc/vsftpd.conf
```

```
# Allow anonymous FTP? (Disabled by default).
anonymous_enable=YES
#
# Uncomment this to allow local users to log in.
local_enable=NO
. . .
write_enable=NO
. . .
ftpd_banner=Welcome to blah FTP service.
. . .
chroot_local_user=NO
```

```
sudo systemctl restart vsftpd
```

**ftp://your_server_ip**


