# Database

## Facts
- Why We Use Databases
 - Data has always been important. In the past, people stored data in paper ledgers. Finding specific information required searching through the pages manually, and physical records could be lost or damaged.
 - Later, spreadsheets made it easier to store and search data on computers. However, spreadsheets can still be prone to human errors and become difficult to manage as the amount of data grows.
 - Today, we use databases to store and manage large amounts of data in a structured way. Databases make it easier to query, update, validate, organize, and control access to data.
- Structured data — Data that follows a defined structure or format, making it easier to store, organize, and query.
- Types of Databases: Relational, Key-Value, Document, Column-Family, Graph and Vector.
 - Relational Database — Stores data in tables made up of rows and columns, similar to a spreadsheet (Excel).
 - Key-Value Database — Stores data as key-value pairs, similar to a JavaScript object.
 - Document Database — Stores data as documents, commonly using JSON-like structures.
 - Column-Family Database — Stores data in column families and is designed for handling large-scale distributed data.
 - Graph Database — Stores data as nodes and relationships, making it useful for highly connected data. It can be thought of as a network of connected branches, similar to a tree structure.
 - Vector Database — Stores and searches vector embeddings, commonly used in AI/ML applications.
- NoSQL databases are databases that use non-relational data models, such as document, key-value, column-family, or graph models.
- Not all NoSQL databases use the same structure or query language.
- For production, a managed/paid database service can be useful because it can provide things such as backups, monitoring, scaling, maintenance, and managed infrastructure.
- For learning, development, and testing, free or self-hosted databases are often sufficient.
- Choosing the right database brand is important because different database brands are designed for different requirements.
- Paid/managed database services often provide additional features and infrastructure out of the box, while with a free or self-hosted database, you may need to configure and manage many of these things yourself.
- If PostgreSQL or MongoDB is running in Docker, deleting the container does not necessarily delete the database data. If the data is stored in a Docker volume or bind mount, the data can remain on the host system even after the container is deleted. Deleting the container and its associated volume/data storage can permanently remove the data.
- `127.0.0.1` refers to the local machine (localhost). It is an IP address, not a server port.
- A database connection normally requires:
 - Host → e.g. `127.0.0.1`
 - Port → e.g. PostgreSQL commonly uses `5432`
 - Database name
 - Username
 - Password
- IP address = Which computer/server should I connect to?
- Port = Which service/port on that computer/server should I connect to?
- For safety, click the "Test Connection" button to verify the database connection before saving the connection details.
- Basic Database Workflow:
 - 1. Create Database
 - 2. Create Table
 - 3. Insert Data
 - 4. Retrieve Data
 - 5. Update Data
 - 6. Delete Data
- `not null` is not empty.
- `default` is the system automatically give if you don't give value.
- You can access a database with CLI.
- Normalization = organizing data to reduce duplication and keep data consistent.
- Denormalization = intentionally adding some duplication to make reading/querying faster or simpler.
- Denormalization can be necessary for historical records so past data stays accurate even when the original data changes. Example: store the product name and price in the order record so an old order still shows what the customer actually bought and paid at that time.
- `PK` = Primary Key → uniquely identifies a row.
- `FK` = Foreign Key → references a key in another table.
- One-to-Many → one category can contain many menu items.
- Many-to-Many → many students can take many courses.
- You can read the business requirements to determine whether a relationship is One-to-Many or Many-to-Many.
- To identify One-to-Many vs Many-to-Many, focus on one record and check how many records it can connect to. Then reverse the perspective.
 - One → Many + Many → One = One-to-Many.
 - One → Many + Many → Many = Many-to-Many.
 - Example: One category can contain many menu items, such as Coffee → Latte and Espresso. From the Latte perspective, Latte connects to one category: Coffee. Therefore, Category → Menu Item is One-to-Many.
- Pivot table = a middle table used to connect a Many-to-Many relationship.
- Transaction = a group of database operations that either all succeed or roll back if something fails.
- Indexing = improves search/query performance, but indexes take storage and can make `INSERT`, `UPDATE`, and `DELETE` somewhat slower.
- View = a saved query that behaves like a virtual table. It is not exactly caching.
- SQL already has built-in functions, so no need to write the functions yourself.
- `Normalization` is the process of organizing data in relational database tables to reduce data redundancy and prevent data anomalies.
- First Normal Form (1NF):
 - Each cell must contain a single value rather than multiple values.
 - Each row must be uniquely identifiable, typically using a primary key.
 - Each column must contain values of a consistent type.
 - Baby explanation: One cell should contain only one item, not multiple items.
 - Incorrect example (multiple values in one cell):
 - | order_id | products                   |
 - | -------- | -------------------------- |
 - | 1        | iPhone 17 Pro, AirPods Max |
 - The `products` cell contains multiple values.
 - Correct example (one product per row):
 - | order_id | product       |
 - | -------- | ------------- |
 - | 1        | iPhone 17 Pro |
 - | 1        | AirPods Max   |
 - Each cell contains a single product value.
- 2NF (Second Normal Form):
 - A table must satisfy 1NF first.
 - Every non-key attribute must depend on the whole candidate key, not just part of a composite key.
 - It eliminates partial dependencies.
 - Baby explanation: If we already have the item's ID, we don't need to repeat its name in a table where that name depends only on the ID.
 - Not in 2NF:
 - | student_id | course_id | student_name | course_name |
 - | ---------- | --------- | ------------ | ----------- |
 - | 1          | C01       | Alex         | SQL         |
 - | 2          | C02       | Bob          | Java        |
 - | 1          | C02       | Alex         | Java        |
 - Fix: Separate the tables:
 - Students:
 - | student_id (PK) | student_name |
 - | --------------- | ------------ |
 - | 1               | Alex         |
 - | 2               | Bob          |
 - Courses:
 - | course_id (PK) | course_name |
 - | -------------- | ----------- |
 - | C01            | SQL         |
 - | C02            | Java        |
 - Enrollments:
 - | student_id (PK, FK) | course_id (PK, FK) |
 - | ------------------- | ------------------ |
 - | 1                   | C01                |
 - | 2                   | C02                |
 - | 1                   | C02                |
- `Denormalization`: Intentionally duplicates data to make reading data faster or queries simpler. Baby explanation: Sometimes, we duplicate data to make it easier or faster to retrieve. Example: Storing historical prices and monthly sales totals so past sales records and monthly sales reports display the correct data.
- Deleting records: If a parent record is referenced by records in a child table, you generally need to delete the related child records first, then delete the parent record. This prevents foreign key constraint violations.
- Transaction rollback = Undoes changes made by a transaction, returning the database to its state before the transaction began (or to a savepoint if one is used).
- Indexing = Improves data retrieval speed by allowing the database to find records more efficiently, especially in large tables containing millions of rows.
- Indexes make data retrieval faster, but they can slow down `INSERT`, `UPDATE`, and `DELETE` operations because the database must maintain the indexes.
- `VIEW`: Similar to caching because it simplifies data access, but it doesn't store query results.


## Syntax
**Heading 1**
```js 
 <!-- code here -->
```
- Description


**Heading 2**
```js 
 <!-- code here -->
```
- Description

## Terminal Commands
### Terminal tool name 1

**Heading 1**
```bash
 <!-- code here -->
```
- Description


**Heading 2**
```bash
 <!-- code here -->
```
- Description


### Terminal tool name 2

**Heading 1**
```bash
 <!-- code here -->
```
- Description


**Heading 2**
```bash
 <!-- code here -->
```
- Description

## Tools
- Oracle Database — A commercial enterprise database. If I were buying a database for production, I would choose Oracle Database.
- MySQL — An open-source relational database owned by Oracle Corporation. It remains widely used, but there are concerns in the open-source community about Oracle's stewardship and the future direction of the project. PostgreSQL may be a better default choice for my own new projects.
- SQLite — A lightweight, embedded relational database. It is commonly used for mobile apps, desktop applications, testing, and small-to-medium workloads. It is not inherently limited to "small storage," but it is generally not the first choice for enterprise-level or large-scale production applications.
- Prisma and Drizzle are ORMs/database tools that make working with databases easier. They let you work with database data using programming-language code instead of writing raw SQL for everything. They also provide features such as type safety, queries, and schema management.