[Lesson 6](https://egghead.io/lessons/graphql-renaming-fields-with-graphql-aliases)

We currently have the query displaying the amount of pets that are checkout out. What if we want to see the amount of pets available and checkout out? If we do both, we get an error. 

```query
query {
  totalPets(status: AVAILABLE)
  totalPets(status: CHECKEDOUT)
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

The error message tells us that these two fields `conflict because they have differing arguments`. If you scroll down a little, it tells you exactly where the issue is occurring. Also if you look just to the left of our query, you can see a small red line indicating that something is wrong. 

Since we have a naming collision, a way we can fix this is adding an alias to the name. We do that by adding a name of our choosing, we will do `available` for the first and `checkedOut` for the second, and a semicolon afterwards. 

```query
query {
  available: totalPets(status: AVAILABLE)
  checkedOut: totalPets(status: CHECKEDOUT)
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

Hitting play will result in no errors now and will display our available and checked out animal amounts. 

You can add an alias to any field. If you wanted to add them to more nested fields, you can do so. 