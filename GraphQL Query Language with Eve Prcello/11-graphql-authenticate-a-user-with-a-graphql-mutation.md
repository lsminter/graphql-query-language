Now that an account has been created, we can login. Find login in the mutations in the schema tab and write that out in the query document with our `username` and `password`.

```query
mutation {
  logIn(username: "ep123" password: "pass") {

  }
}
```

The logIn mutation returns whats called a `logInPayload`. This returns both the customer details and their token. We use the token to check if a user is authorized or not. So lets go ahead and grab their name and their token. 

```query
mutation {
  logIn(username: "ep123" password: "pass") {
    name
  }
  token
}
```
 
When you hit play, you will see the username as well as the token. 

```json
{
  "data": {
    "logIn": {
      "customer": {
        "name": "Eve Porcello"
      },
      "token": 
      "user token"
    }
  }
}
```

To authorize a user, in the bottom left, click on `HTTP HEADERS`, create an object, add in `Authorization`, `Bearer`, then the token. 

```json
{
  "Authorization": "Bearer user token"
}
```

Now with that finished, we can send queries that are for authorized users only. We will send the query `me` which is just going to send info about myself. 

```query
query {
  me {

  }
}

mutation {
  logIn(username: "ep123" password: "pass") {
    name
  }
  token
}
```

The `me` query returns customer details for anyone thats logged in. We will name our query `Me` as well as name the mutation `LogIn`. Lastly add `name` as a field on our `me` query. 

```query
query Me {
  me {
    name
  }
}

mutation LogIn {
  logIn(username: "ep123" password: "pass") {
    name
  }
  token
}
```

Now, we can send this query and we should see all of the details for ourselves, because we are a logged in user. Since we are logged in, we'll be able to check in and check out pets.