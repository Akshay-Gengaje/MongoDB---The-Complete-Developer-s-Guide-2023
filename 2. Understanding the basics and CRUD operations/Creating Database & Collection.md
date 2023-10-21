# Creating Database and Collection

In MongoDB, you can create a new database and collection using the MongoDB shell or a MongoDB driver in your programming language of choice. Here's how you can create a database and a collection in MongoDB:

### Using the MongoDB Shell:

1. **Start MongoDB**: Make sure your MongoDB server is running. You can start it by running the `mongod` command in your terminal.

2. **Access the MongoDB Shell**: Open a new terminal and run the `mongo` command to access the MongoDB shell.

3. **Create a Database**: To create a new database, you can use the `use` command. For example, to create a database named "mydatabase," run:

   ```javascript
   use mydatabase
   ```

   If the database doesn't exist, MongoDB will create it. However, the database won't appear in the list of databases until it contains at least one collection.

4. **Create a Collection**: To create a collection in the newly created database, you can use the `db.createCollection()` method. For example, to create a collection named "mycollection" in the "mydatabase" database, run:

   ```javascript
   db.createCollection("mycollection");
   ```

### Using a MongoDB Driver (e.g., Node.js):

If you are working with a programming language like Node.js and using the MongoDB driver, you can create a database and collection programmatically. Here's an example using Node.js and the `mongodb` driver:

```javascript
const MongoClient = require("mongodb").MongoClient;

const url = "mongodb://localhost:27017"; // Connection URL
const dbName = "mydatabase"; // Name of the database

MongoClient.connect(url, (err, client) => {
  if (err) {
    console.error("Error connecting to MongoDB:", err);
    return;
  }

  const db = client.db(dbName);

  // Create a collection
  db.createCollection("mycollection", (err, collection) => {
    if (err) {
      console.error("Error creating collection:", err);
      return;
    }

    console.log('Collection "mycollection" created.');

    // Close the connection
    client.close();
  });
});
```

Make sure to install the `mongodb` driver for Node.js using npm or yarn:

```
npm install mongodb
```

This code connects to MongoDB, creates a new database called "mydatabase," and then creates a collection named "mycollection" within that database.

Remember to replace the MongoDB connection URL and database/collection names with the appropriate values for your use case.
