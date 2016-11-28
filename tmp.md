
![](http://i.imgur.com/VrzlDHZ.jpg)
![](http://i.imgur.com/FBrDWD9.jpg)
![](http://i.imgur.com/s8y0JOO.jpg)
![](http://i.imgur.com/naidkh5.jpg)


- [vsftpd](https://security.appspot.com/vsftpd.html)
- [vsftpd_conf](http://vsftpd.beasts.org/vsftpd_conf.html)

~~~~
chown_uploads=YES
chown_username=whoever
anon_upload_enable=NO
~~~~

~~~~
# Access rights
anonymous_enable=YES
local_enable=NO
write_enable=NO
anon_upload_enable=NO
anon_mkdir_write_enable=NO
anon_other_write_enable=NO
# Security
anon_world_readable_only=YES
connect_from_port_20=YES
hide_ids=YES
pasv_min_port=50000
pasv_max_port=60000
# Features
xferlog_enable=YES
ls_recurse_enable=NO
ascii_download_enable=NO
async_abor_enable=YES
# Performance
one_process_model=YES
idle_session_timeout=120
data_connection_timeout=300
accept_timeout=60
connect_timeout=60
anon_max_rate=50000
~~~~

~~~~
# Standalone mode
listen=YES
max_clients=200
max_per_ip=4
# Access rights
anonymous_enable=YES
local_enable=NO
write_enable=NO
anon_upload_enable=NO
anon_mkdir_write_enable=NO
anon_other_write_enable=NO
# Security
anon_world_readable_only=YES
connect_from_port_20=YES
hide_ids=YES
pasv_min_port=50000
pasv_max_port=60000
# Features
xferlog_enable=YES
ls_recurse_enable=NO
ascii_download_enable=NO
async_abor_enable=YES
# Performance
one_process_model=YES
idle_session_timeout=120
data_connection_timeout=300
accept_timeout=60
connect_timeout=60
anon_max_rate=50000
~~~~

~~~~
anonymous_enable=NO
local_enable=YES
write_enable=NO
anon_upload_enable=NO
anon_mkdir_write_enable=NO
anon_other_write_enable=NO
chroot_local_user=YES
guest_enable=YES
guest_username=virtual
listen=YES
listen_port=10021
pasv_min_port=30000
pasv_max_port=30999
~~~~
