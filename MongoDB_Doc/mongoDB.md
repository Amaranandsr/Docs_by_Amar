<a href="https://www.typescriptlang.org/" target="_blank" rel="noreferrer"> <img src="https://raw.githubusercontent.com/Amaranandsr/amaranandsr/main/file/img/icon/MongoDB/MongoDB.svg" alt="MongoDB" width="220" /> </a>

> MongoDB is a source-available cross-platform document-oriented database program. Classified as a NoSQL database program, MongoDB uses JSON-like documents with optional schemas. MongoDB is developed by MongoDB Inc. and licensed under the Server Side Public License.

- Username

       m001-student

- Password

      m001-mongodb-basics

- clusterURI

      sandbox

<br>

## Import:

### JSON

**mongoimport**

     mongoimport --uri="mongodb+srv://<your username>:<your password>@<your clusterURI>.mongodb.net/sample_supplies" --drop sales.json

### BSON

**mongorestore**

    mongorestore --uri "mongodb+srv://<your username>:<your password>@<your cluster>.mongodb.net/sample_supplies"  --drop dump

<br>

## Export:

#### JSON

**mongoexport**

    mongoexport --uri="mongodb+srv://<your username>:<your password>@<your cluster>.mongodb.net/sample_supplies" --collection=sales --out=sales.json

#### BSON

**mongodump**

    mongodump --uri "mongodb+srv://<your username>:<your password>@<your cluster>.mongodb.net/sample_supplies"`

<br>

## Data Explorer

Namespace - The concatenation of the database name and collection name is called a namespace.

> Use the filter:

- {"state": "NY"}
- {"state": "NY", "city": "ALBANY"}

<br>

### ObjectId()

- "\_id" unique identifier for a document in a collection.

- "\_id" required in every MongoDB document.

- identical document can exist in the same collection as long as their _"\_id"_ value are different.

  > _ObjectId()_ is the default value for the "\_id" field unless otherwise specified.

<br>
## Find Commmand

**Connect to the Atlas cluster:**

    mongo "mongodb+srv://<username>:<password>@<clusterURI>.mongodb.net/admin"

- show dbs

  > show database lists

- use `<sample_training>`

  > **use** To indicate that we will now be working with the `'sample_training'`

- show collections

  > Show All the Collections

- db.`<zips>`.find(`{"state": "NY"}`)

  > **zips** is a collection name **find()** use as finding the qurey.

- db.`<zips>`.find(`{"state": "NY"}`).count()

  > count the match query

- db.`<zips>`.find(`{"state": "NY", "city": "ALBANY"}`).pretty()

  > `pretty()` use for qurey formatted ease to read

- db.`<zips>`.findOne( )

  > `findOne( )` use for get any random document from the collection

- db.`<zips>`.insert(`{"field1": "value1", "field2": "value2"}`)

  > `insert( )` use for add document in the collection

- db.`<zips>`.insert(`[{"field1": "value1"}, {"field1": "value1"}]`)

  > `insert([ ])` use for add multiple documents in the collection in a written sequence array but any error occur inserting process halt.

- db.`<zips>`.insert(`[{"field1": "value1"}, {"field1": "value1"}],{"ordered": "false"}`)

  > `insert([ ],{"ordered": "false"})` use for add multiple documents in the collection but any error occur to insert any document they move to next document to insert.

- db.`<zips>`.updateOne(`{ "zip": "12534" }, { "$set": { "pop": 17630 } }`)

  > `updateOne({ }, { "$Operators": { } } )` Update a single document in the `<zips>` collection where the zip field is equal to "12534" by setting the value of the "pop" field to 17630.

- db.`<zips>`.updateMany(`{ "city": "HUDSON" }, { "$inc": { "pop": 10 } }`)

  > `updateOne({ }, { "$Operators": { } } )` Update all documents in the `<zips>` collection where the city field is equal to "HUDSON" by adding 10 to the current value of the "pop" field.

- db.`<zips>`.deleteMany(`{ "test": 1 }`)

  > `deleteMany()` Delete all documents in the `<zips>` collection that have test field equal to 1

- db.`<zips>`.deleteOne(`{ "test": 3 }`)

  > `deleteOne()` Delete one documents in the `<zips>` collection that have test field equal to 3.

  > `drop()` delete the given collection

<br>

## Operators

### Fields

- `$inc` Increments the value of the field by the specified amount.
- `$set` Sets the value of a field in a document.
- `$currentDate` - Sets the value of a field to current date, either as a Date or a Timestamp.
- `$min` - Only updates the field if the specified value is less than the existing field value.
- `$max` - Only updates the field if the specified value is greater than the existing field value.
- `$mul` - Multiplies the value of the field by the specified amount.
- `$rename` - Renames a field.
- `$setOnInsert` - Sets the value of a field if an update results in an insert of a document. Has no effect on update operations that modify existing documents.
- `$unset` - Removes the specified field from a document.

### Operators

- `$` - Acts as a placeholder to update the first element that matches the query condition.
- `$[]` - Acts as a placeholder to update all elements in an array for the documents that match the query condition.
- `$[<identifier>]` - Acts as a placeholder to update all elements that match the arrayFilters condition for the documents that match the query condition.
- `$addToSet` - Adds elements to an array only if they do not already exist in the set.
- `$pop` - Removes the first or last item of an array.
- `$pull` - Removes all array elements that match a specified query.
- `$push` - Adds an item to an array.
- `$pullAll` - Removes all matching values from an array.

### Modifiers

- `$each` - Modifies the $push and $addToSet operators to append multiple items for array updates.
- `$position` - Modifies the $push operator to specify the position in the array to add elements.
- `$slice` - Modifies the $push operator to limit the size of updated arrays.
- `$sort` - Modifies the $push operator to reorder documents stored in an array.

### Bitwise

- `$bit` - Performs bitwise AND, OR, and XOR updates of integer values.

<br>

## Query Operators:

### Comparison Operators

> **Syntex :**
> { "`<field>`": { "`<Comparison Operator>`" : `<Value>` }}
> or
> find({ "`<field>`": { "`<Comparison Operator>`" : `<Value>` }})

- `$eq` - Equal to
- `$ne` - Note Equal to
- `$gt` - Greater Than
- `$lt` - Less Than
- `$gte` - Greater Than or Equal to
- `$lte` - Less Than or Equal to

### logic Operators

> **Syntex :**
> { "`<logic Operators>`" : `[{"field1": "value1"}, {"field2": "value2"}]` }
> in logic syntax array is used.

- `$and` - **Match all** specified query clauses.
- `$or` - **At least one** of the query clauses.
- `$nor` - **Fail to match** both query clauses.

> **Syntex :**
> { "`<logic Operators>`" : `[{"field1": "value1"}]` }
> in not logic syntax array is not necessary.

- `$not` - **Negates** the query requirement
