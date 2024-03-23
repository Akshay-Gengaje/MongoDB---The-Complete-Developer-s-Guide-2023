In MongoDB, indexing is crucial for improving the performance of database queries. Indexes are data structures that store a small portion of the collection’s data set in an easy-to-traverse form. They are similar to the indexes found in books, which help you find information quickly without reading through the entire book.

To create an index in MongoDB, you typically use the `createIndex()` method. Here's a basic example:

```javascript
db.collection.createIndex({ field: 1 });
```

In this example:
- `db` is the database object.
- `collection` is the name of the collection in which you want to create an index.
- `field` is the field in the documents of the collection by which you want to create an index.
- `1` specifies that the index should be created in ascending order. You can also use `-1` for descending order.

For example, if you have a collection called "users" and you want to create an index on the "email" field:

```javascript
db.users.createIndex({ email: 1 });
```

This will create an ascending index on the "email" field.

MongoDB supports various types of indexes, including single-field indexes, compound indexes (indexes on multiple fields), multikey indexes (indexes on arrays), text indexes (for text search), geospatial indexes (for geospatial queries), and more.

Remember that while indexes can improve query performance, they also consume additional disk space and can impact write performance during updates. So, it's essential to create indexes judiciously based on your application's specific requirements and usage patterns. Additionally, MongoDB's query planner can use indexes efficiently only if queries are properly formulated to use them.