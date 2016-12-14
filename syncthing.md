<img alt="Syncthing" title="Syncthing" src="https://apt.syncthing.net/images/logo-horizontal.svg" width=20% height=20%>

```console
# Add the release PGP keys:
shell> curl -s https://syncthing.net/release-key.txt | sudo apt-key add -

# Add the "release" channel to your APT sources:
shell> echo "deb https://apt.syncthing.net/ syncthing release" | sudo tee /etc/apt/sources.list.d/syncthing.list

# Update and install syncthing:
shell> sudo apt-get update
shell> sudo apt-get install syncthing
```

---

### :books: 參考網站：
- https://apt.syncthing.net/
- https://docs.syncthing.net/


