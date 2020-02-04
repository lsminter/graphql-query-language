Now we are going to make it so that we can checkout a pet. The checkout mutation takes an ID of a pet to checkout. Let's look at the available pets to checkout. 

Lets query `allPets` with the status of `AVAILABLE`, return the `id`, `name` and `category`. 

```query
query {
  allPets(status:AVAILABLE) {
    id
    name
    category
  }
}
```

Now we choose which pet to checkout. Let's choose the stingray called Switchblade. 

To do that, we set `S-2` to id as well as the other details about the pet, `name`, as well as some details about the customer, `name`. 

```query
mutation Checkout {
  checkOut(id: "S-2") {
    pet {
      name
    }
    customer {
      name
    }
  }
}
```

  When I send the Checkout mutation, I should see the pet has been checked out, and I see the customer who has checked that pet out.

Sending that query, we see the pet name that has been checked out as well as the customer name. 

```json
{
  "data": {
    "checkOut": {
      "pet": {
        "name": "Switchblade"
      },
      "customer": {
        "name": "Eve Porcello:
      }
    }
  }
}
```
