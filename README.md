# Irish Constituencies Neo4j Database
###### Shane Carville, G00301235

## Introduction
This Project is to represent the 2016 Irish general eclection using a Neo4j Database. All Candidates and Constituencys are represented using nodes. Each node for a Candidate has their Name, Party, Gender and Constituency as a property. Each node for a Constituency has the Name of the constituency as a label. All Candidate nodes should have a relationship witht their Constituency node. A query should then be entered to get some interesting data like party with the most female Candidates.

## Database
To Create the database I first found a CSV file with the candidates and their constituency and then shortened it down to just the information that I wanted to repersent in the database. I then entered all the information into the Database and had all the nodes created.
To Create the Candidate

``Create (n:Person {name : "Gerry Adams", Gender : "Male", Party : "Sinn Fein", Constituency : "Louth"})``

I then tried to create relationships between the nodes but could not get it to work I think due to the way I had set up my labels and properties for the nodes.
`` MATCH (a:Person {name : "Gerry Adams"}),(b:Constituency : "Louth")
    WHERE a.Person = 'Node A' AND b.Constituency = 'Node B'
    CREATE (a)-[r:RELTYPE]->(b)
    RETURN r ``

## Queries
The queries for the database had the relationships worked are the following - Party with the most Female Canidiates, Constituency with the most Candidates and the Party with the least amount of Candidates. Without the Database fully complete I was unable to test these Queries.

#### Party with most female Candidates
This query retreives the party with the most Female Candidates
```cypher
MATCH
	n-[:Party]
    Where Person.Female < 20
RETURN
	n.Party;
```

#### Constituency with most Candidates
This query retreives the Constituency with the most Candidates
```cypher
MATCH
	n-[Constituency]
    Where Person < 25
RETURN
	n;
```

#### Party with the least amount of Candidates
This query retreives the Party with the least amout of Candidates
```cypher
MATCH
	n-[:Party]
    Where person > 3
RETURN
	n;
```

## References
1. [Neo4J website](http://neo4j.com/), the website of the Neo4j database.
2. [Github Storyful](https://github.com/storyful/irish-elections), The CSV file that I used to get the information on the Candidates.