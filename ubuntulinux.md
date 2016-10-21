![](https://d207aa93qlcgug.cloudfront.net/dockerized-0.23.1/img/explore_repos/official_ubuntu-h.png)

![](http://manpages.ubuntu.com/assets/light/images/footer_logo.png)

上次更新日期： 2016-08-23    

```console
shell> lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 14.04 LTS
Release:	14.04
Codename:	trusty
```

```console
shell> lsb_release -si
Ubuntu
```

---
/etc/update-manager/release-upgrades

```
New release '14.04.3 LTS' available.
Run 'do-release-upgrade' to upgrade to it.
```

```
#Prompt=lts
Prompt=never
```

```console
shell> sudo sed -i 's/Prompt=.*/Prompt=never/' /etc/update-manager/release-upgrades
shell> sudo rm /var/lib/update-notifier/release-upgrade-available
```

```console
shell> sudo sed -i '/^/s/^/#/" /etc/apt/sources.list
```

sed -i "/^deb cdrom:/s/^/#/" /etc/apt/sources.list



```console
shell> apt-get --version
shell> apt-get -o Acquire::ForceIPv4=true update  
```


apt.conf
```
Acquire::ForceIPv4 "true";


Acquire
{
  ForceIPv4 "true";
  Proxy "http://dockerhost:3142";
};

Acquire::http
{
  Proxy "http://dockerhost:3142";
};  
```


[apt.conf](http://manpages.ubuntu.com/manpages/raring/man5/apt.conf.5.html)
[apt-cacher-ng](https://docs.docker.com/engine/examples/apt-cacher-ng/)

Acquire::http::Timeout "10";
Acquire::ftp::Timeout "10";

---

```console
shell> /etc/network/interfaces
```
```
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
# iface eth0 inet dhcp
iface eth0 inet static
               address 192.168.1.3
               netmask 255.255.255.0
               gateway 192.168.1.1
               dns-nameservers 192.168.1.254 8.8.8.8
               dns-search foo.org bar.com
               post-up arp -f
```

```console
shell> vim /etc/ethers
```
```
90:94:e4:07:df:14 192.168.42.1
b8:27:eb:6e:88:a3 192.168.42.25
00:0c:29:b7:22:3c 192.168.42.31
00:0c:29:d1:41:b0 192.168.42.32
f0:b4:29:73:2d:05 192.168.42.56
00:10:18:03:92:7a 192.168.42.200
00:0e:38:5e:f3:c0 192.168.42.253
```

```console
shell> modprobe 8021q
shell> apt-get install vlan
shell> vconfig add eth0 222 # 222 vlan-id
shell> ifconfig eth0.222 up
shell> ifconfig eth0.222 192.168.2.3 netmask 255.255.255.0

shell> ip addr add 192.168.2.3/24 dev eth0.222
```

```console
shell> /etc/modules
```
```
8021q
```

```
auto eth0.222
iface eth0.222 inet static
            vlan-raw-device eth0
            address 192.168.2.3
            netmask 255.255.255.0
```

```console
shell> vconfig rem eth0.222
```

---

```console
shell> vim /etc/sysctl.conf
```

```ini
[...]
net.ipv6.conf.all.disable_ipv6 = 1
```

```console
shell> reboot
```

```console 
shell> vim /etc/default/grub
```

```ini
[...]
GRUB_CMDLINE_LINUX="ipv6.disable=1"
[...]
```

```console
shell> update-grub
shell> reboot
```

---


```console
shell> cat /proc/sys/fs/file-nr
shell> cat /proc/sys/fs/file-max

shell> cat /proc/sys/fs/inode-nr
```


---

**unattended-upgrades**

```console
shell> apt-get install unattended-upgrades
shell> dpkg-reconfigure unattended-upgrades  
```


### :books: 參考網站：
- [automatic-updates](https://help.ubuntu.com/lts/serverguide/automatic-updates.html)
- [dpkg-reconfigure](http://manpages.ubuntu.com/manpages/saucy/man8/dpkg-reconfigure.8.html)

---

```console
shell> apt-get install lvm2
shell> pvscan
```

---

![](http://i.imgur.com/ykaLJcH.png)

F6

![](http://i.imgur.com/BQAKJ1j.png)

ks=http://172.16.7.15/ks.cfg


```
#System language
lang en_US

#Language modules to install
langsupport en_US

#System keyboard
keyboard us

#System timezone
#timezone America/New_York
timezone Asia/Taipei

#Root password
rootpw --disabled

#Initial user (user with sudo capabilities) 
user ubuntu --fullname "Ubuntu User" --password root4me2

#Reboot after installation
reboot

#Use text mode install
text

#Install OS instead of upgrade
install

#Installation media
cdrom
#nfs --server=server.com --dir=/path/to/ubuntu/

#System bootloader configuration
bootloader --location=mbr 

#Clear the Master Boot Record
zerombr yes

#Partition clearing information
clearpart --all --initlabel 

#Basic disk partition
part / --fstype ext4 --size 1 --grow --asprimary 
part swap --size 1024 
part /boot --fstype ext4 --size 256 --asprimary 

#Advanced partition
#part /boot --fstype=ext4 --size=500 --asprimary
#part pv.aQcByA-UM0N-siuB-Y96L-rmd3-n6vz-NMo8Vr --grow --size=1
#volgroup vg_mygroup --pesize=4096 pv.aQcByA-UM0N-siuB-Y96L-rmd3-n6vz-NMo8Vr
#logvol / --fstype=ext4 --name=lv_root --vgname=vg_mygroup --grow --size=10240 --maxsize=20480
#logvol swap --name=lv_swap --vgname=vg_mygroup --grow --size=1024 --maxsize=8192

#System authorization infomation
auth  --useshadow  --enablemd5 

#Network information
network --bootproto=dhcp --device=eth0

#Firewall configuration
firewall --disabled --trust=eth0 --ssh 

#Do not configure the X Window System
skipx

user joe --fullname "Joe User" --password iamjoe
```


```
ks=cdrom:/ks.cfg
ks=floppy
ks=nfs:<server>:/<path>
ks=http://<server>/<path>
ks=floppy:/<path>
ks=cdrom:/<path>
```

- [ch04s06](https://help.ubuntu.com/lts/installation-guide/i386/ch04s06.html)
- [s1-kickstart2-startinginstall](https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/3/html/System_Administration_Guide/s1-kickstart2-startinginstall.html)





```
linux ks=floppy
```

- [Starting a Kickstart Installation](https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/3/html/System_Administration_Guide/s1-kickstart2-startinginstall.html)


### :books: 參考網站：
- [10.2. Changing Network Kernel Settings](https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/5/html/Tuning_and_Optimizing_Red_Hat_Enterprise_Linux_for_Oracle_9i_and_10g_Databases/sect-Oracle_9i_and_10g_Tuning_Guide-Adjusting_Network_Settings-Changing_Network_Kernel_Settings.html)

---

```console
shell> apt-get install lib32z1 lib32ncurses5 lib32bz2-1.0
```


```console
shell> uname -m
x86_64
```

```console
shell> debconf-set-selections
shell> debconf-get-selections
```

```
mysql-server-5.7	mysql-server/root_password	password	
mysql-server-5.7	mysql-server/root_password_again	password	
mysql-server-5.7	mysql-server/no_upgrade_when_using_ndb	error	
mysql-server-5.7	mysql-server-5.7/postrm_remove_databases	boolean	false
mysql-server-5.7	mysql-server-5.7/really_downgrade	boolean	false
mysql-server-5.7	mysql-server/password_mismatch	error	
mysql-server-5.7	mysql-server-5.7/nis_warning	note	
mysql-server-5.7	mysql-server-5.7/start_on_boot	boolean	true
```


### :books: 參考網站：
- [Official Ubuntu Documentation](https://help.ubuntu.com/)
- [vlan-interfaces](http://manpages.ubuntu.com/manpages/intrepid/man5/vlan-interfaces.5.html)

- [Setting File Handles](https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/5/html/Tuning_and_Optimizing_Red_Hat_Enterprise_Linux_for_Oracle_9i_and_10g_Databases/chap-Oracle_9i_and_10g_Tuning_Guide-Setting_File_Handles.html)
