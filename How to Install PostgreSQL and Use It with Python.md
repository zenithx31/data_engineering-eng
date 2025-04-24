# 📚 What is PostgreSQL?

PostgreSQL is an open-source relational database management system (RDBMS).

A relational database stores data in a table format, allowing relationships between tables. For example, on a website, "members" and "orders" might be stored in separate tables, but they can be linked together to efficiently manage and retrieve information.

PostgreSQL is a stable and high-performance database system that supports ACID (Atomicity, Consistency, Isolation, Durability) properties and is widely used in web applications.

---

# 📚 How to Install PostgreSQL

### 1) Install Homebrew

Homebrew is a package manager that makes installing software on macOS easy.

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

### 2) Install PostgreSQL

Use Homebrew to install PostgreSQL version 15.

```bash
brew install postgresql@15
```

### 3) Start PostgreSQL

```bash
brew services start postgresql@15
```

### +) Stop PostgreSQL

```bash
brew services stop postgresql@15
```

### 4) Check Status

```bash
brew services list
```

If PostgreSQL is running, the status will show "started".

---

# 📚 Using the Database

### 1) Connect to the Database

```bash
psql postgres
```

By default, a database named `postgres` is created, so you can connect to it right away.

If you see an error like "psql command not found", set your environment variable like this:

```bash
export PATH="/opt/homebrew/opt/postgresql@15/bin:$PATH"
```

### 2) Create a New User Account

Replace `'test0'` with your desired username.

```bash
createuser -s test0
```

### 3) Connect with User Account

```bash
psql -U test0 postgres
```

### 4) Create a New Database

```sql
CREATE DATABASE test_db0;
```

### 5) List Databases

```bash
\l
```

### 6) Connect to a Database

```bash
\c test_db0
```

---

# 📚 Working with Tables

### 1) Create a Table

```sql
CREATE TABLE test_table0 (
    id SERIAL PRIMARY KEY,
    name VARCHAR(50),
    age INT,
    email VARCHAR(100)
);
```

### 2) View Table Structure

```bash
\d test_table0
```

### 3) Insert Data

```sql
INSERT INTO test_table0 (name, age, email) VALUES
('Tom', 25, 'tom@example.com'),
('Jeffrey', 30, 'jeffrey@example.com'),
('Gracie', 28, 'gracie@example.com');
```

### 4) Query Data

```sql
SELECT * FROM test_table0;
```

---

# 📚 Connecting PostgreSQL with Python

Use the `psycopg2` library to interact with PostgreSQL in Python.

### 1) Install the Package

```bash
pip install psycopg2
# If error occurs
pip install psycopg2-binary
```

### 2) Sample Python Code

```python
# insert_data.py

import psycopg2

conn = psycopg2.connect(
    dbname="test_db0",
    user="test0",
    # password="yourpassword",
    host="localhost",
    port="5432"
)

cur = conn.cursor()

# Insert sample data
data = [
    ("Chris", 27, "chris@example.com"),
    ("Emily", 24, "emily@example.com")
]

for user in data:
    cur.execute("INSERT INTO test_table0 (name, age, email) VALUES (%s, %s, %s)", user)

conn.commit()

# Query data
cur.execute("SELECT * FROM test_table0;")
rows = cur.fetchall()

for row in rows:
    print(row)

cur.close()
conn.close()
```

---

# 📚 Mini Project Using PostgreSQL (Trending Keyword Analysis System)

Features: User search logging, trending keyword list  
Tech stack: PostgreSQL, FastAPI, psycopg2

---

### 1) Start the Server

```bash
brew services start postgresql@15
brew services list
```

### 2) Create a New Database

```bash
psql postgres
CREATE DATABASE trend_db;
\l
```

### 3) Use the New Database

```bash
\c trend_db
```

### 4) Create a Table

```sql
CREATE TABLE searches (
    id SERIAL PRIMARY KEY,
    keyword VARCHAR(100) NOT NULL,
    searched_at TIMESTAMP DEFAULT NOW()
);
```

```bash
\d searches
```

### 5) Python Setup

```python
# trend_db.py

import psycopg2

DB_NAME = "trend_db"
DB_USER = "test0"
# DB_PASSWORD = "yourpassword"
DB_HOST = "localhost"
DB_PORT = "5432"

def get_connection():
    return psycopg2.connect(
        dbname=DB_NAME,
        user=DB_USER,
        # password=DB_PASSWORD,
        host=DB_HOST,
        port=DB_PORT
    )
```

---

### 6) Install FastAPI

```bash
pip install fastapi
```

### 7) Connect FastAPI with PostgreSQL

```python
# main.py

from fastapi import FastAPI

app = FastAPI()

trending_keywords = ["Python", "FastAPI", "PostgreSQL"]

@app.post("/search")
def add_search(keyword: str):
    if keyword not in trending_keywords:
        trending_keywords.append(keyword)
    return {"message": f"Keyword '{keyword}' has been saved."}

@app.get("/trending")
def get_trending():
    return {"trending_keywords": trending_keywords}
```

### 8) Install uvicorn

```bash
pip install uvicorn
```

### 9) Run uvicorn

```bash
uvicorn app:app --reload
```

### 10) Test the API

```bash
curl -X 'POST' 'http://127.0.0.1:8000/search?keyword=Python'
curl -X 'GET' 'http://127.0.0.1:8000/trending'
```

---

### 11) Add Save & Duplicate Prevention Functionality (Update `main.py`)

```python
# main.py

from fastapi import FastAPI

app = FastAPI()

trending_keywords = ["Python", "FastAPI", "PostgreSQL"]

@app.post("/search")
def add_search(keyword: str):
    if keyword not in trending_keywords:
        trending_keywords.append(keyword)
    return {"message": f"Keyword '{keyword}' has been saved."}

@app.get("/trending")
def get_trending():
    return {"trending_keywords": trending_keywords}
```

### 12) Restart Server

```bash
uvicorn main:app --reload
```

### 13) Save 'JavaScript' Test

```bash
curl -X 'POST' 'http://127.0.0.1:8000/search?keyword=JavaScript'
curl -X 'GET' 'http://127.0.0.1:8000/trending'
```

Now 'JavaScript' is successfully saved.
