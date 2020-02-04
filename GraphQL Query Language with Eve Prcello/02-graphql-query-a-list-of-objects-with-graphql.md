[Lesson 2](https://egghead.io/lessons/graphql-query-a-list-of-objects-with-graphql)

To add onto our query from the previous lesson, we are going to add in the `allPets` query to get a list of all of our pets. Inside of the curly braces for that, we add the `name` and `weight` for each of the pets. 

```
query {
  allPets{
    name
    weight
  }
  totalPets
}
```


  00:18 I'll see that allPets returns an array of pets with name and weight for each of them.

After clicking the play button, it will return an array of all the pets name and weight in JSON again. 

```json
{
  "data": {
    "allPets": [
      {
        "name": "Biscuit",
        "weight": 10.2
      },
      ...
    ]
  }
}
```

You can collapse the `allPets` field and see `totalPets` is still getting displayed. 

Everything that is wrapped in curly braces is called a collection set. Each bit of data requested is called a field. You can also add in comments by using a `#`. 

```query
query {
  # Adding a comment
  allPets{
    name
    weight
  }
  totalPets
}
```

If you change one of the fields to be a comment, you will not get that field returned. 

```query
query {
  # Adding a comment
  allPets{
    # name
    weight
  }
  totalPets
}
```