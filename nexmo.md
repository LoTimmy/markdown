
```bash
#!/bin/bash
sms () {
  to=$1
  text=$2
  # curl "http://rest.nexmo.com/sms/json?api_key=ee28ba0a&api_secret=cc1aa8ea&from=MyCompany20&to=$to&type=unicode&text=$text";
  # curl -fs https://rest.nexmo.com/sms/json -G -X GET \
  curl -fs https://rest.nexmo.com/sms/json -G -X POST  \
    --data-urlencode "api_key=ee28ba0a" \
    --data-urlencode "api_secret=cc1aa8ea" \
    --data-urlencode "from=MyCompany20" \
    --data-urlencode "to=$to" \
    --data-urlencode "type=unicode" \
    --data-urlencode "text=$text"
}

sms 886981995183 Test Message
sms 886981995183 測試訊息
```

### :books: 參考網站：
- [nexmo](https://www.nexmo.com/)
- [docs](https://docs.nexmo.com/)