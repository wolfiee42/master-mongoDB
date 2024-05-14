# Mastering MongoDB Aggregation & Indexing

#### 1. Retrieve the count of individuals who are active (isActive: true) for each gender.

```
db.massiveData.aggregate([

    // stage-1
    { $match: { isActive: true } },

    // stage-2
    { $group: { _id: '$gender', count: { $sum: 1 } } },

])
```

#### 2. Retrieve the names and email addresses of individuals who are active (`isActive: true`) and have a favorite fruit of "banana".

```
db.massiveData.aggregate([

    // stage-1
    { $match: { isActive: true, favoriteFruit: 'banana' } },

    // stage-2
    { $project: { name: 1, email: 1 } }

])
```

#### 3. Find the average age of individuals for each favorite fruit, then sort the results in descending order of average age.

```
db.massiveData.aggregate([

    // stage-1
    {
        $group:
        {
            _id: '$favoriteFruit',
            AvgAge: { $avg: '$age' },
            count: { $sum: 1 }
        }
    },

    // stage-2
    { $sort: { AvgAge: -1 } }

])
```