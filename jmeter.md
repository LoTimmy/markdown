![](http://jmeter.apache.org/images/logo.svg)

- `Apache JMeter`壓力測試
- `Apache`基金會`Jakarta`計畫的`JMeter`，`JMeter`是開放原始程式碼的軟體


使用`JMeter`进行性能测试

`測試計畫` (`Test Plan`)

`執行緒群組` (`Thread Group`)
- `HTTP 要求` (`HTTP Request`)
- `檢視結果樹`
- `彙整報告` (`Summary Report`)
- `HTTP 標頭管理員`
- `CSV 資料設定`
- `一致隨機計時器` (`Gaussian Random Timer`)
    

建立`测试计划`（`Test Plan`）

`Number of Threads`： 設置發送請求的用戶數目
`Ramp-up period`： **每個請求發生的總時間間隔，單位是秒**。比如你的請求數目是5，而這個參數是10，那麼每個請求之間的間隔就是10／5，也就是2秒
`Loop Count`： 請求發生的重複次數，如果選擇後面的forever（默認），那麼 請求將一直繼續，如果不選擇forever，而在輸入框中輸入數字，那麼請求將重複指定的次數，如果輸入0 ，那麼請求將執行一次。


我們應該將Number of Threads設置為5，Ramp-up period設置為0（也就是同時並發請求），不選中forever，在Loop Count後面的輸入框中輸入2，設置後的屏幕截圖如下：
![](https://www.ibm.com/developerworks/cn/java/l-jmeter/images/image003.png)





Non-GUI Mode (Command Line mode)
```console
shell> jmeter -n -t my_test.jmx -l log.jtl -H my.proxy.server -P 8000
```

![](http://jmeter.apache.org/images/screenshots/template_menu.png)

![](http://jmeter.apache.org/images/screenshots/http-request.png)

![](http://jmeter.apache.org/images/screenshots/http-request-advanced-tab.png)

![](http://jmeter.apache.org/images/screenshots/timers/gauss_random_timer.png)

![](http://www.badboy.com.au/static/images/fsscreenshot.png)
---

### :books: 參考網站：
- [Download Apache JMeter](https://jmeter.apache.org/download_jmeter.cgi)
- [get-started](http://jmeter.apache.org/usermanual/get-started.html)
- [HTTP_Request](http://jmeter.apache.org/usermanual/component_reference.html#HTTP_Request)
- [解決網站效能問題的關鍵做法（下）](http://www.ithome.com.tw/voice/91536)
- [badboy](http://www.badboy.com.au/)
- [使用JMeter进行性能测试](https://www.ibm.com/developerworks/cn/java/l-jmeter/)