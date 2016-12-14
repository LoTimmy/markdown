
logstash

```console
shell> java -version

shell> curl -O https://download.elasticsearch.org/logstash/logstash/logstash-{logstash_version}.tar.gz
shell> tar -zxvf logstash-1.5.0.tar.gz
```

```console
shell> cd logstash-{logstash_version}
shell> bin/logstash -e 'input { stdin { } } output { stdout {} }'
```

```
hello world
2013-11-21T01:22:14.405+0000 0.0.0.0 hello world
```

```console
shell> bin/logstash -e 'input { stdin { } } output { stdout { codec => rubydebug } }'
```

```
goodnight moon
{
  "message" => "goodnight moon",
  "@timestamp" => "2013-11-20T23:48:05.335Z",
  "@version" => "1",
  "host" => "my-laptop"
}
```


```console
shell> curl -O https://download.elasticsearch.org/elasticsearch/elasticsearch/elasticsearch-1.5.1.tar.gz
shell> tar -zxvf elasticsearch-1.5.1.tar.gz
shell> cd elasticsearch-1.5.1/
shell> ./bin/elasticsearch
```

```console
shell> bin/logstash -e 'input { stdin { } } output { elasticsearch { host => localhost } }'
```

```
you know, for logs
```
```console
shell> curl 'http://localhost:9200/_search?pretty'
```

```console
shell> bin/logstash -e 'input { stdin { } } output { elasticsearch { host => localhost } stdout { } }'
```


logstash-simple.conf
```
input { stdin { } }
output {
  elasticsearch { host => localhost }
  stdout { codec => rubydebug }
}
```

```console
bin/logstash -f logstash-simple.conf
```


### :books: 參考網站：
https://www.elastic.co/guide/en/logstash/current/getting-started-with-logstash.html