# commands

## show dbs
1.allows you to see all available databases with content
## use 
one can changeor create a new database by typing use the the name of the database you want
    use blog 
    
# CREATION OF COLLECTIONS
   1 db.createCollection("posts")
# INSERTION OF DOCUMENTS
    use of insertOne
    2  db.posts.insertOne(object)
# examples:
        db.posts.insertOne({
        title: "Post Title 1",
        body: "Body of post.",
        category: "News",
        likes: 1,
        tags: ["news", "events"],
        date: Date()
        })
## insertion of multiple documents
use of insertMany
    db.posts.insertMany([  
            {
                title: "Post Title 2",
                body: "Body of post.",
                category: "Event",
                likes: 2,
                tags: ["news", "events"],
                date: Date()
            },
            {
                title: "Post Title 3",
                body: "Body of post.",
                category: "Technology",
                likes: 3,
                tags: ["news", "events"],
                date: Date()
            },
            {
                title: "Post Title 4",
                body: "Body of post.",
                category: "Event",
                likes: 4,
                tags: ["news", "events"],
                date: Date()
            }
            ])
# FINDING DATA
    use find() to select data from a collection in the database 
    it accepts query selector
    and if left empty it will return all documents

    db.posts.find()


    use findOne() to select one document from a collection
    accept query selector left empty returns the first document it finds

    db.posts.findOne()

# QUERING OR FILTERING DATA
    To query or filter data we include query in our find() or findOne() methods

    db.posts.find({ category: "posts" })
### Projection 
    db.projects.find({},{_id: 1 ,title: "Project", description: "Project"})
 ##  note 
  we use a 1 to include a field and 0 to exclude a field
  db.posts.find({}, {category: 0})
  we donot use 1 and 0 at the same time we get error

  # Updating document 
    to update an existing document we use updateOne() method or updateMany() method
## updateOne method
    updates the first document that is found matching the query provided 
    db.posts.find( { title: "Post Title 1" } ) 
    to update  likes of the post we use $set opertor 
    db.posts.updateOne( { title: "Post Title 1" }, { $set: { likes: 2 } } ) 
    $upsert operator insert te document if it is not found

    db.posts.updateOne( 
  { title: "Post Title 5" }, 
  {
    $set: 
      {
        title: "Post Title 5",
        body: "Body of post.",
        category: "Event",
        likes: 5,
        tags: ["news", "events"],
        date: Date()
      }
  }, 
  { upsert: true }
)
# TO UPDATE  USE    updateMany()
    updateMany() method will update all the documents that match the query selector
    we will use $inc (increment) operator 

db.posts.updateMany({}, { $inc: { likes: 1 } })

similar to deleteMany() method  and deleteOne() method will delete all the documents that match the query selector
db.posts.deleteOne({ title: "Post Title 5" })
db.posts.deleteMany({ category: "Technology" })


# MongoDb query  operators
## Comparison operators
    The following operators can be used in queries to compare values:

                $eq: Values are equal
                $ne: Values are not equal
                $gt: Value is greater than another value
                $gte: Value is greater than or equal to another value
                $lt: Value is less than another value
                $lte: Value is less than or equal to another value
                $in: Value is matched within an array
# logical
    The following operators can logically compare multiple queries.

                $and: Returns documents where both queries match
                $or: Returns documents where either query matches
                $nor: Returns documents where both queries fail to match
                $not: Returns documents where the query does not match
# Evaluation 
            The following operators assist in evaluating documents.

            $regex: Allows the use of regular expressions when evaluating field values
            $text: Performs a text search
            $where: Uses a JavaScript expression to match document
# MongoDB update oprator
    There are many update operators that can be used during document updates.

            Fields
            The following operators can be used to update fields:

            $currentDate: Sets the field value to the current date
            $inc: Increments the field value
            $rename: Renames the field
            $set: Sets the value of a field
            $unset: Removes the field from the document
            Array
            The following operators assist with updating arrays.

            $addToSet: Adds distinct elements to an array
            $pop: Removes the first or last element of an array
            $pull: Removes all elements from an array that match the query
            $push: Adds an element to an array