# Table of Contents

<a name="table-of-contents"></a>

- [dig - DNS lookup utility](#dig)
- [named-checkzone](#named-checkzone)
- [freebcp](#freebcp) 
- [tsql](#tsql)
- [gpg](#gpg)
- [export](#export)
- [recode](#recode) 
- [iconv](#iconv)
- [convmv](#convmv) 
- [crontab](#crontab)
- [date](#date)
- [dd](#dd)
- [dmidecode](#dmidecode)
- [lsb_release](#lsb_release)
- [ldd - print shared library dependencies](#ldd)
- [geoip](#geoip)
- [grep](#grep)
- [sed](#sed)
- [perl](#perl)
- [redir - Redirect TCP connections](#redir)
- [fuser](#fuser)
- [strace](#strace)
- [netmask](#netmask)
- [sipcalc](#sipcalc)  
- [lsof](#lsof)
- [sysctl](#sysctl)
- [rsync](#rsync)
- [arping](#arping)
- [ping](#ping)
- [hping3](#hping3)
- [mtr](#mtr)
- [wakeonlan](#wakeonlan)
- [ssh](#ssh)
- [ssh-copy-id](#ssh-copy-id)
- [plink](#plink)
- [seq](#seq)
- [arpspoof](#arpspoof)
- [arptables](#arptables)
- [aria2](#aria2)
- [curl](#curl)
- [wget](#wget)
- [w3m](#w3m)
- [dpkg-reconfigure](#dpkg-reconfigure)
- [loco](#loco)
- [most](#most)
- [ifstat - InterFace STATistics Monitoring](#ifstat)
- [ip - show / manipulate routing, devices, policy routing and tunnels](#ip)
- [ifconfig - configure a network interface](#ifconfig)
- [route](#route)
- [netstat](#netstat)
- [ethtool - query or control network driver and hardware settings](#ethtool)
- [ss - another utility to investigate sockets](#ss) 
- [curlftpfs](#curlftpfs)
- [lsmod - Show the status of modules in the Linux Kernel](#lsmod)
- [modinfo - Show information about a Linux Kernel module](#lsmod)
- [modprobe - Add and remove modules from the Linux Kernel](#lsmod)
- [fio - flexible I/O tester](#fio)
- [systemctl - Control the systemd system and service manager](#systemctl)
- [qpdf](#qpdf)

---
- [pv - Shell pipeline element to meter data passing through](#pv)
- [dialog - Displays user-friendly dialog boxes from shell scripts](#dialog)
- [md5sum - compute and check MD5 message digest](#md5sum)
- [sha1sum - compute and check SHA1 message digest](#sha1sum)
- [sha256sum - compute and check SHA256 message digest](#sha256sum)
- [mencoder - MPlayer's Movie Encoder](#mencoder)
- [imagemagick - image manipulation programs -- binaries](#imagemagick)
- [nikto - Scan web server for known vulnerabilities](#nikto)
- [iotop - simple top-like I/O monitor](#iotop)
- [dmitry - Deepmagic Information Gathering Tool](#dmitry)

---

- [bash-completion](#bash-completion)
- [tcptrack](#tcptrack)

---

- [yum](https://www.centos.org/docs/5/html/yum/sn-managing-packages.html)
- [tools](http://tools.kali.org/tools-listing)


---

<a name="bash-completion"></a>

```console
shell> brew install bash-completion
```

---

<a name="tcptrack"></a>

```console
shell> brew install tcptrack
shell> sudo tcptrack -d -r5 -i en0 port 80 
```

---

**ioping - Simple disk I/O latency measuring tool**

```console
shell> brew install ioping
shell> ioping -c 10 .
```

---

<a name="qpdf"></a>

```console
shell> brew install qpdf
shell> qpdf --show-encryption --password=password
shell> qpdf --decrypt --password=password
```

**[⬆ Back to Top](#table-of-contents)**

---
**tree - displays an indented directory tree, in color**

```console
shell> apt-get install tree
shell> yum install tree -y
shell> brew install tree
shell> tree
```
**[⬆ Back to Top](#table-of-contents)**

---
**oathtool - OATH one-time password tool**

**[⬆ Back to Top](#table-of-contents)**

---

**logrotate ‐ rotates, compresses, and mails system logs**

```console
shell> logrotate -f /etc/logrotate.conf
```

logrotate.conf

```
/var/log/ifstat.log {
    daily
    dateext
    missingok
    rotate 5
    compress
    delaycompress 
    notifempty
    copytruncate
}
```

**[⬆ Back to Top](#table-of-contents)**

---

**ifstat - InterFace STATistics Monitoring**<a name="ifstat"></a>

```console
shell> apt-get install ifstat
shell> ifstat -a
shell> ifstat -i eth0 -b -t
```

```console
shell> brew install oath-toolkit
shell> oathtool --totp -b WQSWOTKQK6YQEY4E
```
**[⬆ Back to Top](#table-of-contents)**

---

**dphys-swapfile - Autogenerate and use a swap file**

```console
shell> apt-get install dphys-swapfile
shell> service dphys-swapfile start
```

`/var/swap`

`/etc/dphys-swapfile`

```
CONF_SWAPFILE=/var/swap
CONF_SWAPSIZE=100
```

**[⬆ Back to Top](#table-of-contents)**

---

**fallocate - preallocate space to a file**

```console
shell> fallocate -l 100M /var/swap
```

```console
shell> swapon -s
shell> fallocate -l 100M /var/swap
shell> chmod 0600 /var/swap
shell> mkswap /var/swap
shell> swapon /var/swap
```

/etc/fstab

```
/var/swap       none            swap    sw                              0 0
```

```console
shell> swapoff /var/swap
```
```console
shell> swapoff -a
```

- /usr/share/doc/util-linux/examples/fstab.example2

**[⬆ Back to Top](#table-of-contents)**

---

**grive - Google Drive client for GNU/Linux**

```console
shell> apt-get install grive
```

**[⬆ Back to Top](#table-of-contents)**

---

**lnav - ncurses-based log file viewer**
```console
shell> apt-get install lnav
shell> lnav
shell> lnav syslog.5.gz
```
**[⬆ Back to Top](#table-of-contents)**

---

**vnstat - console-based network traffic monitor**
```console
shell> apt-get install vnstat
shell> netload eth0
```

`$HOME/.netloadrc`

**[⬆ Back to Top](#table-of-contents)**

---
**rename - renames multiple files**

```console
shell> brew install rename
shell> rename 's/\.bak$//' *.bak
shell> rename 'y/A-Z/a-z/' *

shell> rename IMG img *.jpg
shell> rename .html .htm *.html

shell> rename 's/$/.sh/' filename
shell> rename 's/$/.bak/' filename
```

### :books: 參考網站：
- [rename](http://manpages.ubuntu.com/manpages/xenial/man1/rename.ul.1.html)

**[⬆ Back to Top](#table-of-contents)**

---
**netdiag - Net-Diagnostics (trafshow,netwatch,statnet,tcpspray,tcpblast)**
**netload - Network device load monitor**

```console
shell> apt-get install netdiag
shell> netload eth0
```
**[⬆ Back to Top](#table-of-contents)**

---
**iftop - displays bandwidth usage information on an network interface**

```console
shell> apt-get install iftop
shell> iftop -n
```

**[⬆ Back to Top](#table-of-contents)**

---

**iptraf-ng - Next Generation Interactive Colorful IP LAN Monitor**
**iptraf - Interactive Colorful IP LAN Monitor**

```console
shell> apt-get install iptraf
shell> apt-get install iptraf-ng
shell> iptraf-ng
```

### :books: 參考網站：
- [iptraf](http://manpages.ubuntu.com/manpages/precise/man8/iptraf.8.html)

**[⬆ Back to Top](#table-of-contents)**

---
**speedometer - measure and display the rate of data across a network connection**

```console
shell> apt-get install speedometer
shell> speedometer -r eth0 -t eth0
shell> speedometer -r wlan0 -t wlan0
shell> speedometer -rx eth0
```

### :books: 參考網站：
- [speedometer](http://manpages.ubuntu.com/manpages/wily/man1/speedometer.1.html)

**[⬆ Back to Top](#table-of-contents)**

---

**tar - an archiving utility**

```console
shell> tar cvf file.tar directory
shell> tar xvf file.tar

shell> tar zcvf file.tar.gz directory
shell> tar zxvf file.tar.gz

shell> tar jxvf file.tar.bz

shell> tar Jcvf file.tar.xz directory
shell> tar Jxvf file.tar.xz

shell> tar Zxvf file.tar.Z directory
shell> tar Zxvf file.tar.Z

```

```
file.tar.gz
file.tgz
file.tar.bz
```

**[⬆ Back to Top](#table-of-contents)**

---
**gzip -- compression/decompression tool using Lempel-Ziv coding (LZ77)**

```console
shell> gzip file1
shell> gzip -d file1.gz
shell> gunzip file1.gz
shell> zcat file.Z
shell> uncompress file.Z
```

**[⬆ Back to Top](#table-of-contents)**

---

```console
shell> bzip2 --help
shell> bzip2 -z filename
shell> bzip2 -d filename.bz
shell> bunzip2 filename.bz
```

```
filename.bz2
filename.tbz2
filename.bz
filename.tbz
```

**[⬆ Back to Top](#table-of-contents)**

---

```console
shell> xz --help
shell> xz -z filename
shell> xz -d filename.xz
```
**[⬆ Back to Top](#table-of-contents)**

---
**p7zip - 7z file archiver with high compression ratio**

```console
shell> brew install p7zip
shell> apt-get install p7zip-full
shell> 7z a filename.7z filename
shell> 7z a filename.7z filename -pPassword
shell> 7z x filename.7z
shell> tar cf - directory | 7z a -si directory.tar.7z
shell> 7z x -so directory.tar.7z | tar xf -
```

**[⬆ Back to Top](#table-of-contents)**

---
**rarcrack - Password cracker for rar archives**
**unrar-free - Unarchiver for .rar files**

```console
shell> brew install unrar
shell> apt-get install unrar-free
shell> unrar --help
shell> unrar -x rar_file
```

**[⬆ Back to Top](#table-of-contents)**

---

**pwgen 密碼產生器**

```console
shell> brew install pwgen
shell> apt-get install pwgen
shell> pwgen
shell> pwgen --capitalize --symbols --ambiguous --num-passwords=1
```

**[⬆ Back to Top](#table-of-contents)**

---

```console
shell> brew install lftp
shell> apt-get install lftp
shell> lftp -u h2s,"NMG)h6" 192.168.168.188
shell> lftp -u h2s,"NMG)h6" 192.168.168.188 -e "cd ; put ; bye"
```

`/etc/lftp.conf`
`~/.lftprc`
`~/.lftp/rc`

**[⬆ Back to Top](#table-of-contents)**

---

```console
shell> yes
```

**[⬆ Back to Top](#table-of-contents)**

---

```console
shell> echo HelloWorld | rev

dlroWolleH
```

**[⬆ Back to Top](#table-of-contents)**

---
**inxi - full featured system information script**

```console
shell> apt-get install inxi
shell> inxi
shell> inxi -F
shell> inxi -M
shell> inxi -G
shell> inxi -N
shell> inxi -r
shell> inxi -D -c 3
```

**[⬆ Back to Top](#table-of-contents)**

---
**funny-manpages - more funny manpages**

```console
shell> apt-get install funny-manpages
```

```
/usr/share/figlet
```

**[⬆ Back to Top](#table-of-contents)**

---
**redir - Redirect TCP connections**

```console
shell> apt-get install redir
shell> redir --lport=22960 --caddr=10.192.28.72 --cport=22 &
```
**[⬆ Back to Top](#table-of-contents)**

---
```console
shell> apt-get install python-software-properties software-properties-common -y
shell> add-apt-repository 
```

**[⬆ Back to Top](#table-of-contents)**

---

```console
shell> apt-get install unattended-upgrades -y
shell> dpkg-reconfigure unattended-upgrades  
```

**[⬆ Back to Top](#table-of-contents)**

---

```console
shell> apt-get install ntpdate
shell> ntpdate -u time.apple.com
shell> ntpdate -u time.asia.apple.com
shell> ntpdate -u time.euro.apple.com
shell> ntpdate -u ntp.ubuntu.com
```
**[⬆ Back to Top](#table-of-contents)**

---
**tasksel - a user interface for installing tasks**

```console
shell> tasksel
shell> tasksel install
shell> tasksel remove
```
**[⬆ Back to Top](#table-of-contents)**

---
**sitecopy - program for managing a WWW site via FTP, SFTP, DAV or HTTP**

```console
shell> apt-get install sitecopy
```
**[⬆ Back to Top](#table-of-contents)**

---

```console
insserv
update-rc.d
```

**[⬆ Back to Top](#table-of-contents)**

---
**netdiscover - active/passive network address scanner using arp requests**

```console
shell> apt-get install netdiscover
shell> netdiscover -r 192.168.42.0/24 -i eth0
```

**arp-scan - arp scanning and fingerprinting tool**
```console
shell> apt-get install arp-scan
shell> arp-scan 192.168.42.0/24
```

**[⬆ Back to Top](#table-of-contents)**

---

**bleachbit - delete unnecessary files from the system**

**[⬆ Back to Top](#table-of-contents)**

---

**avahi-utils - Avahi browsing, publishing and discovery utilities**
**avahi-daemon - Avahi mDNS/DNS-SD daemon**

```console
shell> apt-get install avahi-utils
shell> avahi-browse --help
shell> avahi-browse -a
shell> avahi-browse -al

shell> avahi-browse -rt _workstation._tcp 
shell> avahi-browse -rt _http._tcp
```

`_http._tcp`

```console
shell> apt-get install avahi-daemon
```

`/etc/avahi/avahi-daemon.conf`

```conf
[server]
host-name=foo
domain-name=local
use-ipv4=yes
use-ipv6=yes
```

`/usr/share/doc/avahi-daemon/examples`

`/etc/avahi/services`

```xml
<?xml version="1.0" standalone='no'?><!--*-nxml-*-->
<!DOCTYPE service-group SYSTEM "avahi-service.dtd">

<service-group>

  <name replace-wildcards="yes">%h</name>

  <service>
    <type>_ssh._tcp</type>
    <port>22</port>
  </service>

</service-group>
```

### :books: 參考網站：
- [avahi.service](http://manpages.ubuntu.com/manpages/precise/man5/avahi.service.5.html)
- [avahi-daemon](http://manpages.ubuntu.com/manpages/precise/man8/avahi-daemon.8.html)
- [avahi-browse](http://manpages.ubuntu.com/manpages/precise/man1/avahi-browse.1.html)

**[⬆ Back to Top](#table-of-contents)**

---

```console
shell> truncate -s 0 testfile.txt 
shell> truncate --size=0 testfile.txt     
```

```console
shell> du -h --max-depth=1 | sort -n -r
```

**[⬆ Back to Top](#table-of-contents)**

---

**ifconfig - configure a network interface**

<a name="ifconfig"></a>

```console
shell> ifconfig eth0 | grep -Eo 'inet (addr:)?([0-9]*\.){3}[0-9]*' | grep -Eo '([0-9]*\.){3}[0-9]*'  
```

**[⬆ Back to Top](#table-of-contents)**

---

```console
shell> iostat -x 2
shell> blkid

shell> btdownloadcurses ubuntu-8.10-server-i386.iso.torrent

shell> vmstat
```

**[⬆ Back to Top](#table-of-contents)**

---

```console
shell> smbmount //{servicename}/mysharename /mymountpoint -o iocharset=utf8,user={username},password={password}
```

```console
shell> sudo apt-get install cifs-utils
shell> sudo mkdir /mnt/mountpoint
shell> sudo mount -t cifs //servicename/mysharename /mnt/mountpoint -o vers=3.0,user=myaccountname,password=StorageAccountKeyEndingIn==,dir_mode=0777,file_mode=0777
```

`/etc/fstab`
```
//servicename/mysharename /mymountpoint cifs vers=3.0,username= myaccountname,password= StorageAccountKeyEndingIn==,dir_mode=0777,file_mode=0777
```

### :books: 參考網站：
- [如何搭配使用 Azure 檔案儲存體與 Linux](https://azure.microsoft.com/zh-tw/documentation/articles/storage-how-to-use-files-linux/)

**[⬆ Back to Top](#table-of-contents)**

---
**cowsay/cowthink - configurable speaking/thinking cow (and a bit more)**

<a name="cowsay"></a>

```console
shell> apt-get install cowsay
```

**figlet - Make large character ASCII banners out of ordinary text**
<a name="figlet"></a>

```console
shell> apt-get install figlet
```

**[⬆ Back to Top](#table-of-contents)**

---

**systemctl - Control the systemd system and service manager**<a name="systemctl"></a>

```console
shell> systemctl
shell> systemctl list-units

shell> systemctl list-units --type=service

shell> systemctl enable nginx.service
shell> systemctl disable nginx.service

shell> systemctl start nginx.service
shell> systemctl stop nginx.service
shell> systemctl status nginx.service   
```

**[⬆ Back to Top](#table-of-contents)**

---

**pstree - display a tree of processes**

```console
shell> pstree -a
```

**[⬆ Back to Top](#table-of-contents)**

---

**hostname - show or set the system's host name**<a name="hostname"></a>

```console
shell> hostname -a
```

**[⬆ Back to Top](#table-of-contents)**

---

**fio - flexible I/O tester**<a name="fio"></a>

```console
shell> apt-get install fio
shell> fio --name=str --direct=1 --readwrite=randwrite --bs=4k --size=1G --numjobs=16 --runtime=180 --group_reporting --refill_buffers --ioengine=libaio --iodepth=16 

shell> fio --name=str --direct=1 --readwrite=randwrite --bs=4k --size=10M --numjobs=16 --runtime=180 --group_reporting --refill_buffers --ioengine=libaio --iodepth=16 

shell> fio --name=str --direct=1 --readwrite=randread --bs=4k --size=10M --numjobs=16 --runtime=180 --group_reporting --refill_buffers --ioengine=libaio --iodepth=16 
```

**[⬆ Back to Top](#table-of-contents)**

---
**lsmod - Show the status of modules in the Linux Kernel**
**modinfo - Show information about a Linux Kernel module**
**modprobe - Add and remove modules from the Linux Kernel**

<a name="lsmod"></a>
```console
shell> lsmod
shell> modinfo modulename

shell> modprobe nf_conntrack_ftp
shell> modprobe nf_conntrack_pptp
shell> modprobe nf_nat_pptp
```

**[⬆ Back to Top](#table-of-contents)**

---
**netstat - Print network connections, routing tables, interface statistics, masquerade connections, and multicast memberships**<a name="netstat"></a>

```console
shell> netstat -nr
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
0.0.0.0         192.168.42.1    0.0.0.0         UG        0 0          0 eth0
192.168.42.0    0.0.0.0         255.255.255.0   U         0 0          0 eth0

shell> netstat -na
shell> netstat -ntlp
```

**[⬆ Back to Top](#table-of-contents)**

---
**ss - another utility to investigate sockets**<a name="ss"></a>

```console
Display all TCP sockets.
shell> ss -t -a

Display all UDP sockets.
shell> ss -u -a

shell> ss -t -a -n

Display all established ssh connections.
shell> ss -o state established '( dport = :ssh or sport = :ssh )'
```

**[⬆ Back to Top](#table-of-contents)**

---

**sysctl - configure kernel parameters at runtime**<a name="sysctl"></a>

```console
shell> sysctl -w fs.file-max=65536
shell> sysctl -w net.ipv6.conf.all.disable_ipv6=1
shell> sysctl --system
```

### :books: 參考網站：
- [tuning-os](https://docs.oracle.com/cd/E26576_01/doc.312/e24936/tuning-os.htm#GSPTG00007)
- [8.2. Optimized Network Settings](https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/6/html/Performance_Tuning_Guide/s-network-dont-adjust-defaults.html)

**[⬆ Back to Top](#table-of-contents)**

---

**mtr - a network diagnostic tool**<a name="mtr"></a>
**traceroute - print the route packets trace to network host**

```console
shell> apt-get install mtr
shell> apt-get install mtr-tiny
shell> mtr ip-addr
shell> mtr -rw 8.8.8.8
Start: Wed Nov  4 15:49:29 2015
HOST: raspberrypi                      Loss%   Snt   Last   Avg  Best  Wrst StDev
  1.|-- 192.168.42.1                      0.0%    10    0.8   0.8   0.7   1.0   0.0
  2.|-- h254.s98.ts.hinet.net             0.0%    10   16.1  16.1  16.0  16.3   0.0
  3.|-- snuh-3301.hinet.net               0.0%    10   16.3  18.6  16.1  32.1   5.2
  4.|-- SNUH-3202.hinet.net               0.0%    10   16.3  16.2  16.0  16.4   0.0
  5.|-- tyfo-3012.hinet.net               0.0%    10   21.1  22.1  18.1  24.8   2.0
  6.|-- 220-128-9-173.HINET-IP.hinet.net  0.0%    10   17.5  17.5  17.2  17.6   0.0
  7.|-- 74.125.49.158                     0.0%    10   22.4  22.3  22.1  22.4   0.0
  8.|-- 72.14.233.20                      0.0%    10   24.1  26.1  24.1  39.4   4.8
  9.|-- 209.85.252.213                    0.0%    10   21.2  21.4  20.9  23.5   0.7
 10.|-- 209.85.249.75                     0.0%    10   21.0  20.9  20.7  21.1   0.0
 11.|-- ???                              100.0    10    0.0   0.0   0.0   0.0   0.0
 12.|-- google-public-dns-a.google.com    0.0%    10   25.3  25.4  25.2  25.6   0.0

shell> mtr -rw --no-dns 8.8.8.8
Start: Wed Nov  4 15:51:49 2015
HOST: raspberrypi    Loss%   Snt   Last   Avg  Best  Wrst StDev
  1.|-- 192.168.42.1    0.0%    10    0.9   0.8   0.7   0.9   0.0
  2.|-- 168.95.98.254   0.0%    10   16.4  16.2  16.0  16.6   0.0
  3.|-- 168.95.24.78    0.0%    10   16.2  18.9  16.0  43.8   8.7
  4.|-- 220.128.5.226   0.0%    10   16.1  22.0  16.1  46.2  10.6
  5.|-- 220.128.9.106   0.0%    10   17.7  20.3  17.7  24.2   2.3
  6.|-- 220.128.9.173   0.0%    10   17.4  17.6  17.2  18.4   0.0
  7.|-- 74.125.49.158   0.0%    10   22.0  22.3  22.0  22.4   0.0
  8.|-- 72.14.233.20    0.0%    10   24.3  25.8  24.1  36.4   3.8
  9.|-- 209.85.252.213  0.0%    10   37.3  42.1  27.8  56.5   7.4
 10.|-- 209.85.249.75   0.0%    10   26.1  28.6  23.3  47.9   7.0
 11.|-- ???            100.0    10    0.0   0.0   0.0   0.0   0.0
 12.|-- 8.8.8.8         0.0%    10   25.3  25.4  25.2  25.6   0.0

```

```console
shell> traceroute 8.8.8.8
shell> traceroute -n 8.8.8.8
```

**[⬆ Back to Top](#table-of-contents)**

---
<a name="ping"></a>
```console
shell> ping -c 3 -W 10 ubuntu.com
shell> ping -n -c 3 -M do -s 1500 ip-addr
```

```console
shell> ping6 -I eth0 fe80::20c:29ff:fed1:41b0
shell> ping6 ::1
shell> ping6 -I eth0 FF02::1
```

**[⬆ Back to Top](#table-of-contents)**

---
<a name="perl"></a>

```console
shell> perl -pi -e 's/regexp/replacement/g' input-file
shell> perl -e 'print "Hello World\n"'
```

**[⬆ Back to Top](#table-of-contents)**

---
<a name="route"></a>

```console
shell> route add ip-addr gw 127.0.0.1 lo
shell> route add -host ip-addr reject
shell> route del ip-addr
shell> route del -host ip-addr reject
```

**[⬆ Back to Top](#table-of-contents)**

---
<a name="named-checkzone"></a>

```console
shell> named-checkzone example.com /etc/bind/db.example.com
```
### :books: 參考網站：
- [named-checkzone](http://manpages.ubuntu.com/manpages/xenial/en/man8/named-checkzone.8.html)

**[⬆ Back to Top](#table-of-contents)**

---
<a name="sed"></a>
**sed - stream editor for filtering and transforming text**
```console
shell> sed 's/regexp/replacement/g' input-file
shell> sed -i 's/regexp/replacement/g' input-file
shell> sed -n '5,10p' input-file

shell> sed -i -e 's/regexp/replacement/g' -e 's/str/newstr/' -e '/re/d' input-file
```

**[⬆ Back to Top](#table-of-contents)**

---
<a name="most"></a>
**most - browse or page through a text file**
```console
shell> apt-get install most
shell> most
shell> export MANPAGER="/usr/bin/most -s" 
```

**[⬆ Back to Top](#table-of-contents)**

---
<a name="dpkg-reconfigure"></a>
**dpkg-reconfigure - reconfigure an already installed package**
**dpkg-query - a tool to query the dpkg database**

```console
shell> dpkg-query -l

shell> dpkg-reconfigure tzdata
shell> dpkg-reconfigure locales
shell> dpkg-reconfigure dash
shell> dpkg-reconfigure console-setup
shell> dpkg-reconfigure openssh-server  
```

**[⬆ Back to Top](#table-of-contents)**

---
<a name="loco"></a>
```console
shell> loco /var/log/messages
```

**[⬆ Back to Top](#table-of-contents)**

---

<a name="w3m"></a>
```console
shell> w3m -no-cookie -dump http://checkip.dyndns.org/
shell> w3m -dump_head http://www.ubuntu.com/
```
**[⬆ Back to Top](#table-of-contents)**

---
<a name="lsb_release"></a>
**lsb_release - print distribution-specific information**

```console
shell> lsb_release -a

No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 14.04 LTS
Release:	14.04
Codename:	trusty
```
```console
shell> lsb_release -i -s
```
**[⬆ Back to Top](#table-of-contents)**

---
<a name="arp"></a>

```console
shell> arp
shell> arp -f
```

`/etc/ethers`
```
# Ethernet-address  IP-number
08:00:20:00:61:CA  pal
```

### :books: 參考網站：
- [ethers](http://manpages.ubuntu.com/manpages/intrepid/man5/ethers.5.html)

**[⬆ Back to Top](#table-of-contents)**

---

<a name="arptables"></a>

```console
shell> apt-get install arptables
shell> arptables --list
shell> arptables -A INPUT --source-mac 00:15:af:66:ec:57 -j ACCEPT
shell> arptables -A INPUT --source-ip 192.168.111.9 -j ACCEPT
```

**[⬆ Back to Top](#table-of-contents)**

---
<a name="arpspoof"></a>

```console
shell> apt-get install dsniff
shell> arpspoof 192.168.111.1
shell> arpspoof -t 192.168.111.2 192.168.111.1
```

**[⬆ Back to Top](#table-of-contents)**

---
**seq - print a sequence of numbers**
<a name="seq"></a>

```console
shell> seq -f "server%03g" 999
shell> seq 1 2 20
```
**[⬆ Back to Top](#table-of-contents)**

---
**ssh — OpenSSH SSH client (remote login program)**
**ssh-copy-id — use locally available keys to authorise logins on a remote machine**
<a name="ssh"></a>
<a name="ssh-copy-id"></a>
<a name="plink"></a>
```console
shell> ssh -o TCPKeepAlive=yes -o ServerAliveInterval=20 user@example.net
```

```console
shell> ssh-copy-id -i id_dsa.pub user@example.net
```

```console
shell> ssh -CqTfnN -D 1080 user@hostname
```

```console
shell> plink.exe user@hostname -N -D 1080
```

**[⬆ Back to Top](#table-of-contents)**

---
**ip - show / manipulate routing, devices, policy routing and tunnels**
<a name="ip"></a>
```console
shell> ip neigh show
```

**[⬆ Back to Top](#table-of-contents)**

---
**arping - sends IP and/or ARP pings (to the MAC address)**
<a name="arping"></a>

```console
shell> arping
shell> arping -I ethX -c 3 ip-addr
```

**[⬆ Back to Top](#table-of-contents)**

---
**fuser - identify processes using files or sockets**
<a name="fuser"></a>

```console
shell> fuser 80/tcp
shell> fuser -k 80/tcp
```

**[⬆ Back to Top](#table-of-contents)**

---
<a name="host"></a>

```console
shell> host www.apple.com 8.8.8.8
```

**[⬆ Back to Top](#table-of-contents)**

---
**dig - DNS lookup utility**
<a name="dig"></a>

```console
shell> dig www.apple.com
shell> dig @8.8.8.8 www.apple.com
shell> dig +trace www.apple.com
shell> dig +trace A www.apple.com
shell> dig @8.8.8.8 +trace www.apple.com
shell> dig -x 8.8.8.8
shell> dig +short AAAA www.cloudflare.com
shell> dig +short myip.opendns.com @resolver1.opendns.com
```

https://diagnostic.opendns.com/myip

**[⬆ Back to Top](#table-of-contents)**

---
**freebcp - bulk loading utility for Sybase and Microsoft databases**
**tsql - utility to test FreeTDS connections and queries**
<a name="freebcp"></a>
<a name="tsql"></a>

```console
shell> apt-get install freetds-bin
```

`/etc/freetds/freetds.conf`
```
[egServer70]
	host = ntmachine.domain.com
	port = 1433
	tds version = 8.0
```

```console
shell> freebcp "SELECT * FROM database_name.dbo.table_name WHERE " queryout data_file.bcp -S egServer70 -U username -P password -c
```

```console
shell> freebcp database_name.dbo.table_name out data_file.bcp -S egServer70 -U username -P password -c  
```

```console
shell> freebcp database_name.dbo.table_name in data_file.bcp -S egServer70 -U username -P password -c   
```

```console
shell> tsql -S egServer70 -U username -P password
```

```
locale is "en_US.UTF-8"
locale charset is "UTF-8"
using default charset "UTF-8"
1> SELECT * FROM database_name.dbo.table_name;
2> GO 
```

**[⬆ Back to Top](#table-of-contents)**

---
**gpg - OpenPGP encryption and signing tool**
<a name="gpg"></a>
```console
shell> gpg -c testfile.txt
Enter passphrase: 
Repeat passphrase: 
```

```console
shell> gpg testfile.txt.gpg
gpg: CAST5 encrypted data
Enter passphrase: 
```

**[⬆ Back to Top](#table-of-contents)**

---
<a name="export"></a>

```console
shell> export LANG="en_US.UTF-8"
shell> export http_proxy=http://yourproxyaddress:proxyport
shell> export MANPAGER="/usr/bin/most -s"
shell> update-alternatives --config pager
```

### :books: 參考網站：
- [update-alternatives](http://manpages.ubuntu.com/manpages/jaunty/man8/update-alternatives.8.html)

**[⬆ Back to Top](#table-of-contents)**

---
**recode - converts files between character sets**
<a name="recode"></a>

```console
shell> apt-get install recode
```

```console
shell> recode --list | less
shell> recode UTF-16LE..UTF-8
shell> recode UTF-8..UTF-16LE
shell> recode gb2312..utf8
shell> recode big5..utf8
```
```console
shell> echo -n 0x02 | recode latin9/x1..dump-with-names
```

**[⬆ Back to Top](#table-of-contents)**

---
**iconv - Convert encoding of given files from one encoding to another**
<a name="iconv"></a>

```console
shell> iconv --list | less
shell> iconv -f big5 -t utf8
shell> iconv -f utf8 -t big5

shell> iconv -f gb2312 -t utf8
shell> iconv -f utf8 -t gb2312
```

```console
shell> iconv -f BIG-5 -t UTF-8 big5.txt > utf8.txt
```

**[⬆ Back to Top](#table-of-contents)**

---
**convmv - converts filenames from one encoding to another**
<a name="convmv"></a>

```console
shell> apt-get install convmv
```

```console
shell> convmv --list
shell> convmv -f big5 -t utf-8 -r --notest *
```

**[⬆ Back to Top](#table-of-contents)**

---
<a name="crontab"></a>

```.console
shell> crontab
shell> /etc/crontab
```

``` 
SHELL=/bin/bash
PATH=/sbin:/bin:/usr/sbin:/usr/bin
MAILTO=root
HOME=/
# For details see man 4 crontabs
# Example of job definition:
# .---------------- minute (0 - 59)
# | .------------- hour (0 - 23)
# | | .---------- day of month (1 - 31)
# | | | .------- month (1 - 12) OR jan,feb,mar,apr ...
# | | | | .---- day of week (0 - 6) (Sunday=0 or 7) OR sun,mon,tue,wed,thu,fri,sat
# | | | | |
# * * * * * username  command to be executed

# run five minutes after midnight, every day
5 0 * * *       $HOME/bin/daily.job >> $HOME/tmp/out 2>&1

# run at 2:15pm on the first of every month -- output mailed to paul
15 14 1 * *     $HOME/bin/monthly

# run at 10 pm on weekdays, annoy Joe
0 22 * * 1-5    mail -s "It's 10pm" joe%Joe,%%Where are your kids?%

23 0-23/2 * * * echo "run 23 minutes after midn, 2am, 4am ..., everyday"

5 4 * * sun     echo "run at 5 after 4 every sunday"

# Run on every second Saturday of the month
0 4 8-14 * *    test $(date +\%u) -eq 6 && echo "2nd Saturday"

```

```
string         meaning
------         -------
@reboot        Run once, at startup.
@yearly        Run once a year, "0 0 1 1 *".
@annually      (same as @yearly)
@monthly       Run once a month, "0 0 1 * *".
@weekly        Run once a week, "0 0 * * 0".
@daily         Run once a day, "0 0 * * *".
@midnight      (same as @daily)
@hourly        Run once an hour, "0 * * * *".
```

### :books: 參考網站：
- https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/6/html/Deployment_Guide/ch-Automating_System_Tasks.html

**[⬆ Back to Top](#table-of-contents)**

---
**netmask - a netmask generation and conversion program**
<a name="netmask"></a>

```console
shell> apt-get install netmask
```

```console
shell> netmask 60.248.90.170
60.248.90.170/32
```

```console
shell> netmask 60.248.90.170/24
60.248.90.0/24
```

```console
shell> netmask 60.248.90.0:60.248.90.127
60.248.90.0/25
```

```console
shell> netmask 60.248.90.170/24
60.248.90.0/24
```

```console
shell> netmask 60.248.90.0/25 -r
60.248.90.0-60.248.90.127   (128)
```

**[⬆ Back to Top](#table-of-contents)**

---
**sipcalc - IP subnet calculator**
<a name="sipcalc"></a>

```console
shell> apt-get install sipcalc
shell> sipcalc 60.248.90.0 255.255.255.0

-[ipv4 : 60.248.90.0 255.255.255.0] - 0

[CIDR]
Host address		- 60.248.90.0
Host address (decimal)	- 1022908928
Host address (hex)	- 3CF85A00
Network address		- 60.248.90.0
Network mask		- 255.255.255.0
Network mask (bits)	- 24
Network mask (hex)	- FFFFFF00
Broadcast address	- 60.248.90.255
Cisco wildcard		- 0.0.0.255
Addresses in network	- 256
Network range		- 60.248.90.0 - 60.248.90.255
Usable range		- 60.248.90.1 - 60.248.90.254

-
```

**[⬆ Back to Top](#table-of-contents)**

---
**dmidecode - DMI table decoder**
<a name="dmidecode"></a>

```console
shell> apt-get install dmidecode
shell> dmidecode -t
shell> dmidecode -t 16
shell> dmidecode -t 17
shell> dmidecode -t memory
shell> dmidecode -t system
shell> dmidecode -t processor
shell> dmidecode -t bios
```

**[⬆ Back to Top](#table-of-contents)**

---
**lsof - list open files**
<a name="lsof"></a>

```console
shell> lsof
shell> lsof -i 4 -a -p 1234
shell> lsof -i TCP:25
shell> lsof -i -P
```

**[⬆ Back to Top](#table-of-contents)**

---
**strace - trace system calls and signals**
<a name="strace"></a>
```console
shell> strace -fF -p 1234
```

**[⬆ Back to Top](#table-of-contents)**

---
**dd - convert and copy a file**
<a name="dd"></a>

```console
shell> dd if=/dev/sda of=/dev/sdb
shell> dd if=/dev/sda of=/dev/sdb conv=noerror,sync

shell> dd if=/dev/sda of=HardDisk.img
shell> dd if=HardDisk.img of=/dev/sdb 

shell> dd if=/dev/sda1 of=Partition.img
shell> dd if=/dev/sda1 of=/dev/sdb1 bs=4096 conv=noerror,sync 

shell> dd if=/dev/cdrom of=cdrom.iso bs=2048

shell> dd if=/dev/sda | gzip > HardDisk.img.gz
shell> gzip -dc HardDisk.img.gz | dd of=/dev/sda   

shell> dd if=/dev/fd0 of=filename.flp
```

**[⬆ Back to Top](#table-of-contents)**

---
**lscpu - display information on CPU architecture**
**lsblk - list block devices**
**lspci - list all PCI devices**
**lsusb - list USB devices**
**lshw - list hardware**
<a name="lscpu"></a>
<a name="lsblk"></a>
<a name="lspci"></a>
<a name="lsusb"></a>
<a name="lshw"></a>

```console
shell> lscpu
shell> lsusb
shell> lspci
shell> lspci -v

shell> lsblk
shell> lshw
```

**[⬆ Back to Top](#table-of-contents)**

---
<a name="grep"></a>
<a name="egrep"></a>

```console
shell> grep PATTERN testfile.txt
shell> grep -r PATTERN .
shell> grep -nrI PATTERN .
shell> grep -r PATTERN --include "*.txt" .
```


`GREP_COLOR` `GREP_COLORS`

```
shell> head testfile.txt | grep --color=always "PATTERN1" | GREP_COLOR="1;32" --color "PATTERN2" 
```

```console
shell> grep `PATTERN1\|PATTERN2` testfile.txt
```

```console
shell> grep -E 'PATTERN1|PATTERN2' testfile.txt
shell> egrep 'PATTERN1|PATTERN2' testfile.txt

shell> egrep '^root|^mysql' /etc/passwd
shell> egrep '^(root|mysql)' /etc/passwd
shell> egrep -v '#|^$' filename
```

```console
shell> grep -e PATTERN1 -e PATTERN2 testfile.txt
```
```console
shell> grep -E 'PATTERN1.*PATTERN2' testfile.txt
```

```console
shell> grep -E -o "([0-9]{1,3}[\.]){3}[0-9]{1,3}" testfile.txt
shell> grep -E -o "\b[A-Za-z0-9._%+-]+@[A-Za-z0-9.-]+\.[A-Za-z]{2,6}\b" testfile.txt 
```

**[⬆ Back to Top](#table-of-contents)**

---
**date - print or set the system date and time**
<a name="date"></a>

日期轉換成`時間戳記` (`TimeStamp`)
```console
shell> date +%s
shell> date +%s --date '2014-09-13 09:19:36' 
```
`時間戳記` (`TimeStamp`)轉換成日期
```console
shell> date -d @1410571176
```

**[⬆ Back to Top](#table-of-contents)**

---
```console
shell> set +o history
shell> set -o history
```

**[⬆ Back to Top](#table-of-contents)**

---

```console
shell> getconf LONG_BIT
64

shell> uname -m
armv6l
armv7l
x86_64 // 64 位元
       // 32 位元	
```

**[⬆ Back to Top](#table-of-contents)**

---
**update-alternatives - maintain symbolic links determining default commands**
<a name="update-alternatives"></a>

```console
shell> update-alternatives --get-selections
shell> update-alternatives --query editor
shell> update-alternatives --config editor

shell> update-alternatives --config pager
```

```console
shell> visudo

# Allow members of group sudo to execute any command
%sudo   ALL=(ALL:ALL) ALL

# Uncomment to allow members of group sudo to not need a password
%sudo ALL=NOPASSWD: ALL


shell> groupadd sudo
shell> usermod -G sudo <username>
shell> sudo su -

shell> sudo -H -s
shell> sudo -K
```

```
sudo: unable to resolve host 
```

**[⬆ Back to Top](#table-of-contents)**

---
**ldd - print shared library dependencies**
<a name="ldd"></a>
```console
shell> ldd /bin/ls
```

**[⬆ Back to Top](#table-of-contents)**

---
<a name="curlftpfs"></a>
```console
shell> curlftpfs -v -o allow_other -o user="user:pass" ftp.myserver.com:21 /mnt/ftp
shell> curlftpfs -o codepage=utf8,iocharset=big5,ipv4,user={username}:{password} ftp://{servicename} /root/file-sharing
```

```console
shell> .netrc
```
```
machine ftp.host.com  
login myuser  
password mypass 
```

### :books: 參考網站：
- [curlftpfs](http://curlftpfs.sourceforge.net/)

**[⬆ Back to Top](#table-of-contents)**

---

**curl - transfer a URL**<a name="curl"></a>

```console
shell> curl -s --head http://127.0.0.1/

shell> if curl -s --head http://192.168.41.1/ | grep "200 OK" > /dev/null; then ; fi

shell> curl http://127.0.0.1/login?username=admin&password=secret

shell> curl -d "username=admin&password=secret" http://127.0.0.1/login
shell> curl -L -d "username=admin&password=secret" http://127.0.0.1/login

shell> curl -w "\n" -d '{"username":"admin", "password":"secret"}' -H "Content-Type: application/json" http://127.0.0.1/login 

 -H "Content-Type: application/json"
 -H "Accept-Language: zh-TW"
```

**[⬆ Back to Top](#table-of-contents)**

---
**Wget - The non-interactive network downloader.**<a name="wget"></a>

`wget - retrieves files from the web`

```console
shell> brew install wget
```

```console
shell> wget --spider https://www.google.com/textinputassistant/tia.png
shell> wget -nv --spider https://www.google.com/textinputassistant/tia.png
```
```console
shell> wget --mirror --convert-links --adjust-extension --page-requisites --no-parent http://getbootstrap.com/
shell> wget -mkEpnp http://getbootstrap.com/      
```

```console
shell> wget -r --no-parent http://getbootstrap.com/
```


`~/.wgetrc`
```
# You can set the default proxies for Wget to use for http, https, and ftp.
# They will override the value in the environment.
#https_proxy = http://proxy.yoyodyne.com:18023/
#http_proxy = http://proxy.yoyodyne.com:18023/
#ftp_proxy = http://proxy.yoyodyne.com:18023/
     
# If you do not want to use proxy at all, set this to off.
#use_proxy = on
   
# Force the default system encoding
#locale = UTF-8
     
# Force the default remote server encoding
#remoteencoding = UTF-8

content_disposition = on
```

**[⬆ Back to Top](#table-of-contents)**

---
```console
shell> apt-get install exfat-utils exfat-fuse
```
---
**ethtool - query or control network driver and hardware settings**<a name="ethtool"></a>
```console
shell> apt-get install ethtool
shell> ethtool -i eth0
shell> ethtool eth0
```

**[⬆ Back to Top](#table-of-contents)**

---

<a name="wakeonlan"></a>
```console
shell> apt-get install wakeonlan
shell> wakeonlan 00:1c:c0:5e:e4:e8
```

**[⬆ Back to Top](#table-of-contents)**

---
```console
shell> apt-get install udisks
shell> udisks --show-info /dev/sda1
shell> udisks --mount /dev/sda1
shell> udisks --mount /dev/sda1 --mount-fstype=ntfs
shell> udisks --mount /dev/sda1 --mount-options umask=0
Mounted /org/freedesktop/UDisks/devices/sda1 at /media/AEE8EC25E8EBEA13

shell> udisks --show-info /dev/sda1
shell> udisks --unmount /dev/sda1

shell> ls -al /dev/disk/by-uuid

shell> udisks --mount /dev/disk/by-uuid/3AEE81A116ADF905
```

**[⬆ Back to Top](#table-of-contents)**

---

time of last system boot
```console
shell> who -b
shell> last -1 reboot
``` 

```console
echo '{"json":"obj"}' | python -mjson.tool

echo '{"json":"obj"}' | jq '.'
echo '{ "_id" : 5, "type" : "food", "item" : "aaa", "ratings" : [ 5, 8, 9 ] }' | python -mjson.tool | jq '.item'
```

**[⬆ Back to Top](#table-of-contents)**

---
**OptiPNG - Optimize Portable Network Graphics files**<a name="optipng"></a>
**jpegoptim - utility to optimize/compress JPEG/JFIF files.**<a name="jpegoptim"></a>

```console
shell> apt-get install optipng
shell> optipng file.png
shell> optipng -o7 file.png
shell> find . -type f -name "*.png" -exec optipng {} \;
```
```console
shell> apt-get install jpegoptim
shell> jpegoptim --help
shell> jpegoptim --strip-all --preserve --totals --all-progressive --max=90

shell> find . -type f -name "*.png" -exec jpegoptim {} \;
```

**[⬆ Back to Top](#table-of-contents)**

---
```console
shell> apt-get install nfs-kernel-server

rpcbind

/etc/fstab
example.hostname.com:/ubuntu /local/ubuntu nfs rsize=8192,wsize=8192,timeo=14,intr

shell> sudo mount example.hostname.com:/ubuntu /local/ubuntu
```

```console
shell> aptitude install nfs-common rpcbind
shell> service rpcbind start
```
```console
shell> showmount -e 54.183.226.77
Export list for 54.183.226.77:
/pub (everyone)
```

```console
shell> mount.nfs remotetarget dir
shell> mount.nfs 54.183.226.77:/pub /mnt/pub
shell> mount.nfs -o rsize=8192,wsize=8192,timeo=14,intr 54.183.226.77:/pub /mnt/pub
```

**[⬆ Back to Top](#table-of-contents)**

---

**rsync - fast, versatile, remote (and local) file-copying tool**<a name="rsync"></a>

```console
shell> rsync -avz foo:src/bar /data/tmp
shell> rsync -avz --delete src/ dst_directory/

shell> rsync -av --partial --append --progress mylinux.iso 10.1.2.3:~/
shell> rsync -avP --append mylinux.iso 10.1.2.3:~/

shell> rsync -avz --delete --append --progress -e ssh 10.1.2.3:~/src dst_directory/  
```

**[⬆ Back to Top](#table-of-contents)**

---

**aria2 - High speed download utility**<a name="aria2"></a>

```console
shell> apt-get install aria2
shell> brew install aria2
```

**Download a file**

```console
shell> aria2c http://example.org/mylinux.iso
```

**Download a file from 2 different HTTP servers**
```console
shell> aria2c http://a/f.iso ftp://b/f.iso
shell> aria2c -o myfile.zip "http://mirror1/file.zip" "http://mirror2/file.zip"
```

```console
shell> aria2c -x2 http://a/f.iso
shell> aria2c http://example.org/mylinux.torrent
shell> aria2c http://example.org/mylinux.metalink
```

`$HOME/.aria2/aria2.conf`
```
http-accept-gzip=true

ftp-pasv=true
ftp-reuse-connection=true

allow-overwrite=false
always-resume=true
auto-file-renaming=false
continue=true
remote-time=true

enable-dht=true
enable-peer-exchange=true
dht-listen-port=60000
listen-port=60000

disk-cache=0
file-allocation=none

summary-interval=0

seed-ratio=1.0
seed-time=120

disable-ipv6=true

follow-torrent=mem

bt-exclude-tracker="*"

max-upload-limit=50K
all-proxy=http://user:pass@proxy:8888
```

```console
shell> screen -d -m aria2c http://example.org/mylinux.torrent
```

### :books: 參考網站：
- [screen](https://www.gnu.org/software/screen/)

**[⬆ Back to Top](#table-of-contents)**

---

**tmux - terminal multiplexer**


<img src="https://tmux.github.io/ss-tmux1.png" width="600">

<img src="https://tmux.github.io/ss-tmux2.png" width="600">



```console
shell> apt-get install tmux
```

### :books: 參考網站：
- [tmux](https://tmux.github.io/)

**[⬆ Back to Top](#table-of-contents)**

---

```console
shell> apt-get install mosh
```

**[⬆ Back to Top](#table-of-contents)**

---

```console
shell> apt-get install dhcping
shell> dhcping -s 255.255.255.255 -r -v
```

**[⬆ Back to Top](#table-of-contents)**

---

``` .ruby
#!/usr/bin/ruby
require 'net/http'

# Get the first argument from the command-line (the URL)
url = ARGV[0]

begin
  # Create a new HTTP connection
  httpCon = Net::HTTP.new( url, 80 )
  # Perform a HEAD request
  resp, data = httpCon.head( "/", nil )

  # If it succeeded (200 is success)
  if resp.code == "200" then
    # Iterate through the response hash
    resp.each {|key,val|
      # If the key is the server, print the value
      if key == "server" then
        print "  The server at "+url+" is "+val+"\n"
      end
    }
  end
end
```

```console
shell> ./srvinfo.rb www.cisco.com
  The server at www.cisco.com is Apache
shell> ./srvinfo.rb www.microsoft.com
  The server at www.microsoft.com is Microsoft-IIS/8.5
shell> ./srvrinfo.rb www.apache.org
  The server at www.apache.org is Apache/2.4.10 (Unix) OpenSSL/1.0.1i
```

**[⬆ Back to Top](#table-of-contents)**

---
**ncdu - ncurses disk usage viewer**
**pydf - colourised df(1)-clone**
**htop - interactive processes viewer**

```console
shell> apt-get install ncdu
shell> apt-get install pydf
shell> apt-get install htop
```

**[⬆ Back to Top](#table-of-contents)**

---
<a name="geoip"></a>

`/etc/cron.d/geoip-database-contrib`
`/usr/share/GeoIP`

`/usr/share/GeoIP/GeoIP.dat`
`/usr/share/GeoIP/GeoIPv6.dat`

```console
shell> apt-get install geoip-bin
shell> apt-get install geoip-database-contrib
shell> cd /usr/share/GeoIP
shell> wget -q http://geolite.maxmind.com/download/geoip/database/GeoLiteCountry/GeoIP.dat.gz
shell> wget -q http://geolite.maxmind.com/download/geoip/database/GeoIPv6.dat.gz
shell> gunzip -f GeoIP.dat.gz GeoIPv6.dat.gz
shell> geoiplookup 80.60.233.195
```
**[⬆ Back to Top](#table-of-contents)**

---
<a name="hping3"></a>

```console
shell> apt-get install hping3
shell> hping3 -S -p 80 www.apple.com
shell> hping3 www.apple.com -1 -i u100000 -a 100.100.100.100
shell> hping3 www.apple.com -i u100000 -S -F -a 100.100.100.100
shell> hping3 www.apple.com –i u100000 –F –S –R –P –A –U –a 100.100.100.100

shell> hping3 --rand-source www.apple.com       
```

**[⬆ Back to Top](#table-of-contents)**

---

```console
shell> mpstat -P ALL
shell> mpstat -P ALL 2
shell> iostat -d -m -t 2

shell> top -p pid
Linux 3.18.11+ (ip-192-168-42-23) 	09/22/2015 	_armv6l_	(1 CPU)

12:50:14 PM  CPU    %usr   %nice    %sys %iowait    %irq   %soft  %steal  %guest   %idle
12:50:14 PM  all    2.03    0.00    0.59    0.55    0.00    0.02    0.00    0.00   96.82
12:50:14 PM    0    2.03    0.00    0.59    0.55    0.00    0.02    0.00    0.00   96.82
```

**[⬆ Back to Top](#table-of-contents)**

---
**freebsd**
**disks-adding**

```console
shell> dmesg
shell> gpart list da0
shell> gpart destroy da0

shell> gpart create -s GPT da0
shell> newfs -U /dev/da0
shell> mkdir /newdisk

shell> vi /etc/fstab
/dev/da0	/newdisk	ufs	rw	2	2
shell> mount /newdisk
```

### :books: 參考網站：
- [disks-adding](https://www.freebsd.org/doc/handbook/disks-adding.html)

**[⬆ Back to Top](#table-of-contents)**

---
<a name="usbmount"></a>

**usbmount - automatically mount and unmount USB mass storage devices**

```console
shell> apt-get install usbmount
shell> /etc/usbmount/usbmount.conf
```

**[⬆ Back to Top](#table-of-contents)**

---

```console
shell> apt-get install libpam-google-authenticator
shell> google-authenticator
```

`/etc/pam.d/sshd`
```
auth required /lib/security/pam_google_authenticator.so

# Standard Un*x authentication.
# @include common-auth
```

**[⬆ Back to Top](#table-of-contents)**

---

**md5sum - compute and check MD5 message digest**<a name="md5sum"></a>
**sha1sum - compute and check SHA1 message digest**<a name="sha1sum"></a>
**sha256sum - compute and check SHA256 message digest**<a name="sha256sum"></a>

```console
shell> md5sum file
shell> md5sum file > MD5SUMS
shell> md5sum -c MD5SUMS

shell> sha1sum file
shell> sha1sum file > SHA1SUMS
shell> sha1sum -c SHA1SUMS

shell> sha256sum file
shell> sha256sum file > SHA256SUMS
shell> sha256sum -c SHA256SUMS
```
**[⬆ Back to Top](#table-of-contents)**

---

<a name="pv"></a>
<a name="dialog"></a>

**pv - Shell pipeline element to meter data passing through**
**dialog - Displays user-friendly dialog boxes from shell scripts**

```console 
shell> apt-get install pv
shell> yum install pv
shell> brew install pv

shell> apt-get install dialog
shell> brew install dialog

shell> pv file | gzip > file.gz
shell> pv file | nc -w 1 somewhere.com 3000

shell> (pv -n file | gzip > file.gz) 2>&1 | dialog --gauge "Please Wait" 10 70 0
shell> (pv -n file | gzip > file.gz) 2>&1 | dialog --gauge "請稍候" 10 70 0


shell> pv file | md5sum
shell> pv file | sha256sum
shell> pv file | sha512sum

shell> pv -EE /dev/sda > disk-image.img
shell> pv disk-image.img > /dev/sda

shell> pv < /dev/zero > /dev/sda
```

**[⬆ Back to Top](#table-of-contents)**

---

<a name="mencoder"></a>

**mencoder - MPlayer's Movie Encoder**

```console 
shell> apt-get install mencoder
```

**[⬆ Back to Top](#table-of-contents)**

---

**iotop - simple top-like I/O monitor**<a name="iotop"></a>

**[⬆ Back to Top](#table-of-contents)**

---

**imagemagick - image manipulation programs -- binaries**<a name="imagemagick"></a>

```console 
shell> apt-get install imagemagick
shell> convert file1.pdf file2.pdf output-file.pdf
shell> convert file1.pdf[1] file2.pdf[0,5] output-file.pdf
shell> convert file1.pdf[0-9] file2.pdf[0-4] output-file.pdf  
shell> convert *.jpg output-file.pdf  
shell> convert rose.jpg rose.png  
shell> convert rose.jpg -resize 50% rose.png
```

**[⬆ Back to Top](#table-of-contents)**

---

**nikto - Scan web server for known vulnerabilities**<a name="nikto"></a>

```console
shell> apt-get install nikto
shell> nikto -C all -h 127.0.0.1
```
```
- Nikto v2.1.5
---------------------------------------------------------------------------
+ Target IP:          127.0.0.1
+ Target Hostname:    localhost
+ Target Port:        80
+ Start Time:         2016-11-10 21:32:00 (GMT-7)
---------------------------------------------------------------------------
+ Server: nginx/1.10.2
+ Server leaks inodes via ETags, header found with file /, fields: 0x580639b1 0x264 
+ The anti-clickjacking X-Frame-Options header is not present.
+ 6544 items checked: 0 error(s) and 2 item(s) reported on remote host
+ End Time:           2016-11-10 21:32:23 (GMT-7) (23 seconds)
---------------------------------------------------------------------------
+ 1 host(s) tested
```

**[⬆ Back to Top](#table-of-contents)**

---

**dmitry - Deepmagic Information Gathering Tool**<a name="dmitry"></a>

`DMitry`

```console
shell> apt-get install dmitry
shell> dmitry
shell> dmitry -winsepo example.txt example.com
```

- [DMitry](http://tools.kali.org/information-gathering/dmitry)

**[⬆ Back to Top](#table-of-contents)**

---


### :books: 參考網站：

- [putty](http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/putty.html)
- [Better Monitoring Tools For Ubuntu And CentOS](https://www.vultr.com/docs/better-monitoring-tools-for-ubuntu-and-centos)
- https://www.centos.org/docs/5/html/5.2/Deployment_Guide/s1-nfs-client-config-options.html
- https://www.centos.org/docs/5/html/5.2/Deployment_Guide/s1-nfs-client-config.html
- https://www.centos.org/docs/5/html/5.2/Deployment_Guide/s2-nfs-fstab.html
- [http://stedolan.github.io/jq/manual/](http://stedolan.github.io/jq/manual/)
- http://www.ibm.com/developerworks/cn/linux/l-cn-filetransfer/
- http://www.ibm.com/developerworks/cn/linux/l-spider/
- [ldd](http://manpages.ubuntu.com/manpages/maverick/man1/ldd.1.html)
- [using-utils](https://cygwin.com/cygwin-ug-net/using-utils.html)
