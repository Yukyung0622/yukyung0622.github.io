---
layout: post
title: "[Bigdata]Spark - MongoDB 연동"
date: 2022-06-11 21:03:36 +0530
categories: TechnicalNote
---

#spark-shell --conf "spark.mongodb.input.uri=mongodb://chhak:1234@192.168.50.82:27017/chhak.member" --packages org.mongodb.spark:mongo-spark-connector_2.11:2.4.0

#MongoDB 데이터 추출후 HDFS 파일로 저장
scala> import com.mongodb.spark._
scala> val memberRDD = MongoSpark.load(sc).map(line => line.toJson)
scala> memberRDD.saveAsTextFile("hdfs:///sample/memberRDD")

scala> val memberDF = spark.read.json("hdfs:///sample/memberRDD/*")
scala> val userDF = memberDF.select('user, 'name, 'hp, 'pos, 'dep)
scala> userDF.write.format("com.databricks.spark.csv").save("hdfs:///sample/userDF")


