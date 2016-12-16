### 停用 IPv6

~~~~~~~~~~
shell> vim /etc/sysctl.conf
~~~~~~~~~~
~~~~~~~~~~
[...]
net.ipv6.conf.all.disable_ipv6 = 1
~~~~~~~~~~
~~~~~~~~~~
shell> reboot
~~~~~~~~~~
----------
~~~~~~~~~~
shell> vim /etc/default/grub 
~~~~~~~~~~
~~~~~~~~~~
[...]
GRUB_CMDLINE_LINUX="ipv6.disable=1"
[...]
~~~~~~~~~~

~~~~~~~~~~
shell> update-grub
shell> reboot
~~~~~~~~~~

----------
[如何停用 IPv6 或 Windows 中 IPv6 的元件](http://support.microsoft.com/kb/929852/zh-tw)