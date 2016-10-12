上次更新日期： 6/23/2016 6:26:00 PM                                                          

```console 
shell> mkvmerge --no-subtitles --title '' -o mymovie.mkv input.mkv
shell> mkvmerge -o mymovie.mkv input.mkv zh-TW.idx
shell> mkvmerge -o mymovie.mkv input.mkv zh-TW.srt  
```

```console 
shell> mkvmerge -o MM-complete.mkv MyMovie-with-sound.mkv MyMovie-add-audio.ogg
shell> mkvmerge -o MM-complete.mkv -A MyMovie.avi MyMovie.ogg MyMovie-add-audio.ogg
shell> mkvmerge -o output.mkv --language 0:fre franASais.ogg --language 0:deu deutsch.ogg
```

```console 
shell> mkvmerge --list-languages
```

```
English language name                                                            | ISO639-2 code | ISO639-1 code
-------------------------------+---------------+--------------
Chinese                                                                          | chi           | zh           
English                                                                          | eng           | en
Japanese                                                                         | jpn           | ja           
Korean                                                                           | kor           | ko           
```

```console 
shell> mkvpropedit movie.mkv --tags all:
```



```

mkvmerge -o mymovie.mkv mymovie.avi mymovie.srt
HandBrakeCLI
mkvmerge
mkvinfo
mkvextract
mkvpropedit
input.mkv
file.mkv
movie.mkv

java -jar BDSup2Sub
java -jar BDSup2Sub.jar --help
java -jar BDSup2Sub.jar


```
