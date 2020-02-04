Now that we can checkout pets, we need to be able to check them back in. There is a mutation in the schema called CheckIn that will take the id of the pet. 

Keep in mind that you need your auth token. Let's `checkIn` the pet we checked out, `S-2`. This mutation returns something called `checkout`. We find out what that is in the schema tab. 

```query
mutation CheckIn {
  checkIn(id: "S-2") {

  }
}
```

Checkout returns a `pet`, `checkOutDate`, `checkInDate`, and a `late` boolean. Let's get those four things. 

```query
mutation CheckIn {
  checkIn(id: "S-2") {
    pet {
      name
    }
    checkOutDate
    checkInDate
    late
  }
}
```

When you click play, you should see all four of those fields for this pet. 

```json
{
  "data": {
    "checkIn": {
      "pet": {
        "name": "Switchblade"
      },
      "checkOutDate": "2019-05-26T00:30:35.088Z",
      "checkInDate": "2019-05-26T00:50:48.378Z",
      "late": true
    }
  }
}
```

Now that we have checked out and in a pet, we can look at that data on `allCustomers`. All customers returns us `username` as well as the `checkoutHistory` for those users. On `checkoutHistory`, we will want to add the field of `pet` as well as `id` and `name` of the pet. 

```query
query {
  allCustomers {
    username
    checkoutHistory {
      pet {
        id
        name
      }
    }
  }
}
```

Now this will return us all of the info that we need. 