---
layout: post
title: "[AWS]EC2 root로 로그인하기"
date: 2022-05-24 21:03:36 +0530
categories: TechnicalNote
---

1. AWS EC2 생성하기
2. 해당 키페어를 이용하여 EC2 접속하기 (ec2-user)
    또는 브라우저에서 인스턴스 마우스 오른쪽 메뉴에서 연결
3. 접속후 다음과 같은 순서로 변경합니다. 
- sudo passwd root
- sudo vi  /etc/ssh/sshd_config
    ( 38 : PermitRootLogin no를 yes로 변경)
    ( 65 : PasswordAuthentication no를 yes로 변경)

- sudo mkdir /root/.ssh
- sudo cp /home/ec2-user/.ssh/authorized_keys /root/.ssh
- sudo service sshd restart
4. root로 접속하기