To be able to change data with GraphQL, we use a `mutation`. You can search for mutations in the schema tab. We have a mutation called `createAccount` that we are going to write out. 

We start by writing out `mutation` like we would `query` and use the name of the mutation, `createAccount`. It takes an input that we need to figure out. If we search in the schema tab again, scroll down to the input, we find out that `createAccount` is a wrapper around `name`, `username` and `password`. 

Every time an account is created, those are going to need to be provided. 

Here we are going to use the input. Without it, we will have to send all of these variables one at a time. If we wrap them in the input, we can send them all at once. 

To use it, we have to pass it as a variable in the parameters of `mutation`. `$input: CreateAccountInput!`. To make something `non-nullable`, we use the `!` sign. 

```query
mutation ($input: CreateAccountInput!) {
  createAccount(input: $input) {}
}
```

On the bottom left, we will use that `QUERY VARIABLES` panel to pass in the variables. We are going to nest in an object, `name`, `username`, and `password`. Now that they are defined, we need to return something from the mutation. 

```json
{
  "input": {
    "name": "Eve Porcello",
    "username": "ep123",
    "password": "pass"
  }
}
```

This returns a customer object and all of the fields on that. Put this in our mutation, and when we click play, it'll return those values. 

```query
mutation ($input: CreateAccountInput!) {
  createAccount(input: $input) {
    username
    name
  }
}
```
