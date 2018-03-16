# A Quick Example of Using GraphQL with MongoDB

## Intro

This example uses Express, MongoDB and GraphQL. Featuring queries, mutations, resolvers including support for nested queries in about 100 lines of code.

## Getting Started

Install, build and run:

```
yarn install
yarn run build
yarn start
```

## Behold the Beauty of GraphQL....

Visit http://localhost:3002/graphiql and play around with it.

### Add a post:

```
mutation {
  createPost(title:"hello", content:"world") {
    _id
    title
    content
  }
}
```

 ### Get a post:

```
query {
  posts {
    _id
    title
    content
  }
}
```

### Add a comment:

```
mutation {
  createComment(postId: "584ebf8bee8d98127efb080c", content: "I like the way you say hello world.") {
    _id
    postId
    content
  }
}
```
### Get all posts including comments:

```
query {
  posts {
    _id
    title
    content
    comments {
      _id
      postId
      content
    }
  }
}
```

and you should see something like:

```
{
  "data": {
    "posts": [
      {
        "_id": "584ebf8bee8d98127efb080c",
        "title": "hello",
        "content": "world",
        "comments": [
          {
            "_id": "584ec10eee8d98127efb080e",
            "postId": "584ebf8bee8d98127efb080c",
            "content": "I like the way you say hello world."
          }
        ]
      },
    ]
  }
}

```


Pretty swish aye? I knew you'd like it :)