We are now going to look at two queries that we haven't touched on yet, `familyPets` and `exoticPets`. 

Clicking on familyPets in the schema, we see that it returns a list of family pets, either dog or cat. 

We are also going to look at `union`. Unions return a list of multiple types. 

Lets create that query for `familyPets` and have `__typename` as a field. It will return us a list of `"Cat"` and `"Dog"`.

```query
query {
  familyPets {
    __typename
  }
}
```

Trying to query for the name of one of these pets, we get an error. It recommends us to inline fragment instead. 

We do that with `... on Cat`, then we can add `name` and `sleepAmount` as fields to that. This returns us our animal name and how much they sleep. 

```query
query {
  familyPets {
    __typename
    ... on Cat {
      name
      sleepAmount
    }
  }
}
```

We can do the same with dogs with we want to get their name and either or not they are good by doing another inline fragment. 

```query
query {
  familyPets {
    __typename
    ... on Cat {
      name
      sleepAmount
    }
    ... on Dog {
      name
      good
    }
  }
}
```