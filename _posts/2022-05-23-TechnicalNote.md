---
layout: post
title: "[AWS]EC2 톰캣 8080 포트포워딩"
date: 2022-05-23 21:03:36 +0530
categories: TechnicalNote
---

AWS EC2는 유저 권한의 프로세스가 80 포트 사용을 제한하기 때문에 80포트로 들어오는 것을 8080포트로 포워딩 시켜줘야 한다.

```
# iptables -t nat -I PREROUTING -p tcp --dport 80 -j REDIRECT --to-port 8080

# service iptables save
```

[출처] https://m.blog.naver.com/halowd/221936944706
