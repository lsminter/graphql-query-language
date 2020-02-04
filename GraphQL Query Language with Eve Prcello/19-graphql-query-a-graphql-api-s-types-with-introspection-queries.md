We are going to look at how to see the available queries and types without having to use the schema tab.

We start by writing out the query for `__schema`, then getting the `types` for that schema, then getting the `name`, `kind`, and `description` for the type. 

```query
query {
  __schema {
    types {
      name
      kind
      description
    }
  }
}
```

Clicking play on this, shows us all of the different types. 

Now to write a query for the customer type. We query the `__type` with a `name` of `Customer`. Then for the `fields`, we just want the `name` and `description`.

```query
query Customer {
  __type(name: "Customer") { 
    fields {
      name
      description
    }
  }
}
```

Clicking play on that, we see the `username`, `name`, `dateCreated`, `currentPets`, and their `description`.

To figure out what available queries we have, we'll start by writing a query for `AvailableQueries`. We look at the `__schema`, the `queryType` for that schema, the `fields` for the queryType, and the `name` and `description` for those fields. 

```query
query AvailableQueries {
  __schema {
    queryType {
      fields {
        name
        description
      }
    }
  }
}
```

Now we see all of the totalPets, availablePets, checkedOutPets, all of the queries on this API when we click the play button. 

The last query to look at is the `Pet` interface. So we will write a query for `InterfaceTypes`, look at the `__type`,  and look for the `kind`, `name` and `description` of the pet. 

```query
query InterfaceTypes {
  __type(name: "Pet") {
    kind
    name
    description
  }
}
```

To see the different implementations of an interface, you use `possibleTypes`. Query for the `name`, `kind`, and `description`. 

```query
query Interfacetypes {
  __type(name: "Pet") {
    kind
    name
    description
    possibletypes {
      name
      kind
      description
    }
  }
}

This prints out all of that relevent information!