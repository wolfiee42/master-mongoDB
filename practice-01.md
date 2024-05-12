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