[Lesson link](https://egghead.io/lessons/graphql-send-a-query-with-graphql-playground)


We use a specific [moonhighway](https://pet-library.moonhighway.com) repo that the instructor has previously set up. 

GraphQL has only one endpoint, so to send data, you have to write a query. 

To start writing a query, you'll click on the left box and type out: 

```js
query {
  totalPets
}
```

to get the total amount of pets in the library. 

When you click the play button, your data will be returned as JSON. The JSON will be formatted the same as the query and all of the files will be the same. 

```json
{
  "data": {
    "totalPets": 25
  }
}
```