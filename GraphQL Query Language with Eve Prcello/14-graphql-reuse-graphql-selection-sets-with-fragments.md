We start with a query for `allPet` and filter by `category` of `RABBIT` and a `status` of `AVAILABLE`. 

On that, we will grab `name`, `weight`, `category`, and `status`.

```query
query {
  allPets(category: RABBIT, status: AVAILABLE) {
    name
    weight
    category
    status
  }
}
```

Now we are going to make it so that we don't have to type these fields out every time we want to use them. We start by making a `fragment` called `PetDetails`. PetDetails is going to be a fragment on a certain type. This is going to be for `Pet`.

```query
fragment PetDetails on Pet {}
```

We copy over those fields into the fragment and push the `PetDetails` into the query by using the spread syntax. 

```query
query {
  allPets(category: RABBIT, status: AVAILABLE) {
    ...PetDetails
  }
}

fragment PetDetails on Pet {
  name
  weight
  category
  status
}
```

Clicking play, we still see everything printed out as it was before. 

  00:54 Now, we can also adjust the fragment to add additional fields. If I wanted to grab the photo as well as the thumbnail, we can see that the thumbnail for the photo is being returned.

We can add other fields as well, such as the thumbnail for the pet photo. 

```query
fragment PetDetails on Pet {
  name
  weight
  category
  status
  photo {
    thumb
  }
}
```

  Let's add onto this query a little bit and add petByID.

  01:08 We're going to look for the pet C-1, and here, we can reuse PetDetails inside of the query so that we don't have to retype them. There we go, we get all of those fields for that pet. You can also add additional fields alongside your fragment.

  01:24 Let's add inCareOf, name, and username.

Let's add onto our query with `petById`. Let's look for the pet `C-1` and add in `PetDetails` again. We can also add in additional fields with the fragment. Let's add `inCareOf`, `name`, and `username`. 

```query
query {
  petById(id: "C-1") {
    ...PetDetails
    inCareOf {
      name
      username
    }
  }
  allPets(category: RABBIT, status: AVAILABLE) {
    ...PetDetails
  }
}
```

  We should see the person who has checked out this pet. Since we're having so much fun with fragments, we can create a fragment for CustomerDetails. We're going to specify that these fields come from the customer type, and we can add name and username from inCareOf.

This prints out everything we would expect. Now we can create a fragment for `CustomerDetails` as well. We will add in `name` and `username`. 

```query
query {
  petById(id: "C-1") {
    ...PetDetails
    inCareOf {
      ...CustomerDetails
    }
  }
  allPets(category: RABBIT, status: AVAILABLE) {
    ...PetDetails
  }
}

fragment CustomerDetails on Customer {
  name
  username
}
```

Everything prints out as we would expect it to. 