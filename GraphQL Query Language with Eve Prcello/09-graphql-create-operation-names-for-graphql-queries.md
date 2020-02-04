GraphQL will allow us to write out these huge queries and in this one we are collecting data about customers and pets. But what we want to do is break this down into two separate queries, one for pets and the other for customers. 

```query
query {
  totalCustomers
  allCustomers {
    name
    username
    dataCreated
    checkoutHistory {
      pet {
        name
      }
      checkOutDate
      CheckInDate
      late
    }
  }
  availablePets: totalPets(status: AVAILABLE)
  checkedOutPets: totalPets(status: CHECKEDOUT)
  dogs: allPets(category: DOG, status: AVAILABLE) {
    name
    weight
    status
    category
    photo {
      full
      thumb
    }
  }
}
```

When we break this up into two queries, we have an issue. Both queries are unnamed. 

```query
query {
  availablePets: totalPets(status: AVAILABLE)
  checkedOutPets: totalPets(status: CHECKEDOUT)
  dogs: allPets(category: DOG, status: AVAILABLE) {
    name
    weight
    status
    category
    photo {
      full
      thumb
    }
  }
}

query {
  totalCustomers
  allCustomers {
    name
    username
    dataCreated
    checkoutHistory {
      pet {
        name
      }
      checkOutDate
      CheckInDate
      late
    }
  }
}
```

Clicking on one of these unnamed queries, it gives us, "This anonymous operation must be the only defined operation." If we have more than one query, we need to give each of them a name to not have them blank. 

  00:40 Right now, these are anonymous queries. Think of those like anonymous functions. We need to give them a name. I'll call the first one, "PetPage." I'll call the second one, "CustomerPage."

The first one we will name `"PetPage"` and the second name will be `"CustomerPage"`. 

```query
query PetPage {
  availablePets: totalPets(status: AVAILABLE)
  checkedOutPets: totalPets(status: CHECKEDOUT)
  dogs: allPets(category: DOG, status: AVAILABLE) {
    name
    weight
    status
    category
    photo {
      full
      thumb
    }
  }
}

query CustomerPage {
  totalCustomers
  allCustomers {
    name
    username
    dataCreated
    checkoutHistory {
      pet {
        name
      }
      checkOutDate
      CheckInDate
      late
    }
  }
}
```

Now a cool thing happens. When we click the Play button, we get a drop down menu where we can select which query we want to run, `PetPage` or `CustomerPage`. 
