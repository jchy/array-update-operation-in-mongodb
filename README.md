# array-update-operation-in-mongodb
### Assignment: 5455
Array operations in mongo DB

PART : 1
1. push a new tag into a post
soln :~ 
```js
   db.posts.updateOne( { id: 1 }, { $push: { tags: "headphone" } })
```
2. push multiple tags into a post
soln :~ 
```js
   db.posts.updateOne( { id: 2 }, { $push: { tags: {$each : ["hello", "me","I"]} } })
```

3. pull and remove a particular tag
soln :~ 
```js
   db.posts.updateOne( { id: 2 }, { $pull: { tags: "I"} })
```
4. pull and remove an array of values use $in
soln :~ 
```js
   db.posts.updateOne( { id: 2 }, { $pull: { tags: {$in : ["me","life"]}}})
```

5. use $pop to remove first and last tag
soln :~ 
```js
   db.posts.updateOne( { id: 2 }, { $pop: { tags: 1}},{$pop : {tags :-1}})
```

6. use addToSet to add.5 tags
soln :~ 
```js
   db.posts.updateOne( { id:1}, {$addToSet: { tags : {$each : ["masai","tommy","alover","tom","som"]}}})
```
#### Part : 2

7. create a collection of users with high scores
soln :~ 
```js
   db.createCollection("user")
```
8. each user can have 3 high scores
```js
   db.user.insertOne({highScores: [24,23,21]})
```
9. it should be always in descending order
```js
  db.user.updateOne({_id: ObjectId("6207c472653233e0b6d72c16")}, { $push: { highScores: { $each: [12, 35, 2, 1], $sort: { highScores: -1 } } } })
```
10. add 5 new high scores, and maintain the order, and keep the limit of 3 scores
```js
  db.user.updateOne({_id: ObjectId("6207c472653233e0b6d72c16")}, { $push: { highScores : { $each : [ 99,100,98,97,96], $sort :-1,$slice : 3 }}})
```
11. remove multiple scores which are greater than x value
```js
  try { 
... db.user.deleteMany( { "highScores" : { $gt : 98}})}
... catch(e){ 
... print(e);
... }
```

