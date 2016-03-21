# Find size of document

To find out the size of a document in MongoDB you can use the `Object.bsonsize()` function which will display the document size in bytes, you can use it like so:

```javascript
Object.bsonsize(db.users.find({"name": "Owen"}))
```