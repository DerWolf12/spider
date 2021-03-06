## 🕷️ Spider
> Make a graph network of your followers.

<p align="center"><img width=100% src="https://github.com/instautils/spider/raw/master/resources/intro.png"></p>

---

#### Neo4j Graph Database

> Neo4j is the most popular graph database according to DB-Engines ranking, and the 22ⁿᵈ most popular database overall.

```
$ docker-compose up
```

#### Dependencies

```
$ sudo pip install -r requirements.txt
```

#### Start spider.py

```bash
$ export INSTAGRAM_NEO4J='' 
$ export INSTAGRAM_USERNAME='' 
$ export INSTAGRAM_PASSWORD='' 
$ python spider.py # running with python 2
```


### NEO4J Example Queries

```
MATCH (a:Person {gender: 'female'})-[:FOLLOW]->(b:Person) 
WITH a, count(b) as c 
WHERE c > 2 
RETURN a
```

```
MATCH (a:Person {gender: 'female'})-[:FOLLOW]->(b:Person) 
WITH a, collect(b) as collection, count(b) as c 
WHERE c > 2
RETURN a, collection
```

```
MATCH (me:Person {name: "aidenzibaei"}), (a:Person {gender: 'female'})-[:FOLLOW]->(b:Person) 
MATCH path = allShortestPaths((me)-[*..6]-(a))
WITH a, count(b) as c, path 
WHERE c > 3 RETURN a, path
```

---

<p align="center"><img width=100% src="https://github.com/instautils/spider/raw/master/resources/neo4j_2.png"></p>

<p align="center"><img width=100% src="https://github.com/instautils/spider/raw/master/resources/neo4j_1.png"></p>