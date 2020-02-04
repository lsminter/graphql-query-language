[Lesson 5](https://egghead.io/lessons/graphql-filter-a-graphql-query-result-using-arguments)

We have a list of all of the pets so far. Now we are going to be looking at how to filter through these to either see just the pets that are available or the pets that are checked out.

To do this, we add an `argument`. We add the preexisting argument on `totalPets` called `status` with the value of `AVAILABLE` on it. This displays that we have 20 pets available. 

```query
query {
  totalPets(status: AVAILABLE)
  allPets {
    name
    weight
    category
    photo {
      thumb
      full
    }
  }
}
```

If we change this to `CHECKEDOUT`, we'll see that the total checked out pets is five.

In the schema tab, you can search for `totalPets` and click on `PetStatus` argument to see the value options on it. 
