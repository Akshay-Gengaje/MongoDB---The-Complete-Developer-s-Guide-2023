## Delete Operations -

In MongoDB, there are several methods to perform delete operations on documents in a collection:

1. **deleteOne():** This method deletes a single document that matches the specified filter. If multiple documents match the filter, only the first one encountered is deleted.

```javascript
db.collection.deleteOne({ /* filter criteria */ });
```

2. **deleteMany():** This method deletes all documents that match the specified filter.

```javascript
db.collection.deleteMany({ /* filter criteria */ });
```

3. **remove():** Although `remove()` method is deprecated, it still works in MongoDB. It's similar to `deleteOne()` but can also delete multiple documents if the `justOne` option is set to false. It's recommended to use `deleteOne()` or `deleteMany()` instead.

```javascript
db.collection.remove({ /* filter criteria */ });
```

Remember to exercise caution when performing delete operations, as they can't be undone. Always ensure your filter criteria are accurate to avoid unintended data loss.



# Dropping collections and database -

In MongoDB, you can drop a database and a collection using the following methods:

1. **Drop a Database:**

```javascript
db.dropDatabase();
```

This command will drop the current database that you are connected to. It deletes the entire database, including all of its collections.

2. **Drop a Collection:**

```javascript
db.collection.drop();
```

This command will drop a specific collection within the current database. Replace `collection` with the name of the collection you want to drop.

Remember, dropping a database or collection is irreversible and will permanently delete all data within them. Make sure to use these commands with caution and ensure that you have appropriate backups in place if needed.
