[Lesson 4](https://egghead.io/lessons/graphql-send-a-nested-graphql-query)

Let's see if we can add a photo for each of our pets. 

Start by using the search bar at the top of the schema tab and searching for `Photo`. Clicking on that, we see that it has two fields for either full size image or thumb size image. 

  00:26 If I query photo, it gives me this error message that says, "Field photo of type photo must have a selection of subfields."

If we add in the `photo` field, we get an error: `Field photo of type photo must have a selection of subfields.`

Because `photo` is an object, I'm going to need to add another selection set here.

  00:38 This allows us to have some flexibility when we are sending a query. A photo may have more than one field associated with it. Then we can request just the fields that we want with our GraphQL query.

So if we add in `full` or `thumb` or both to our `photo` field, we get a link to our picture and no error message. 

```query
query {
  allPets {
    name
    weight
    category
    photo {
      thumb
      full
    }
  }
  totalPets
}
```