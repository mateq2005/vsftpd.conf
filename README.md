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

**Banner**
```
ftpd_banner= Welcome to vsftpd.service
```

**Anonymous Connection**
```
anonymous_enable=YES
write_enable=YES
anon_upload_enable=YES
anon_mkdir_write_enable=YES
anon_root=/srv/ftp
```

**Users' Isolation**
```
chroot_local_user=YES
chroot_list_enable=NO
allow_writeable_chroot=YES
```

**Specific User's Isolation**
```
chroot_local_user=NO
chroot_list_enable=YES allow_writeable_chroot=YES
chroot_list_file=/etc/vsftpd.chroot_list
```
• add isolated user to *vsftpd.chroot_list*

**Specific User's not isolating**
```
chroot_local_user=YES
chroot_list_enable=NO
allow_writeable_chroot=YES
chroot_list_file=/etc/vsftpd.chroot_list
```
• add isolated user to *vsftpd.chroot_list*

**Restarting vsftpd**
```
sudo systemctl restart vsftpd
```

**ftp://your_server_ip**


