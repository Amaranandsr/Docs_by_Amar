# **MongoDB**
>MongoDB is a source-available cross-platform document-oriented database program. Classified as a NoSQL database program, MongoDB uses JSON-like documents with optional schemas. MongoDB is developed by MongoDB Inc. and licensed under the Server Side Public License.


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

>Use the filter:
- {"state": "NY"}
- {"state": "NY", "city": "ALBANY"}


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
 	> **zips** is a collection name **find()** use as finding. 

- db.`<zips>`.find(`{"state": "NY"}`).count()
	> count the match query

- db.`<zips>`.find(`{"state": "NY", "city": "ALBANY"}`).pretty()
	> `pretty()` use for qurey formatted ease to read