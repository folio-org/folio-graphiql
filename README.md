# folio-graphiql

Copyright (C) 2016-2018 The Open Library Foundation

This software is distributed under the terms of the Apache License,
Version 2.0. See the file "[LICENSE](LICENSE)" for more information.

----

A simple webapp that lets you authenticate to Okapi and use [GraphiQL](https://github.com/graphql/graphiql) to explore its GraphQL endpoint (provided by [mod-graphql](https://github.com/folio-org/mod-graphql)).

Built with [create-react-app](https://github.com/facebook/create-react-app), this is a typical React/Webpack app that requires `nodejs` and `yarn` (or `npm`, probably).

Before running, you must install dependencies:
```
yarn install
```

You can run it on `http://localhost:3000` (or elsewhere if you set an [environment variable](https://github.com/facebook/create-react-app/blob/master/packages/react-scripts/template/README.md#advanced-configuration)) with:
```
yarn start
```

Or output optimized files to `./build` that you can host on another server:
```
yarn build
```

If you would like to change the default Okapi URL in the login form or the text that first populates GraphiQL's query box, that is currently conspicuously hardcoded in [src/App.js](src/App.js).

## Using `folio-graphiql`

The GraphQL syntax can be a bit verbose and not as intuitive as one might hope. This is best demonstrated by examples.

To fetch information about a specific instance, set the GraphQL query to:
```
query ($id:String!)
{
  instance_storage_instances_SINGLE(instanceId: $id) {
    title
  }
}
```
And the query variables to
```
{
  "id": "69640328-788e-43fc-9c3c-af39e243f3b7"
}
```
When you press the play button, you should see something like:
```
{
  "data": {
    "instance_storage_instances_SINGLE": {
      "title": "ABA Journal"
    }
  }
}
```
