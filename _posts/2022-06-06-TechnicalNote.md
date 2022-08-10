---
layout: post
title: "[Bigdata]hdfs dfs-put ShellScript"
date: 2022-06-06 21:03:36 +0530
categories: TechnicalNote
---

<move_weather_to_namenode.sh>
#!/bin/sh
date=$(date +%Y-%m-%d -d '-1days')
echo $date
scp  -r  ./weather/$date  root@192.168.56.201:/root/weather/
rm   -rf ./weather/$date
exit 0

<put_weather_to_hdfs.sh>
#!/bin/sh
date=$(date +%Y-%m-%d -d '-1days')
hdfs  dfs  -put  ./weather/$date    /weather
rm    -rf  ./weather/$date
exit 0

