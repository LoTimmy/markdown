### 在 `Ubuntu` 14.04 LTS 上建置 `yowsup`

因本文主要介紹`yowsup`如何安裝及設定，作業系統方面就不再詳述。

```console
shell> lsb_release -a
```
```
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 14.04 LTS
Release:	14.04
Codename:	trusty
```
### 安裝 yowsup 
```console

shell> pip install yowsup2

shell> aptitude install python python-dateutil ncurses-dev python-setuptools libevent-dev python-dev 
shell> git clone https://github.com/tgalal/yowsup.git
shell> cd yowsup
shell> sudo python setup.py install
shell> yowsup-cli version
yowsup-cli v2.0.13
Using yowsup v2.4

shell> yowsup-cli registration --phone 886988086692 --cc 886 -r sms
shell> yowsup-cli registration --phone 886981995183 --cc 886 -r sms

INFO:yowsup.common.http.warequest:{"status":"sent","length":6,"method":"sms","retry_after":10805}

status: sent
retry_after: 10805
length: 6
method: sms

shell> yowsup-cli registration --phone 886988086692 --cc 886 -R 642958
shell> yowsup-cli registration --phone 886981995183 --cc 886 -R 389-620

status: ok
kind: free
pw: rMO5/3g2Ur90QV994sW3w5F25Pc=
price: NT$30
price_expiration: 1422699213
currency: TWD
cost: 30.00
expiration: 1450800544
login: 886981995183
type: existing


shell> yowsup-cli demos --login 886981995183:rMO5/3g2Ur90QV994sW3w5F25Pc= --yowsup

shell> yowsup-cli demos --login 886981995183:rMO5/3g2Ur90QV994sW3w5F25Pc= --send 886988086692 "測試訊息"
shell> yowsup-cli demos --login 886981995183:rMO5/3g2Ur90QV994sW3w5F25Pc= --send 886988086692 "Test Message"

```

```console
shell> yowsup-cli demos --login 886981995183:rMO5/3g2Ur90QV994sW3w5F25Pc= --yowsup
Yowsup Cli client
==================
Type /help for available commands

[offline]:/help
---------------------
/account       delete                                       Delete your account 
/group         participants   [group_jid]                   Get pariticipants in a group
/group         setSubject     [jid] [subject]               Change group subject
/help                                                       Print this message  
/seq                                                        Send init seq       
/contacts      sync           [contacts]                    Sync contacts, contacts should be comma separated phone numbers, with no spaces
/keys          set                                          Send prekeys        
/keys          get            [jid]                         Get shared keys     
/image         send           [number] [path]               Send and image      
/presence      available                                    Set presence as available
/presence      subscribe      [contact]                     Subscribe to contact's presence updates
/presence      unsubscribe    [contact]                     Unsubscribe from contact's presence updates
/presence      name           [name]                        Set presence name   
/presence      unavailable                                  Set presence as unavailable
/ping                                                       Ping server         
/L                                                          Quick login         
/state         paused         [jid]                         Send paused state   
/state         typing         [jid]                         Send typing state   
/groups        create         [subject]                     Create a new group with the specified subject
/groups        list                                         List all groups you belong to
/disconnect                                                 Disconnect          
/login                        [username] [b64password]      Login to WhatsApp   
/ib            clean          [dirtyType]                   Send clean dirty    
/message       broadcast      [numbers] [content]           Broadcast message. numbers should comma separated phone numbers
/message       send           [number] [content]            Send message to a friend
---------------------
[offline]:
```



```
[offline]:/L
Auth: Logged in!
[connected]:/message send 886988086692 測試訊息
[connected]:/message send 886988086692 "Test Message"       
```

```ini
############# Yowsup Configuration Sample ###########
cc=886
phone=886981995183
password=rMO5/3g2Ur90QV994sW3w5F25Pc=
#######################################################
```



### :books: 參考網站：

[yowsup](https://github.com/tgalal/yowsup)
[yowsup-cli](https://github.com/tgalal/yowsup/wiki/Yowsup-2.0-Command-line-client)

