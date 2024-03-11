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



# Advance update operations

Advanced update operations in MongoDB provide more flexibility and power when modifying documents in a collection. These operations allow you to perform complex updates, such as updating nested fields, using aggregation pipelines, or performing conditional updates. Here are some advanced update operations:

1. **Update with Aggregation Pipeline**:
   MongoDB 4.2 introduced the ability to use aggregation pipelines in update operations. This allows you to perform complex transformations on documents before updating them. You can use various aggregation stages such as `$match`, `$project`, `$addFields`, etc., to modify documents based on specific conditions or criteria.
   
   ```javascript
   db.collection.updateMany(
      <filter>,
      [
         { $set: { <newField>: <expression> } },
         { $unset: "<fieldToRemove>" },
         // Additional aggregation stages
      ]
   )
   ```

2. **Array Update Operators**:
   MongoDB provides operators like `$push`, `$addToSet`, `$pop`, `$pull`, etc., to update array fields efficiently. These operators allow you to add or remove elements from arrays within documents.
   
   ```javascript
   db.collection.updateOne(
      { _id: ObjectId("documentId") },
      { $push: { arrayField: <value> } }
   )
   ```

3. **Conditional Updates**:
   You can perform updates based on certain conditions using the `$cond` operator or other conditional operators like `$gt`, `$lt`, etc.
   
   ```javascript
   db.collection.updateMany(
      { conditionField: { $gt: threshold } },
      { $set: { status: "high" } }
   )
   ```

4. **Upsert**:
   Upsert is a combination of "update" and "insert". If the document does not exist, it inserts a new document; otherwise, it updates the existing document.
   
   ```javascript
   db.collection.updateOne(
      { _id: <id> },
      { $set: { field: value } },
      { upsert: true }
   )
   ```

5. **Array Filters**:
   When updating arrays in documents that contain multiple elements, you can specify conditions to match specific array elements using array filters.
   
   ```javascript
   db.collection.updateOne(
      { _id: <id>, "arrayField.id": <elementId> },
      { $set: { "arrayField.$.property": value } }
   )
   ```

These advanced update operations give you fine-grained control over how you modify documents in MongoDB collections, enabling you to perform complex updates efficiently.
