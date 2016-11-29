
開源的分散式叢集架構的儲存軟體`DRBD` (`Distributed Replicated Block Device`)，也就是**類似磁碟陣列的`RAID 1`**，不過，`RAID 1`是在同一臺電腦內執行， `DRBD`則是**透過網路，來確保資料一致性與可靠性**。


將兩臺伺服器主機的網路卡，經由1G專線串接，然後把兩臺伺服器主機硬碟建置成`RAID 1`，當資料寫入A主機時，B主機也會同步寫入，中間沒有經過任何交換器等設備，而是經由網路專線來達到資料同步，因此，可以避免交換器故障或是交換器端頻寬滿載等問題，進而保證資料的一致性與可靠性。

![](http://upload.wikimedia.org/wikipedia/commons/5/5b/DRBD_concept_overview.png)
![](http://docs.oracle.com/cd/E19957-01/mysql-refman-5.5/images/drbd-main.png)


![](http://docs.oracle.com/cd/E19957-01/mysql-refman-5.5/images/drbd-sepinterface.png)
 
~~~~
shell> lsb_release -a
~~~~
~~~~
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 14.04 LTS
Release:	14.04
Codename:	trusty
~~~~

##### Setting Up a DRBD Primary Node
~~~~
shell> apt-get install drbd8-utils
shell> apt-get install xfsprogs
~~~~
~~~~
shell> cd /etc/drbd.d/
shell> cp global_common.conf{,.bak}
shell> > global_common.conf
~~~~

~~~~
global { usage-count no; }
common { protocol C; }
resource r0 {
    meta-disk internal;
    device /dev/drbd0;

    on drbd01 {
        disk /dev/sdb1;
        address 192.168.154.128:7788;
    }
    on drbd02 {
        disk /dev/sdb1;
        address 192.168.154.129:7788;
}
~~~~

~~~~
shell> modprobe drbd
shell> lsmod | grep drbd  
shell> drbdadm create-md r0
shell> drbdadm up r0
shell> drbdadm -- --overwrite-data-of-peer primary all
shell> mkfs.xfs /dev/drbd0
  
shell> watch -n1 cat /proc/drbd
shell> drbdsetup /dev/drbd0
shell> mount /dev/drbd0 /srv
echo "DRBD Device" >/srv/samplefile 
~~~~

~~~~
shell> service drbd status
~~~~
~~~~
drbd driver loaded OK; device status:
version: 8.4.3 (api:1/proto:86-101)
srcversion: F97798065516C94BE0F27DC 
m:res  cs         ro                 ds                 p  mounted  fstype
0:r0   Connected  Primary/Secondary  UpToDate/UpToDate  C  /srv     xfs
~~~~

##### Setting Up a DRBD Secondary Node
~~~~
shell> apt-get install drbd8-utils
~~~~
~~~~
shell> cd /etc/drbd.d/
shell> cp global_common.conf{,.bak}
shell> > global_common.conf
~~~~

~~~~
global { usage-count no; }
common { protocol C; }
resource r0 {
    meta-disk internal;
    device /dev/drbd0;

    on drbd01 {
        disk /dev/sdb1;
        address 192.168.154.128:7788;
    }
    on drbd02 {
        disk /dev/sdb1;
        address 192.168.154.129:7788;
}
~~~~

~~~~
shell> modprobe drbd
shell> lsmod | grep drbd
~~~~
----------
~~~~
shell> service drbd status
~~~~
~~~~
drbd driver loaded OK; device status:
version: 8.4.3 (api:1/proto:86-101)
srcversion: F97798065516C94BE0F27DC 
m:res  cs          ro                 ds                     p  mounted  fstype
...    sync'ed:    27.1%              (3062620/4193116)K
0:r0   SyncTarget  Secondary/Primary  Inconsistent/UpToDate  C
~~~~

~~~~
drbd driver loaded OK; device status:
version: 8.4.3 (api:1/proto:86-101)
srcversion: F97798065516C94BE0F27DC 
m:res  cs         ro                 ds                 p  mounted  fstype
0:r0   Connected  Secondary/Primary  UpToDate/UpToDate  C
~~~~
----------

##### Testing

DRBD Primary Node
~~~~
shell> cp -r /etc/default /srv
shell> umount /srv
shell> drbdadm secondary r0
~~~~

DRBD Secondary Node
~~~~
shell> drbdadm primary r0
shell> mount /dev/drbd0 /srv 
~~~~
----------
[DRBD](https://help.ubuntu.com/14.04/serverguide/drbd.html)
[http://docs.oracle.com/cd/E19957-01/mysql-refman-5.5/ha-overview.html](http://docs.oracle.com/cd/E19957-01/mysql-refman-5.5/ha-overview.html)
