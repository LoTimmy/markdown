
最後更新： 2015-11-13         


```console
shell> @powershell -NoProfile -ExecutionPolicy unrestricted -Command "(iex ((new-object net.webclient).DownloadString('https://chocolatey.org/install.ps1'))) >$null 2>&1" && SET PATH=%PATH%;%ALLUSERSPROFILE%\chocolatey\bin
```

```console
shell> iex ((new-object net.webclient).DownloadString('https://chocolatey.org/install.ps1'))
```

```console
shell> choco
Chocolatey v0.9.9.11 
```

```console
shell> choco install mkvtoolnix
shell> choco install jre8
shell> choco install quicktime
shell> choco install ccleaner
shell> choco install googlechrome
shell> choco install dotnet4.0
shell> choco install dropbox
shell> choco install git.install
shell> choco install rdcman
shell> choco install mpc-hc
shell> choco install defraggler
```

```console
shell> choco install flashplayerplugin
shell> choco install googlechrome
shell> choco install firefox
shell> choco install ie11
shell> choco install googlechrome-allusers
shell> choco install unitywebplayer

shell> choco install git.install -y
shell> choco install tortoisegit

shell> choco install 7zip.install
shell> choco install winrar -y

shell> choco install beyondcompare
shell> choco install markdownpad2

shell> choco install autoit
shell> choco install innosetup
shell> choco install nodejs.install
shell> choco install skype
shell> choco install google-chrome-x64
shell> choco install dropbox
shell> choco install wget
shell> choco install wireshark
shell> choco install winscp
shell> choco install winscp.install

shell> choco install rdcman

shell> choco install line

shell> choco install handbrake.install

shell> choco install mssqlservermanagementstudio2014express
shell> choco install sql2012.nativeclient
shell> choco install sqlserver2014express
shell> choco install sqlserver2012express

shell> choco install visualstudio2013ultimate
shell> choco install visualstudio2013professional
shell> choco install visualstudiocommunity2013
shell> choco install visualstudio2015community

shell> choco install k-litecodecpackfull
shell> choco install vmwarevsphereclient

shell> choco install conemu
shell> choco install pstools -y


shell> choco install bginfo

shell> choco install mysql
shell> choco install mongodb
shell> choco install redis-64
shell> choco install rabbitmq
shell> choco install memcached
shell> choco install nginx
```

```console
shell> choco upgrade winrar
```

```console
shell> choco install snagit
ZEN5H-24LZK-TNYET-2EGKJ-MMCE4
```
### :books: 參考網站：

- [chocolatey](https://chocolatey.org/)
- [packages](https://chocolatey.org/packages)