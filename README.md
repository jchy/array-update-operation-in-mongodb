# array-update-operation-in-mongodb
Array operations in mongo DB

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
