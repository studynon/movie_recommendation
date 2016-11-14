## 电影推荐系统
这是一个经典推荐系统的案例, 数据集来自于MoviesLens. 借鉴https://www.codementor.io/spark/tutorial/building-a-recommender-with-apache-spark-python-example-app-part1 完成的. 但是作者有些地方没有进行格式转换, 在我的机器上运行不了(也许跟运行环境有关?)
比如:
...
    return ID_and_ratings_tuple[0], (nratings, sum(float(x) for x in ID_and_ratings_tuple[1])/nratings) # float一定要加
...
movie_rating_counts_RDD = movie_ID_with_avg_ratings_RDD.map(lambda x: (int(x[0]), x[1][0])) # int一定要加, 否则会报unicode不兼容错误

作者使用自定义函数的时候先groupByKey在用自定义函数map, 在网上搜了一下更提倡用reduceByKey和aggregaeByKey(因为他们可以直接使用自定义函数)

作者给的案例还是很良心的, 连url的下载\解压的代买都包括了, 如果本地已经有数据集了, 可以注释掉这部分代码.




