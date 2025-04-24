# [Neo4j] Installing Neo4j with Docker and Connecting it with Python

---

## 📚 Installing Neo4j with Docker

Here's how to install Neo4j using Docker.

If you prefer to install it on your local machine directly, you can download the installer from the [official Neo4j website](https://neo4j.com/download/).

```bash
$ docker pull neo4j
$ docker run --publish=7474:7474 --publish=7473:7473 --publish=7687:7687 --volume=$HOME/neo4j/data:/data neo4j
```

Once installation is complete, open **Docker Desktop** to confirm the Neo4j container is running.

You can access the Neo4j browser at [http://localhost:7474/](http://localhost:7474/).

- Default username: `neo4j`  
- Default password: `neo4j`

---

## 📚 Connecting with Python

Next, let's connect Neo4j with Python.

```bash
$ pip install neo4j
```

After installation, you can check the installed version using the following code:

```python
from neo4j import __version__ as neo4j_version
print(neo4j_version)
# Example output: 5.7.0
```

> (As of April 2023, the latest version is: 5.7.0)

---

Here is an example of how to connect to Neo4j from Python:

```python
from neo4j import GraphDatabase

driver = GraphDatabase.driver('bolt://localhost:7687', auth=('neo4j', '0000'))
# driver = GraphDatabase.driver(uri, auth=(user, password))
session = driver.session()
```

- `bolt://` is the Bolt protocol used by Neo4j for communication.
- `7687` is the default port for Neo4j.

Once the code runs, you can visit the [Neo4j browser](http://localhost:7474/) to confirm the connection.
