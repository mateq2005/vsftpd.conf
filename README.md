# vsFTPd

### Installing vsftpd

```
sudo apt-get update
sudo apt-get install vsftpd -y
```

```
systemctl start vsftpd
systemctl enable vsftpd
systemctl status vsftpd
```

```
sudo cp /etc/vsftpd.conf /etc/vsftpd.conf.orig
```

### Preparing the User Directory

```
sudo mkdir /srv/ftp/directory_name
sudo chown -R nobody:nogroup /srv/ftp/directory_name
sudo chmod -R 755 /srv/ftp/directory_name
echo "Hello!" > /srv/ftp/directory_name/message
```

### Configuring FTP Access

```
sudo nano /etc/vsftpd.conf
```

**Banner**
```
ftpd_banner= Welcome to vsftpd.service
```

### Anonymous Connection
```
anonymous_enable=YES
write_enable=YES
anon_upload_enable=YES
anon_mkdir_write_enable=YES
anon_root=/srv/ftp
anon_other_write_enable=YES
```

```
sudo mkdir /srv/ftp/anonymous
sudo chown -R nobody:nogroup /srv/ftp/anonymous
sudo chmod -R 755 /srv/ftp/anonymous
```

### Users' Isolation
```
chroot_local_user=YES
chroot_list_enable=NO
allow_writeable_chroot=YES
```

### Specific User's Isolation
```
chroot_local_user=NO
chroot_list_enable=YES allow_writeable_chroot=YES
chroot_list_file=/etc/vsftpd.chroot_list
```
• add isolated user to *vsftpd.chroot_list*

### Specific User's not isolating
```
chroot_local_user=YES
chroot_list_enable=NO
allow_writeable_chroot=YES
chroot_list_file=/etc/vsftpd.chroot_list
```
• add isolated user to *vsftpd.chroot_list*

### Restarting vsftpd

```
sudo systemctl restart vsftpd
```

**ftp://your_server_ip**

