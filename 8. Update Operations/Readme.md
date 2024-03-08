In MongoDB, the update operation is used to modify existing documents in a collection. There are several ways to update documents in MongoDB, and the choice depends on the specific requirements of your application. Here are some common methods:

1. **updateOne()**: This method updates a single document that matches the specified filter.
   
   ```javascript
   db.collection.updateOne(
       <filter>,
       <update>,
       {
           <options>
       }
   )
   ```

2. **updateMany()**: This method updates all documents that match the specified filter.
   
   ```javascript
   db.collection.updateMany(
       <filter>,
       <update>,
       {
           <options>
       }
   )
   ```

3. **replaceOne()**: This method replaces a single document that matches the specified filter with the specified replacement document.
   
   ```javascript
   db.collection.replaceOne(
       <filter>,
       <replacement>,
       {
           <options>
       }
   )
   ```

In the above methods:

- `<filter>`: A document that specifies the selection criteria for the update. It uses the same query syntax as the `find()` method.
- `<update>` or `<replacement>`: Specifies the modifications to apply to the selected document(s).
- `<options>`: Optional parameters such as `upsert`, `arrayFilters`, `collation`, etc., depending on the method used.

Here's an example of updating a document using `updateOne()`:

```javascript
db.inventory.updateOne(
   { item: "mouse" },
   {
     $set: { price: 15.99 },
     $currentDate: { lastModified: true }
   }
)
```

This query will update the first document in the `inventory` collection where the `item` field is `"mouse"`, setting the `price` field to `15.99` and adding the `lastModified` field with the current date.

Remember to handle updates carefully, especially when dealing with large datasets or in a distributed environment to ensure consistency and avoid unintended consequences.
