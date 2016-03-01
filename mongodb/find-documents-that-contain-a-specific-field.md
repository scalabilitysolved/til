# Find documents that contain a specific field

Just as sometimes we want to find documents that are missing a field it can also be very useful to be able to find documents where a field does exist but we don't care about the particular value in MongoDB.  To achieve this we can run the following:

```javascript
db.collection.find({ "fieldToCheck" : { $exists : true, $ne : null } })
```