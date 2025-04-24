# [ Neo4j ] Relational Databases vs. Graph Databases

Until now, I had only used relational databases (RDB), especially MySQL. But recently, I had an opportunity to work with a NoSQL database for the first time.

While relational databases are convenient for managing small-scale data, NoSQL databases are often more efficient when handling large-scale or complex data, especially when the data doesn't fit neatly into tables.

In a previous project, I planned to use MongoDB but couldn’t due to other issues. So this time, I’m taking the chance to explore NoSQL databases—especially Neo4j—and document my findings.

---

## 📚 Key Differences Between Relational and Graph Databases

| Relational Database       | Graph Database                        |
|---------------------------|----------------------------------------|
| Uses SQL queries          | Uses Cypher queries                    |
| Table-based structure     | Node and Relationship-based structure  |
| Composed of rows and columns | Nodes and relationships with properties |
| Rigid schema              | Flexible data modeling                 |

---

### ✅ Relational Databases

Relational databases store data in tables using a query language called SQL.  
Each table is composed of rows (records) and columns (fields), where:
- Each row represents an individual data entry
- Each column represents an attribute or feature of that data

They are structured, consistent, and well-suited for applications where data relationships are simple and tabular.

---

### ✅ Graph Databases

Graph databases store data using nodes and relationships.  
- **Nodes** represent entities  
- **Relationships** represent the connections between entities  
- Both nodes and relationships can have **properties**

This structure is more intuitive for modeling real-world relationships and allows for highly flexible and expressive data modeling.

---

### 🔎 Example of Nodes and Relationships in Neo4j

```
(Alice)-[:FRIENDS_WITH]->(Bob)
```

- `Alice`, `Bob`: Nodes (entities)  
- `FRIENDS_WITH`: Relationship (link between entities)  
- You can also add additional properties to both nodes and relationships (e.g., age, registration date)

---

Traditional RDBs require restructuring data to fit into predefined formats. As the volume of data increases, this can lead to complexity and reduced clarity.

In contrast, **graph databases** model data in a way that reflects real-world relationships, making them more **intuitive** and **flexible**, even for non-experts.

> 📌 This post is a summary of my personal experience exploring NoSQL, particularly **Neo4j**.  
> I plan to adopt more diverse database systems in future projects to find the best fit for each use case.
