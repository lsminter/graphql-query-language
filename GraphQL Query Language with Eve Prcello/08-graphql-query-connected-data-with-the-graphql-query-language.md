There is another main type of this API that we haven't touched on yet and that's called `Customer`. 

Now we are going to write some queries that will connect the `Pet` type with the `Customer` type. We start with `petById`. 

  00:24 This is going to take in `id` as an argument. This is going to return Biscuit.

`petById` takes `"C-1"` as its value and we pass in the `name` property. 

```query
query {
  petById(id: "C-1") {
    name
  }
}
```

  There's another field on pet called `inCareOf`. `inCareOf` is going to return the customer who has checked out this pet. Biscuit has been checked out by this customer.

The other field on pet that we can use is `inCareOf`. This will return who has checked out this pet. If we do that and add `name` and `username` as properties on `inCareOf` we will see who checked out Biscuit.

```query
query {
  petById(id: "C-1") {
    name
    inCareOf {
      name
      username
    }
  }
}
```

returns

```json
{
  "data": {
    "name": "Biscuit",
    "inCareOf": {
      "name": "Shana Nelson",
      "username": "snelson"
    }
  }
}
```

To be able to see all of the customers we have, we are going to use `allCustomers`. We are going to use `name`, `username`, and `currentPets` with `name` as a field on that to be able to see all of our customers names, their usernames, and their current pet's names. 

```query
query {
  allCustomers {
    name username currentPets {
      name
    }
  }
  petById(id: "C-1") {
    name
    inCareOf {
      name
      username
    }
  }
}
```

That connection is made on the currentPets field. allCustomers returns a list of customers for each of those customer objects that are going to have a list of current pets that are checked out.

It could either be an empty array or return a list of the current pets they have checked out. 