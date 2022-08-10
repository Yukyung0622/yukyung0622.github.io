---
layout: post
title: "[Bigdata]Spark - MongoDB (Naver 영화)"
date: 2022-06-12 21:03:36 +0530
categories: TechnicalNote
---

# spark-shell --conf "spark.mongodb.input.uri=mongodb://chhak:1234@192.168.50.82:27017/chhak.movies" --packages org.mongodb.spark:mongo-spark-connector_2.11:2.4.0
# movies
scala> import com.mongodb.spark._
scala> val moviesRDD = MongoSpark.load(sc).map(line => line.toJson)
scala> moviesRDD.saveAsTextFile("hdfs:///sample/moviesRDD")

scala> val moviesDF = spark.read.json("hdfs:///sample/moviesRDD/*")
scala> val movieDF = moviesDF.select('reple, 'score)
scala> movieDF.write.format("com.databricks.spark.csv").save("hdfs:///sample/movieDF")


