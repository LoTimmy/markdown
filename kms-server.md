
```console
shell> apt-get install p7zip-full

shell> wget http://rghost.net/download/62BgHwKq9/3aca2cf0274480ba9a34928220b549511fb4c515/3aca2cf0274480ba9a34928220b549511fb4c515/vlmcsd-svn818-2016-03-07-Hotbird64.7z

shell> 7za x vlmcsd-svn818-2016-03-07-Hotbird64.7z -o./kms-server -p2016 
```

```
binaries/Linux/intel/static/
├── vlmcsdmulti-x64-musl-static
├── vlmcsdmulti-x86-musl-static
├── vlmcsd-x64-musl-static
├── vlmcsd-x86-musl-static
├── vlmcsd-x86-musl-static-threads
├── vlmcs-x64-musl-static
└── vlmcs-x86-musl-static

0 directories, 7 files
```

```console
shell> ./vlmcsdmulti-x64-musl-static
vlmcsdmulti svn818, built 2016-03-07 23:06:06 UTC

Usage:
	./vlmcsdmulti-x64-musl-static vlmcsd [<vlmcsd command line>]
	./vlmcsdmulti-x64-musl-static vlmcs [<vlmcs command line>]

shell> ./vlmcsdmulti-x64-musl-static vlmcsd
shell> ./vlmcsdmulti-x64-musl-static vlmcs
```

```
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 0.0.0.0:1688            0.0.0.0:*               LISTEN      14712/vlmcsdmulti-x
tcp6       0      0 :::1688                 :::*                    LISTEN      14712/vlmcsdmulti-x
```


**Windows Server 2012 R2 Server Standard**
```
slmgr.vbs /upk
slmgr.vbs /ipk D2N9P-3P6X9-2R39C-7RTCD-MDVJX
slmgr.vbs /skms 172.16.7.103
slmgr.vbs /ato
slmgr.vbs /dlv
```

<!--
Windows 10 Professional
W269N-WFGWX-YVC9B-4J6C9-T83GX

Windows 7 專業版
FJ82H-XT6CR-J8D7P-XQJJ2-GPDD4
-->


### :books: 參考網站：

- [kms-server](http://forums.mydigitallife.info/threads/50234-Emulated-KMS-Servers-on-non-Windows-platforms)
- [大量啟用的 Slmgr.vbs 選項](https://technet.microsoft.com/zh-tw/library/dn502540.aspx)
- [附錄 A：KMS 用戶端安裝識別碼](https://technet.microsoft.com/zh-tw/library/jj612867.aspx)



