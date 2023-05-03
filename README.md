Download Link: https://assignmentchef.com/product/solved-cs1656-lab6-cypherneo4jpython
<br>
In this lab, we will query a Neo4j graph database using with Cypher language and Python. Neo4j is a highly scalable, native graph database purpose-built to leverage not only data but also its relationships. Cypher is a declarative graph query language that allows for expressive and efficient querying and updating of the graph store.

In [1]: <em># Use the following to get the neo4j database password from the user </em>import getpass

print (“Give me your neo4j password:”) neopass = getpass.getpass()

<em>#print (“You typed:”, neopass)</em>

Give me your neo4j password:

<ul>

 <li>·······</li>

</ul>

In [2]: from neo4j import GraphDatabase

<em># More information on neo4j python API at:</em>

<em># http://neo4j.com/docs/api/python-driver/current/</em>

<em>#Connect to the database </em>uri = “bolt://localhost:7687” <em>#auth=(“neo4j”, neopass) </em>driver = GraphDatabase.driver(uri, auth=(“neo4j”, neopass))

<em>#Start new session </em>session = driver.session()

<em>#Start new transaction </em>transaction = session.begin_transaction()

<strong>1.2.1     Queries</strong>

<strong>Q1) Find the actor named “Tom Hanks”.</strong>

In [ ]: result = transaction.run(“”” MATCH (tom:Actor {name: ‘Tom Hanks’})

RETURN tom ;”””) for record in result: print (record)

1

<strong>1.2.2     Tasks</strong>

<strong>Q2) Find the movie with title “Avatar”.</strong>

<strong>Q3) Find movies released in the 1990s.</strong>

<strong>Q4) List all Tom Hanks movies.</strong>

<strong>Q5) Who directed “Avatar”.</strong>

<strong>Q6) Tom Hanks’ co-actors.</strong>

<strong>Q7) How people are related to “Avatar”.</strong>

<strong>Q8) Extend Tom Hanks co-actors, to find co-co-actors who haven’t worked with Tom Hanks.</strong>

<strong>Q9) Find someone to introduce Tom Hanks to Tom Cruise. Let’s close the session and the transaction.</strong>

In [ ]: transaction.close() session.close()