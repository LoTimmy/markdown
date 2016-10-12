![](http://i.imgur.com/3hIAdKc.png)
![](http://i.imgur.com/PTsVNBp.png)

最後更新： 2014-12-30       

`OpenVPN`是透過`OpenSSL`加密庫中的SSLv3/TLSv1協議函數庫，建構企業內部`虛擬私有網路`，`OpenVPN`允許參與建立`VPN`的單點使用公開金鑰、電子證書或是帳戶／密碼來進行身分認證。它並不是一個Web-based的`VPN`軟體，也不與`IPsce`及其他`VPN`軟體相容，目前`OpenVPN`能夠在`Linux`、`FreeBSD`、`OpenBSD`、`Solaris`、`Mac OS X`與微軟的Windows 2000/XP/Vista/2003上運行。 

`OpenVPN`預設採用`1194`埠做通訊，並且**推薦使用`UDP`協議，不過同時也支援`TCP`，使用者可以自己修改**。`OpenVPN`提供了`Tun`和`Tap`驅動兩種虛擬網路介面，透過它們可以建立`Layer3`的IP通道或是虛擬`Layer2`乙太網路，後者可以傳送任何類型的`Layer2`乙太網路封包，並可以使用`LZO演算法`壓縮。使用`Layer3`或`Layer2`時，使用者可以依自己的網路架構做選擇。 

在選擇使用`TCP`或`UPD`協議時，需要注意**如果有高延遲或是遺失封包較多的情況，建議選擇`TCP`協議作為底層傳輸的協定，因`UDP`協定為不可靠傳輸，網路不穩定時可能會導致要求通道上層的協議進行重傳，效率非常低**。 

`OpenVPN`是基於`SSL` (`Secure Socket Layer`)進行資料加密傳輸。

### 在 `Ubuntu` 14.04 LTS 上建置 `OpenVPN` (`SSL VPN`)

安裝作業系統及`OpenVPN`相關套件。
因本文主要介紹`OpenVPN`如何安裝及設定，作業系統方面就不再詳述。

##### 安裝`OpenVPN`

安裝`OpenVPN`套件。
```console 
shell> apt-get install openvpn
```

切換至「/etc/openvpn」目錄下。
```console
shell> cd /etc/openvpn
```
### Certificate Authority Setup
```console
shell> cp -r /usr/share/doc/openvpn/examples/easy-rsa/2.0 ./easy-rsa
```

使用指令「vi vars」開始編輯vars檔。
```console
shell> cd /etc/openvpn/easy-rsa/
shell> vi vars
```
```ini
export KEY_SIZE=2048
export CA_EXPIRE=3650

export KEY_COUNTRY="TW"
export KEY_PROVINCE="Taiwan"
export KEY_CITY="TPE"
export KEY_ORG="Example Company"
export KEY_EMAIL="steve@example.com"
export KEY_CN=MyVPN
export KEY_NAME=MyVPN
export KEY_OU=MyVPN
```
```console
shell> ln -s openssl-1.0.0.cnf openssl.cnf
```
匯出 (Export) 剛剛所編輯的 vars 環境，使用「source vars」
```console
shell> source vars
```
使用指令「./clean-all」清掉所有暫存的CA。
```console
shell> ./clean-all
```
接著建置Root CA。使用指令「./build-ca」來執行此動作。
```console 
shell> ./build-ca
```
---
### Server Certificates

執行指令「./build-key-server server」建置Server Key和Server Crt
```console
shell> ./build-key-server server
```

---

接著建置「密鑰交換」Diffie-Hellman，執行指令「./build-dh」。
```console
shell> ./build-dh
```
```console
shell> cd keys/
shell> cp server.crt server.key ca.crt dh1024.pem /etc/openvpn/
```
---
### Client Certificates
shell> ./build-key client1

開始編輯設定檔。由於剛裝好的OpenVPN並沒有server.conf檔，使用者必須自行從範例檔複製
```console
shell> cp /usr/share/doc/openvpn/examples/sample-config-files/server.conf.gz /etc/openvpn/
shell> gzip -d /etc/openvpn/server.conf.gz
shell> vi /etc/openvpn/server.conf
```

```
push "redirect-gateway def1"
plugin /usr/lib/openvpn/openvpn-auth-pam.so common-account
```

```console
shell> iptables -t nat -A POSTROUTING -s 10.8.0.0/24 -o eth0 -j MASQUERADE
```
---
### 安裝 Google Authenticator (`兩步驟驗證`)
```console
shell> wget https://google-authenticator.googlecode.com/files/libpam-google-authenticator-1.0-source.tar.bz2
shell> apt-get install  libpam0g-dev
```
```console
shell> cd /etc/pam.d
shell> cp common-account openvpn
shell> vi openvpn
```
```
auth required /etc/openvpn/pam_google_authenticator.so
```
```console
shell> vi /etc/openvpn/server.conf
```
```
plugin /usr/lib/openvpn/openvpn-auth-pam.so openvpn
```

---
```console
shell> vim client.ovpn
```
```
client
dev tun
proto tcp

remote my-server-2 443
resolv-retry infinite
nobind

persist-key
persist-tun

<ca>
-----BEGIN CERTIFICATE-----
[...]
-----END CERTIFICATE-----
</ca>
<cert>
-----BEGIN CERTIFICATE-----
[...]
-----END CERTIFICATE-----
</cert>
<key>
-----BEGIN PRIVATE KEY-----
[...]
-----END PRIVATE KEY-----
</key>

ns-cert-type server
comp-lzo

verb 0

auth-user-pass mypassword.txt
auth-nocache
```

---
### :books: 參考網站：


### :books: 參考網站：
- [使用Linux建置企業虛擬私有網路SSL VPN（上）](http://www.netadmin.com.tw/article_content.aspx?sn=1112270002)
- [使用Linux建置企業虛擬私有網路SSL VPN（下）](http://www.netadmin.com.tw/article_content.aspx?sn=1201120003)

![](https://code.google.com/p/tunnelblick/logo?cct=1407712974)
- [tunnelblick](https://code.google.com/p/tunnelblick/)
