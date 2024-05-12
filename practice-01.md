# In-Depth Exploration of MongoDB Queries

#### 1. Find all documents in the collection where the age is greater than 30, and only return the name and email fields.

```
 db.testing101
    .find({
        age: { $gt: 30 }
    })
    .project({ name: 1, email: 1 })
```

#### 2. Find documents where the favorite color is either "Maroon" or "Blue."

```
db.testing101
    .find({
        favoutiteColor: { $in: ['Maroon', 'Blue'] }
    })
    .project({ favoutiteColor: 1 })
```

#### 3. Find all documents where the skill is an empty array.

```
db.testing101
    .find({
        skills: { $size: 0 }
    })
    .project({ skills: 1 })
```

#### 4. Find documents where the person has skills in both "JavaScript" and "Java."

```
db.testing101.find({
    $and: [
        { 'skills.name': 'JAVASCRIPT' },
        { 'skills.name': 'JAVA' }
    ]
}).project({ skills: 1 })
```

#### 5. Add a new skill to the skills array for the document with the email "gloveitt18@com.com". The skill is

{"name": "Python"
,
"level": "Beginner"
,
"isLearning": true}

```
db.testing101.updateOne(
    { email: "gloveitt18@com.com" },
    {
        $addToSet: {
            skills: {
                "name": "Python"
                ,
                "level": "Beginner"
                ,
                "isLearning": true
            }
        }
    }
)
```

#### 6. Add a new language "Spanish" to the list of languages spoken by the person.

```
db.testing101.updateOne(
    { email: "gloveitt18@com.com" },
    {
        $addToSet: {
            language: {
                $each: ['Spanish']
            }
        }
    }
)
```

#### 7. Remove the skill with the name "Kotlin" from the skills array.

```
db.testing101.updateOne(
    { _id: new ObjectId('6406ad64fc13ae5a40000071') },
    {
        $pull: {
            skills: { name: 'KOTLIN' }
        }
    }
)
```
