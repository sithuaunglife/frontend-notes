# MongoDB

## Facts
- MongoDB is a NoSQL database that stores data as documents.
- NoSQL databases don't require a fixed schema.
- MongoDB is a widely used NoSQL database.
- BSON = Binary JSON, the format MongoDB uses to store documents.
- MongoDB has a shell for interacting with databases from the command line.
- MongoDB Compass can display MongoDB documents in a table-like view, similar to a relational database.
- Unlike SQL, MongoDB doesn't require you to create a table before inserting data. You can insert a document directly, and MongoDB can create the collection automatically if it doesn't exist.
- MongoDB has operators that start with `$` and are used to perform different operations on data.
- MongoDB Compass provides a GUI where you can write and run MongoDB queries without using the MongoDB shell.
- For `updateOne()`, all update operators go inside the same `{}`.
- In MongoDB, an aggregation is basically a set of instructions/stages that process data step by step.
- Aggregation is important for processing and analyzing data from multiple documents.
- You can write multiple conditions in one field to filter results, such as `$gte` and `$lte`. Example: `{ age: { $gte: 18, $lte: 30 } }` This means age must be between 18 and 30.
- Embedding = storing related data inside the same MongoDB document. Good when the related data belongs closely to the parent.
- MongoDB supports relationships between data, even though it is NoSQL.
- Referencing = storing a reference such as an _id to another document, then fetching that related document separately. It's similar in purpose to SQL relationships/joins, but referencing itself is not the same thing as a SQL JOIN.
- MongoDB supports indexing. Indexes make queries faster by creating a data structure MongoDB can use to find documents efficiently.
- Validation = checking whether incoming/stored data follows defined rules. It's not exactly security. Validation helps maintain correct data and can prevent malformed/unexpected input.

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
### MongoDB shell

- `use my_db` switches to a database. If the database doesn't exist, MongoDB creates it when data is first stored.
- `db.createCollection("first")` creates a collection.
- `db.first.find()` retrieves documents from the `first` collection.
- `db.first.find({_id: 1})` filters the documents in the `first` collection and retrieves the document where `_id` is `1`.
- `db.first.insert({_id: 1, name: "John"})` inserts a document and manually sets its _id to 1. If `_id` is not provided, MongoDB automatically generates an _id for the document.
- `db.first.updateOne({_id: 1}, {$set: {m: "ooo"} })` updates only one document that matches `_id: 1` by setting `m` to `"ooo"`.
- `db.first.deleteOne({_id: 1})` deletes only one document that matches `_id: 1`.


**Inserting single document**
```MongoDB shell
db.products.insertOne({
  _id: 1,
  name: "iPhone 17 Pro",
  category: "smartphone",
  price: 1249.00,
  stock: 500,
  created_at: new Date(),
  updated_at: new Date()
});
```
- `db.products.insertOne()` inserts one document into the products collection. If the collection doesn't exist, MongoDB creates it automatically.
- `_id: 1` manually sets the unique identifier of the document.
- `name` stores the product name.
- `category` stores the product category.
- `price` stores the product price.
- `stock` stores the available quantity.
- `created_at` stores the date and time when the document is created.
- `updated_at` stores the date and time when the document is last updated.
- `new Date()` generates the current date and time.


**Inserting multiple document**
```MongoDB shell
db.products.insertMany([
  { _id: 2,  name: "MacBook Air",           category: "laptop",      price: 1099.00, stock: 300,  created_at: new Date(), updated_at: new Date() },
  { _id: 3,  name: "MacBook Pro",           category: "laptop",      price: 1999.00, stock: 200,  created_at: new Date(), updated_at: new Date() },
  { _id: 4,  name: "iPad Air",              category: "tablet",      price: 599.00,  stock: 400,  created_at: new Date(), updated_at: new Date() },
  { _id: 5,  name: "iPad Pro",              category: "tablet",      price: 999.00,  stock: 350,  created_at: new Date(), updated_at: new Date() },
  { _id: 6,  name: "AirPods Pro",           category: "audio",       price: 249.00,  stock: 1000, created_at: new Date(), updated_at: new Date() },
  { _id: 7,  name: "AirPods Max",           category: "audio",       price: 549.00,  stock: 250,  created_at: new Date(), updated_at: new Date() },
  { _id: 8,  name: "Apple Watch Series 11", category: "wearable",    price: 399.00,  stock: 700,  created_at: new Date(), updated_at: new Date() },
  { _id: 9,  name: "Apple TV 4K",           category: "accessory",   price: 129.00,  stock: 800,  created_at: new Date(), updated_at: new Date() },
  { _id: 10, name: "Mac Mini",              category: "desktop",     price: 599.00,  stock: 450,  created_at: new Date(), updated_at: new Date() },
  { _id: 11, name: "iPhone 17",             category: "smartphone",  price: 999.00,  stock: 600,  created_at: new Date(), updated_at: new Date() }
]);
```
- `db.products.insertMany()` inserts multiple documents into the products collection. If the collection doesn't exist, MongoDB creates it automatically.
- `_id` manually sets the unique identifier for each document.
- `name` stores the product name.
- `category` stores the product category.
- `price` stores the product price.
- `stock` stores the available quantity.
- `created_at` stores the date and time when the document is created.
- `updated_at` stores the date and time when the document is last updated.
- `new Date()` generates the current date and time.


- `db.products.find({category: "laptop"})` filters the documents in the `products` collection and retrieves documents where the `category` is `"laptop"`.
- `db.products.find({price: {$gt : 1000}})` filters the documents in the `products` collection and retrieves documents where the `price` is greater than `1000`.
- `db.products.deleteMany({_id: {$in: [4, 7, 9]}})` deletes multiple documents whose `_id` is `4`, `7`, or `9`. `$in` matches a field against any value in the specified array.


**Update One and Set**
```MongoDB shell
db.products.updateOne(
  { _id: 1 },
  { $set: { price: 1249.00 }, $currentDate: { updated_at: true } }
);
```
- `db.products.updateOne({_id: 1}, {$set: {price: 1249.00}, $currentDate: {updated_at: true}})` updates one document where `_id` is `1`.
- `$set` changes the price field to 1249.00.
- `$currentDate` sets updated_at to the current date and time.
- `updateOne()` updates only one matching document.


**Update Many and Set**
```MongoDB shell
db.products.updateMany(
  { category: "laptop" },
  [{ $set: { price: { $multiply: ["$price", 0.9] } } }, { $set: { updated_at: "$$NOW" } }]
);
```
- `db.products.updateMany()` updates all documents that match the filter.
- `{ category: "laptop" }` filters for products where the category is `"laptop"`.
- `$set` updates or creates a field.
- `$multiply: ["$price", 0.9]` multiplies the existing `price` by `0.9`, effectively reducing the price by 10%.
- `$$NOW` represents the current date and time.
- `updated_at: "$$NOW"` updates the `updated_at` field to the current date and time.
- Since I am applying multiple update stages, I use an array `[...]` to contain them.


- `$nin` means "not in" — it excludes the specified values from the results.
- `db.products.find({$or: [{category: "laptop"}, {category: "smartphone"}]})` `$or` means "at least one condition must be true." In this example, it finds products where the `category` is either `"laptop"` or `"smartphone"`.
- `db.products.find({category: {$not: {$in: ["smartphone", "laptop"]}}})` `$not` means "not" — it excludes values that match the condition.
- `$eq` means equal.
- `.sort(1)` — `1` means ascending, while `-1` means descending.
- `db.products.find().sort({name: 1})` — `1` means ascending, while `-1` means descending.
- `db.products.find().sort({category: 1, price: -1})` — sorts the category in ascending order, and within each category, sorts the price from expensive to cheap.
- `.limit(3)` means limiting the results and showing only 3 items.
- `db.products.find().limit(3)` — limits the results and shows only 3 items.
- `.skip(3)` - skips the first 3 results. For example, if the results are 1, 2, 3, 4, 5, it skips 1, 2, 3 and starts from 4.
- `db.products.find().limit(3).skip(3)` — skips the first 3 results, then shows the next 3 results.
- `db.products.aggregate([])` returns all documents, similar to `find()`. `aggregate()` expects the pipeline as an array: `[]`. The array contains the stages you want MongoDB to execute.
- `db.products.aggregate([{$group: {_id: null, count: {$sum: 1}}}])` groups all products together and counts them by adding `1` for each document.
- A string field in `$group` means you can group products by that field and get each unique value. For example: `{ $group: { _id: "$stock" } }` Groups products by the stock field and gives you each unique stock value.
- `$sum: 1` = count things.
- `$regex` = matches text patterns in data. It is similar to searching for text.
- `as` can be used to give MongoDB results a temporary field name, similar to a variable.
- `$project: { _id: 1 }` → shows `_id`. Other fields are hidden automatically.
 - `1` = include the field.
 - `0` = exclude the field.
 - You generally don't need to write `0` for every other field when you're using inclusion.
- `$group: {}` → groups documents based on a specified `_id` expression and can calculate things like `$sum`, `$avg`, `$count`, etc.
- `$match: {}` → filters documents that match the specified conditions.
- `$lookup` → combines documents from another collection based on matching fields. It's roughly similar to a SQL `JOIN`.
- `$unwind: {}` → deconstructs an array field so that each array element becomes a separate document. It's not specifically for one-to-one relationships. It's commonly useful when you use `$lookup` and want to turn the resulting array into individual documents.
- `$multiply: ["$stock", "$price"]` → multiplies the values of `stock` and `price`. The `$` before a field name means "use the value from this document's field."


### Docker

**Running MongoDB in Docker**
```bash
docker run --name my-mongo `
  -e MONGO_INITDB_ROOT_USERNAME=root `
  -e MONGO_INITDB_ROOT_PASSWORD=asdffdsa `
  -p 27017:27017 `
  -v "$(pwd)/data/mongo:/data/db" `
  -d mongo:7
```
- `--name my-mongo` gives the container a friendly name to refer to later.
- `-e MONGO_INITDB_ROOT_USERNAME=root` sets the MongoDB root user's username.
- `-e MONGO_INITDB_ROOT_PASSWORD=asdffdsa` sets the MongoDB root user's password.
- `-p 27017:27017 maps port 27017` on the host machine to port 27017 inside the container.
- `-v "$(pwd)/data/mongo:/data/db"` mounts the local data/mongo directory to MongoDB's data directory inside the container, allowing the data to persist.
- `-d` runs the container in detached mode, meaning it runs in the background.
- `mongo:7` specifies the MongoDB Docker image and version 7 to run.


**Heading 2**
```bash
 <!-- code here -->
```
- Description

## Tools
- MongoDB — A document-oriented NoSQL database. It has both free and paid offerings.
- MongoDB Compass — MongoDB's official graphical user interface for working with MongoDB databases. It allows you to explore collections, documents, indexes, and other database information visually.

## My Confusion & Understanding

-Confusion:Example note

Understanding:Example note

-Confusion:Example note

Understanding:Example note