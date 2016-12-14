![](https://www.kali.org/wp-content/uploads/2015/09/kali-2.0-website-logo-300x90.png)

![](https://www.kali.org/wp-content/uploads/2013/03/kali-special-features-ISO1.png)

![](http://docs.kali.org/wp-content/uploads/2013/02/kali-usb-150x150.png)

---

![](http://docs.kali.org/wp-content/uploads/2013/02/kali-pass-150x150.jpg)

```
toor
```

---

```console 
shell> xzcat kali-$version-rpi2.img.xz | dd of=/dev/sdb bs=512k
```

```console
shell> xz -d kali-$version-rpi2.img.xz
shell> diskutil list
shell> diskutil unmountDisk /dev/disk3
shell> sudo dd bs=4m if=~/Downloads/kali-$version-rpi2.img of=/dev/disk3
shell> dd if=~/Downloads/kali-$version-rpi2.img | pv | sudo dd bs=4m of=/dev/disk3
shell> diskutil eject /dev/disk3
```
---

```console
shell> iwconfig
shell> iwconfig wlan0
shell> iwlist wlan0 scan
shell> vim /etc/wpa_supplicant/wpa_supplicant.conf
```

```
country=GB
ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
update_config=1

network={
	ssid="example wpa-psk network"
	key_mgmt=WPA-PSK
	proto=WPA
	pairwise=TKIP
	group=TKIP
	psk="secret passphrase"
}

network={
	ssid="Sapido_RB-1602G3_d179e7"
	key_mgmt=WPA-PSK
	proto=WPA2
	pairwise=TKIP
	group=TKIP
	psk="12345678"
}

```




- [rpi](https://images.offensive-security.com/arm-images/kali-2.1.2-rpi.img.xz)
- [rpi2](https://images.offensive-security.com/arm-images/kali-2.1.2-rpi2.img.xz)

### :books: 參考網站：
- [install-kali-linux-arm-raspberry-pi](http://docs.kali.org/kali-on-arm/install-kali-linux-arm-raspberry-pi)
- [kali-linux-raspberry-pi2](http://docs.kali.org/kali-on-arm/kali-linux-raspberry-pi2)

---

```console 
shell> wget -q -O - https://www.kali.org/archive-key.asc | gpg --import
shell> gpg --keyserver hkp://keys.gnupg.net --recv-key 7D8D0BF6
shell> gpg --list-keys --with-fingerprint 7D8D0BF6
shell> gpg --verify SHA1SUMS.gpg SHA1SUMS
```

---



