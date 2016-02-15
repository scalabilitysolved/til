# Find documents that don't have a particular field

MongoDB can be great for quick development and having such a flexible (see non existent) schema.  As many benefits as it brings it also has a few pitfalls, mainly the fact that your schema is held in your code as opposed to being defined at the DB level.  Sometimes you have documents in a collection that don't have the same fields, the easiest way to find a document that is missing your field in question is the following:

```javascript
db.COLLECTION_NAME.find({FIELD_IN_QUESTION: null})
```

This query will return any documents where the field is _either_ null or not present in the document, you can append `.count()` like below to get an idea of how many documents are missing this field in any given collection

```javascript
db.COLLECTION_NAME.find({FIELD_IN_QUESTION: null}).count()
```