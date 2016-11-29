
- 在應用程式類型的支援上，`IIS`除了運行`ASP`、`ASP .NET`等`Microsoft`自家的程式語言外，還可以手動方式或者透過`WPI` (`Web Platform Installer`) 圖形介面來安裝在`Linux`作業系統中最廣泛使用的`PHP`程式語言元件，並將其最佳搭檔`MySQL`資料庫系統一併安裝在`Windows`作業系統內。
- 透過`WPI`介面所能夠安裝的不僅只有`IIS`元件、語言套件或是相關管理工具，還可以找到許多以`ASP.NET`或`PHP`所發展的開源應用程式，包括知名的`WordPress`、`Joomla`、`Moodle`、`Gallery Server`、`.Net CMS`等等，而且一旦經由`WPI`介面進行安裝設定後，原本複雜的操作過程都會變得相當容易。 
- 打從`IIS 7.0`版本開始，無論是`Windows Client`或`Windows Server`作業系統，便已經提供了一個名為「`Appcmd`」的命令管理工具，讓系統人員能夠透過它來執行許多批次管理作業，例如針對網站、應用程式、應用程式集區以及虛擬目錄的建立和設定。並且，也可以進行如網站或應用程式集區的啟動與停止，而在進階操作上，還能夠檢視網站運行中的工作處理程序與要求。 

Appcmd 的命令格式是「Appcmd (command) (object-type) < /parameter1:value1 ... >」，主要就是由指定的管理命令（例如Add）搭配所要管理的物件類型（例如Site）與特定的參數，以針對管理物件進行新增、修改或刪除等操作。 
 
想要使用 Appcmd 命令管理工具時，只要先開啟命令提示字元，再下達「cd %windir%\system32\inetsrv」命令，便可以切換到 Appcmd 命令程式的所在路徑並開始使用。 


```console
shell> cd %windir%\system32\inetsrv
```


### :books: 參考網站：
- [IIS服務平台活用技巧 不再只看網站能通就滿足](http://www.netadmin.com.tw/article_content.aspx?sn=1601130003)
- [Appcmd.exe](https://technet.microsoft.com/zh-tw/library/cc772200(v=ws.10).aspx)


---



```console
shell> cmdkey /add:targetname /user:username /pass:password
shell> sc \\targetname query
shell> cmdkey /delete:targetname
```


```console
shell> sc \\myserver create NewService binpath= c:\windows\system32\NewServ.exe
```               

```console
shell> sc [ServerName] stop ServiceName
shell> sc \\myserver stop MSSQLSERVER 
```               

- [sc](https://technet.microsoft.com/en-us/library/bb490995.aspx)



---

### :books: 參考網站：
- [customheaders](http://www.iis.net/configreference/system.webserver/httpprotocol/customheaders)
- [iis-disabling-ssl-v3](https://www.digicert.com/ssl-support/iis-disabling-ssl-v3.htm)
- [iis-ssl-encryption](https://www.digicert.com/iis-ssl-encryption.htm)
- [IISCrypto](https://www.nartac.com/Products/IISCrypto/)
- [如何停用 Internet Information Services 中的 PCT 1.0、SSL 2.0、SSL 3.0 或 TLS 1.0](https:// support.microsoft.com/en-us/kb/187498)
- [如何停用 Internet Information Services 中的 PCT 1.0、SSL 2.0、SSL 3.0 或 TLS 1.0](https://support.microsoft.com/zh-tw/kb/187498)
