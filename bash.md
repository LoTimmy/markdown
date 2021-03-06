- `Bash Shell`為`UNIX`的殼層程式，不但是`GNU`作業系統的殼層程式，也是`Linux`及`Mac OS X`的預設殼層程式，算是各種`Linux`版本上最常見的公用程式。它採用命令列介面，允許使用者輸入文字命令，也可讓使用者遠端下達指令（如透過`ssh`或` telnet`）。
- `Bash`是一個指令列`shell` （殼層）程式，廣泛存在於 `Linux`、`BSD` 和 `Mac OS X` 等`UNIX-based`的作業系統，使用者只要將指令輸入到一個簡單的文字式視窗，作業系統便會依指令運作。

---
```console
shell> foo='() { echo not patched; }' bash -c foo
```

```console
shell> env x='() { :;}; echo vulnerable' bash -c "echo this is a test"
```

```sh
# for name [ [ in [ word ... ] ] ; ] do list ; done

for seq in 1 2 3 4 5 6 7 8 9 10; do
  echo $seq
done

for seq in $(seq 1 2 20); do
  echo $seq
done

# for (( expr1 ; expr2 ; expr3 )) ; do list ; done
for (( i=1; i<=5; i++ )); do
    echo $seq
done

# 無限迴圈
for (( ; ; )); do
    echo "Hello World!"
done
 
```
---

```
((expression))
expression1 && expression2
[[ expression ]]

-eq
-ne
-lt
-le
-gt
-ge
  
```

```sh
#!/bin/bash
while true
do
  echo "$(date +"%Y-%m-%d %T") $(netstat -ntap | grep 46998 | grep ESTABLISHED | wc -l)" | tee -a LogFile
  sleep 2
done
```

```sh
#!/bin/bash

i=1
while [ $i -le 5 ]
do
  echo $i
  (( i++ ))
done
```


```sh
RAM_SIZE=$(free -b | grep Mem | awk '{print $2}')
HOSTNAME=`/bin/hostname -f`

uname -m | grep 64
IS_64BIT=$?
#BIT_WIDTH=64
BIT_WIDTH=32
CONNTRACK_MAX=$(($RAM_SIZE / 16384 * 32 / $BIT_WIDTH))

echo $IS_64BIT
echo $CONNTRACK_MAX
echo $RAM_SIZE
echo $RANDOM

echo My home directory is $HOME
echo "My current directory is $PWD"
```

---
```sh
#!/bin/bash

ip=$(curl -s https://api.ipify.org)
echo "My public IP address is: $ip"
```

### :books: 參考網站：
- [ipify](https://www.ipify.org/)

---

```sh
#!/bin/bash
if COMMANDS; then COMMANDS;
else COMMANDS;
fi
```

---

### :books: 參考網站：
- [Unix /Linux 的Bash Shell 出現重大漏洞，危險等級可能超越 Heartbleed](http://www.ithome.com.tw/news/91107)
- [Bash 漏洞已出現攻擊行動，又傳出修補後仍有漏洞！](http://www.ithome.com.tw/news/91148)
- [Bash 漏洞連環爆：第二波修補還未完，第三波漏洞又來襲！](http://www.ithome.com.tw/news/91233)
- [Linux大廠二度釋出Shellshock漏洞的修補程式！](http://www.ithome.com.tw/news/91180)