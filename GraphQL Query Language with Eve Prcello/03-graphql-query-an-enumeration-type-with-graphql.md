[Lesson 3](https://egghead.io/lessons/graphql-query-an-enumeration-type-with-graphql)

We want to get more information about our animals. To do that, we can hit `control`+`space` and this will bring up all of the fields that are available. 


Let's add `category` to our query which will return what type of animal our pet is. 

```query
query {
  allPets {
    name
    weight
    category
  }
  totalPets
}
```

```json
{
  "name": "Biscuit",
  "weight": 10.2,
  "category": "CAT"
}
```

GraphQL is a query language for your API, but it's also a type system for your API.

The GraphQL spec describes a schema definition language, which we'll use to define all of the different queries and all of the different types that are available on this API. If you click the `schema` tab, you can take a look at this schema.

If you click on `allPets` in the schema tab, it'll show you all the different fields you can call on `allPets`. This is where we got our `category` field from where our types of pets are listed, `CAT`, `DOG`, `RABBIT`, and `STINGRAY`. 

In the query side of the browser, you can hover over a field and hold `command`. If you then click on the field, it will pop up in the schema with that field definition. 
