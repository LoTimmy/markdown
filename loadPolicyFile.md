- 一般而言，來自於A網域的`Flash`應用程式無法存取B網域的資料，但這同時也限制了`Flash`應用程式的能力，`Adobe`為了解決該問題推出了 `crossdomain.xml` 以讓特定網域能夠存取其他網域的資料。
- 根據預設，Flash Player 會尋找從連接埠 843 提供的通訊端原則檔。

```js
if (www.foo.com/myExample.swf getURL( www.bar.com/images/myImage.jpg ) ) {
  www.bar.com/crossdomain.xml
} else {
}
```

www.bar.com/crossdomain.xml
```
<?xml version="1.0"?> 
<!DOCTYPE cross-domain-policy SYSTEM "http://www.adobe.com/xml/dtds/cross-domain-policy.dtd"> 
<cross-domain-policy> 
  <allow-access-from domain="www.foo.com" /> 
</cross-domain-policy>
```


```
<?xml version="1.0"?>
<cross-domain-policy>
  <allow-access-from domain="*"/>
</cross-domain-policy>
```


```
System.security.loadPolicyFile("http://foo.com/sub/dir/pf.xml");
System.security.loadPolicyFile("xmlsocket://foo.com:414");
Security.loadPolicyFile("xmlsocket://server.com:2525");
```

```
<policy-file-request/>
```

```
<cross-domain-policy> 
    <allow-access-from domain="*" to-ports="507" /> 
    <allow-access-from domain="*.foo.com" to-ports="507,516" /> 
    <allow-access-from domain="*.bar.com" to-ports="516-523" /> 
    <allow-access-from domain="www.foo.com" to-ports="507,516-523" /> 
    <allow-access-from domain="www.bar.com" to-ports="*" /> 
</cross-domain-policy>
```



http://www.adobe.com/devnet/flex/flex-sdk-download.html



### :books: 參考網站：
- [loadPolicyFile (security.loadPolicyFile 方法)](http://help.adobe.com/zh_TW/as2/reference/flashlite/WS5b3ccc516d4fbf351e63e3d118ccf9c47f-7a8b.html)
- [Managing Flash Player security](http://help.adobe.com/en_US/Flex/4.0/UsingFlashBuilder/WS6f97d7caa66ef6eb1e63e3d11b6c4d0d21-7ec3.html)
- [http://help.adobe.com/zh_TW/AS2LCR/Flash_10.0/help.html?content=00000474.html](http://help.adobe.com/zh_TW/AS2LCR/Flash_10.0/help.html?content=00000474.html)
- [http://help.adobe.com/zh_TW/ActionScript/3.0_ProgrammingAS3/WS5b3ccc516d4fbf351e63e3d118a9b90204-7c60.html](http://help.adobe.com/zh_TW/ActionScript/3.0_ProgrammingAS3/WS5b3ccc516d4fbf351e63e3d118a9b90204-7c60.html)
- [http://docs.unity3d.com/Manual/SecuritySandbox.html](http://docs.unity3d.com/Manual/SecuritySandbox.html)
- [http://help.adobe.com/en_US/flex/using/WS2db454920e96a9e51e63e3d11c0bf6167e-7fff.html](http://help.adobe.com/en_US/flex/using/WS2db454920e96a9e51e63e3d11c0bf6167e-7fff.html)
