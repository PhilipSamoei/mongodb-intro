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
 ####  note 
  we use a 1 to include a field and 0 to exclude a field
  db.posts.find({}, {category: 0})
  we donot use 1 and 0 at the same time we get error