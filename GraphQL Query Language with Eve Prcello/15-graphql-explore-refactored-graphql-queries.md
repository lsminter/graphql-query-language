There have been some updates to our pet library. We start by making a query for `totalPets`. But we can make two more new queries, `availablePets` and `checkedOutPets`. We can access these values without having to use any filters or arguments. 

```query
query {
  totalPets
  availablePets
  checkedOutPets
}
```

There is another new query called `customersWithPets`. This returns a list of all the customers with pets checked out. 

```query
query {
  customersWithPets {

  }
  totalPets
  availablePets
  checkedOutPets
}
```

This refactor makes things much easier for us. We have access to all of the same data but don't have to use as much boilerplate to get it to work. 

```query
query {
  customersWithPets {
    username
    name
  }
  totalPets
  availablePets
  checkedOutPets
}
```