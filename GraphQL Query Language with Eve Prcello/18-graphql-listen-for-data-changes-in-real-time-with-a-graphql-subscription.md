The last operation type we are going to look at is GraphQL Subscription. Let's say we wanted to set up a real-time listener for anytime a pet is returned.

To do this first we need to login, checkout a pet, then be able to checkin a pet. 

```query
mutation {
  logIn(username: "ep123" password: "123") {
    customer {
      username
      name
    }
    token
  }
}
```

Click play on this so we can get the token and authorize the user. Add a Bearer and past in the token into the HTTP HEADERS. 

```
{
  "Authorization": "Bearer token"
}
```


Now we want to add in our subscription. Our query is going to be called `petReturned`. 

The `petReturned` subscription returns the `Checkout` object. This gives us access to `pet`, `checkoutDate`, `checkInDate`, and `late`. So we will add the `pet` query and `name`. 

```query
subscription {
  petReturned {
    pet {
      name
    }
  }
}
```

Now when we click play, we get text at the bottom saying `Listening ...` and a spinner in the middle of the tab. It's waiting and listening to any changes being made. 

Now we add a mutation and checkout a pet, immediately check back in that pet. 

```query
mutation {
  checkIn(id: "C-2")
  pet {
    name
  }
}
```

Swapping back to our subscription tab, we see the data for that checkedIn pet. 

```json
{
  "data": {
    "petReturned": {
      "pet": {
        "name": "Jungle"
      }
    }
  }
}
```