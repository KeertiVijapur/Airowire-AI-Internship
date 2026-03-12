# Parsing JSON for Data Analysis (https://www.youtube.com/watch?v=1lxrb_ezP-g)

JSON (JavaScript Object Notation) is a widely used format for storing and transferring structured data. APIs, logs, configuration files, and large datasets often store data in JSON format.

However, JSON data can be complex because it often contains **nested structures**, making it challenging to process efficiently, especially when dealing with large datasets.

This exercise demonstrates different techniques and tools for **extracting, transforming, and analyzing JSON data**.

---

# Why JSON Parsing is Important

In real-world data pipelines, JSON is commonly used for:

* API responses
* Application logs
* Configuration files
* Data exchange between services

Large JSON files may contain thousands or millions of records. Efficient parsing techniques help process this data without loading everything into memory.

---

# Tools for Processing JSON

Different tools can be used depending on the size and complexity of the JSON data.

| Tool                   | Purpose                     | Use Case                            |
| ---------------------- | --------------------------- | ----------------------------------- |
| **jq**                 | Command-line JSON processor | Quick filtering and transformation  |
| **JMESPath**           | Query language for JSON     | Extract values from nested JSON     |
| **ijson**              | Streaming JSON parser       | Efficient processing of large files |
| **Pandas**             | Data analysis library       | Convert JSON to structured tables   |
| **SQL JSON Functions** | Query JSON inside databases | Analyze JSON stored in SQL tables   |
| **DuckDB JSON**        | Analytical queries on JSON  | Fast processing of large datasets   |

---

# Example JSON Processing Techniques

## 1. Command-Line Processing using jq

`jq` allows quick exploration of JSON data directly from the command line.

Example:

```bash
cat data.json | jq '.select(.type == "user") | {id, name}'
```

Use cases:

* filtering logs
* extracting specific fields
* quick data inspection

---

# 2. Extracting Data using JMESPath

JMESPath is a powerful query language used to extract specific fields from nested JSON.

Example JSON:

```python
import jmespath

data = {
 "locations":[
 {"name":"Seattle","state":"WA","info":{"population":737015}},
 {"name":"Portland","state":"OR","info":{"population":652503}}
 ]
}

cities = jmespath.search("locations[?info.population > `700000`].name", data)
```

Output:

```
["Seattle"]
```

This helps extract values from deeply nested structures.

---

# 3. Streaming Large JSON Files with ijson

Loading very large JSON files into memory can crash systems.

`ijson` solves this by **streaming data incrementally**.

Example:

```python
import ijson

with open("large.json") as file:
    parser = ijson.items(file, "item")

    for record in parser:
        if record["value"] > 100:
            print(record)
```

Advantages:

* memory efficient
* processes very large files
* ideal for log analytics

---

# 4. JSON Analysis using Pandas

Pandas can convert JSON into tabular format for easier analysis.

Example:

```python
import pandas as pd
import json

df = pd.read_json("data.json")
df = pd.json_normalize(df)
```

Benefits:

* convert nested JSON to dataframe
* perform aggregations
* visualize data easily

---

# 5. SQL JSON Functions

Modern databases support JSON functions that allow querying JSON fields directly.

Example:

```sql
SELECT
 json_extract(data, '$.name') as name,
 json_extract(data, '$.email') as email
FROM users
WHERE json_extract(data, '$.active') = true;
```

Advantages:

* analyze JSON without external scripts
* integrate with relational databases

---

# 6. DuckDB JSON Processing

DuckDB supports fast analytics directly on JSON data.

Example:

```sql
SELECT
 json_extract(data, '$.user.name') AS name,
 avg(json_extract(data, '$.metrics.value')) AS avg_value
FROM logs
GROUP BY name;
```

DuckDB is useful when analyzing **large datasets locally without heavy database setup**.

---

# Practical Example: Analyzing API Data

A Python script can fetch JSON data from APIs and analyze it.

Steps involved:

1. Fetch JSON from API
2. Parse the JSON response
3. Extract relevant fields
4. Store results locally
5. Sort or analyze data

Example workflow:

```python
import requests

url = "https://api.example.com/data"
response = requests.get(url)

data = response.json()

for item in data:
    print(item["name"], item["value"])
```
