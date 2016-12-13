---

```console
shell> gcc -v
```




```c
/* HelloWorld */
#include <stdio.h>

int main (void)
{
  printf ("HelloWorld\n");
  return 0;
}
```

```c
#include <stdio.h>
#include <ctype.h>
#include <regex.h>
#include <sys/types.h>

#include <errno.h>
#include <stdarg.h>

#include <stdlib.h>
#include <string.h>
#include <unistd.h>



strends()
fclose()
isdigit()
getchar()
sleep (1);
```

```console
shell> gcc -o myprog myprog.c 
```


---

```c
int i;
int j;
int i = 0;
int k = 0;
int i, j, k;

int lines = 0;
int total = 1;

unsigned short k = 65533;
char buffer [10];
int x[10] = { 1, 2, 3, 4, 5, 6, 7, 8, 9, 10 };
char c;

int main( void )
{
}


int myarray[10];
int myarray[10];
char myarray[10];

printf("\"\n");
printf("\t\"");   
```

- [資料類型範圍](https://msdn.microsoft.com/zh-tw/library/s3f49ktz.aspx)

---

**Syntax**
```
do
statement
while ( expression ) ;
```

**Example**
```c
#include <stdio.h>
int main()
{
  int i = 0;
  do
  {
    printf("\n%d",i++);
  } while (i < 3);
}
```
---

```
   while ( expression )
statement
```

**Example**
```c
#include <stdio.h>

int main()
{
  int i = 0;

  while (1) {
    printf("\n%d",i++);
    sleep (1);          
  }
}
```

```console
shell> gcc -o while_statement while_statement.c 
```

---

```c
#include <stdio.h>

int main()
{
  for (int i = 0 ; i < 5 ; i++) {
    printf("\n%d", i);
  }
}   
```

```console
shell> gcc -o myprog myprog.c -std=c99
```

---

```c
#include <stdio.h>

int main (void)
{
  FILE *file;
  const char *filename;
  int c;
  filename = "myfile.txt";

  file = fopen(filename, "r");

  if (file) {
    while ((c = getc(file)) != EOF) putchar(c);
    fclose(file);
  }

  return 0;
}
```

```c
#include <stdio.h>

int main (void)
{
  FILE *file;
  const char *filename;
  int c;
  filename = "myfile.txt";

  file = fopen(filename, "r");

  if (file == NULL) err(2, "can't open %s", filename);
  while ((c = getc(file)) != EOF) putchar(c);
  fclose(file);

  return 0;
}
```

```c
#include <stdio.h>
#include <assert.h>

int main (void)
{
  FILE *file;
  const char *filename;
  int c;
  filename = "myfile.txt";

  file = fopen(filename, "r");
  assert (file);
  while ((c = getc(file)) != EOF) putchar(c);
  fclose(file);

  return 0;
}
```

```console
shell> gcc -o myprog myprog.c -g
shell> ulimit -c unlimited
shell> gdb myprog core
```

```console
shell> file core
core: ELF 64-bit LSB  core file x86-64, version 1 (SYSV), SVR4-style, from './myprog'
```

```
(gdb) where
(gdb) info frame
```

```console
shell> gcc -o myprog myprog.c -O3
```

```
Segmentation fault (core dumped)
Aborted (core dumped)
```


```
"r"  開啟以讀取。如果檔案不存在或找不到，fopen 呼叫就會失敗。
"w"  開啟空白檔案以寫入。如果指定的檔案已存在，其內容將被終結。
"a"  開啟以供在檔案結尾寫入 (附加)，並且在將新資料寫入檔案之前，不會移除檔案結尾 (EOF) 標記。如果檔案不存在時，建立檔案。
"r+" 開啟以進行讀取和寫入。檔案必須存在。
"w+" 開啟空白檔案以進行讀取和寫入。如果檔案存在，其內容會遭到銷毀。
"a+" 開啟以進行讀取和附加。附加作業包括在將新資料寫入檔案之前移除 EOF 標記。寫入完成後，不會還原 EOF 標記。如果檔案不存在時，建立檔案。
```

---

```c
#include <stdio.h>
#include <ctype.h>

int main (void)
{
  int i = 0;
  char c;
  char string[] = "HELLO WORLD!";

  while (string[i])
  {
    putchar(tolower(string[i]));
    i++;
  }

  return 0;
}
```

---

```c
#include <stdio.h>

int main (void)
{
  for (int i = 1 ; i < 10 ; i++) {
    for (int j = 1 ; j < 10 ; j++) {
      printf(" %d*%d=%2d ", i, j, i*j);
    }
    printf("\n");
  }

  return 0;
}
```

```console
shell> gcc -o myprog myprog.c -std=c99
```

---

```console
shell> g++ -o myprog myprog.cpp
```

---

```c
#include <sys/socket.h>
#include <netinet/in.h>
#include <arpa/inet.h>
#include <unistd.h>
#include <stdlib.h>
#include <string.h>
#include <stdio.h>

define 

len
AF_INET
SOCK_DGRAM
int     
struct 
char         
sizeof

bzero 
sockaddr 


int main (void) {
  int sock, len;
  struct sockaddr_in name;
  sizeof(struct sockaddr_in);
  

  /* Create the socket. */
  sock = socket (AF_INET, SOCK_DGRAM, 0);
  if (sock < 0) {
    perror ("socket");
    exit (EXIT_FAILURE);
  }

}
```

- [](http://lobert.iteye.com/blog/1769618)
- [netinet_in.h](http://pubs.opengroup.org/onlinepubs/9699919799/basedefs/netinet_in.h.html)
- [arpa_inet.h](http://pubs.opengroup.org/onlinepubs/9699919799/basedefs/arpa_inet.h.html)
- [sys_socket.h](http://pubs.opengroup.org/onlinepubs/9699919799/basedefs/sys_socket.h.html)

---


①
②
③
④
⑤
⑥
⑦



- [mingw](http://www.mingw.org/)
- [include](https://msdn.microsoft.com/zh-tw/library/36k2cdd4.aspx)