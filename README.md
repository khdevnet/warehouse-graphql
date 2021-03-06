# Warehouse GraphQL
**GraphQL API** endpoint as a standalone (micro)service, backing up web front-ends and/or mobile apps requests.
It will be used for internal purposes and in future for external clients to share oor services.

## Tech Stack

* [Docker][docker], [Node.js][node], [Yarn][yarn], [TypeScript][typescript] — core platform and dev tools
* [Express][express], [cors][cors] etc. — common HTTP-server features
* [GraphQL.js][gqljs], [DataLoader][loader], [validator][validator] — [GraphQL][gql] schema and API endpoint

## Directory Layout

```bash
.
├── /dist/                      # The compiled output (via TypeScript)
├── /src/                       # Node.js application source files
│   ├── /schema/                # GraphQL schema type definitions
│   ├── /server.ts              # Node.js server (entry point)
├── /types/                       # TypeScript type definitions
├── package.json                # List of project dependencies
```


## Prerequisites

* [VS Code][code] editor (preferred) + [Project Snippets][vcsnippets],
  [EditorConfig][vceditconfig], TSLint, Typescript.
  plug-ins.
  
## Getting Started

Just clone the repo and run `docker-compose up`:

```bash
git clone https://github.com/khdevnet/warehouse-graphql
cd example-api                  # Change current directory to the newly created one
docker-compose up               # Launch Docker containers with the Node.js API app running inside
```

The API server must become available at [http://localhost:8080/graphql](http://localhost:8080/graphql).

Once the Docker container named `api` is started, the Docker engine executes `node tools/run.js`
command that installs Node.js dependencies, migrates database schema to the latest version,
compiles Node.js app from source files (see [`src`](./src)) and launches it with "live reload"
on port `8080`.

## Testing

```bash
yarn lint                       # Find problematic patterns in code
yarn check                      # Check source code for type errors
yarn docker-test                # Run unit tests once inside a Docker container
yarn docker-test-watch          # Run unit tests in watch mode inside a Docker container
```

For more information visit http://facebook.github.io/jest/


## Debugging

In order to run the app with [V8 inspector][v8debug] enabled, simply replace `node tools/run.js`
with `node --inspect=0.0.0.0:9229 tools/run.js` in either [`docker-compose.yml`](docker-compose.yml)
file or, even better, in `docker-compose.override.yml`. Then restart the app (`docker-compose up`) and
[attach your debugger][vsdebug] to `127.0.0.1:9230` (see [`.vscode/launch.json`](./.vscode/launch.json))

## Related Projects

* [GraphQL.js](https://github.com/graphql/graphql-js) — The JavaScript reference implementation for [GraphQL](http://graphql.org/)
* [DataLoader](https://github.com/facebook/dataloader) — Batching and caching for GraphQL data access layer
* [Membership Database](https://github.com/membership/membership.db) — SQL schema boilerplate for user accounts, profiles, roles, and auth claims

## Warehouse Navigation
* [Home](https://github.com/khdevnet/warehouse)
* [Goals](https://github.com/khdevnet/warehouse/blob/master/README.md#goals)
* [Features](https://github.com/khdevnet/warehouse#features)
* [Development](https://github.com/khdevnet/warehouse/blob/master/README.md#development)
* [User Documentation](https://github.com/khdevnet/warehouse/blob/master/README.md#user-documentation)

[node]: https://nodejs.org
[js]: https://developer.mozilla.org/docs/Web/JavaScript
[gql]: http://graphql.org/
[gqljs]: https://github.com/graphql/graphql-js
[gqlrelay]: https://github.com/graphql/graphql-relay-js
[yarn]: https://yarnpkg.com
[express]: http://expressjs.com/
[session]: https://github.com/expressjs/session
[flash]: https://github.com/expressjs/flash
[cors]: https://github.com/expressjs/cors
[do]: https://m.do.co/c/eef302dbae9f
[code]: https://code.visualstudio.com/
[vcsnippets]: https://marketplace.visualstudio.com/items?itemName=rebornix.project-snippets
[vceditconfig]: https://marketplace.visualstudio.com/items?itemName=EditorConfig.EditorConfig
[vceslint]: https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint
[docker]: https://www.docker.com/community-edition
[compose]: https://docs.docker.com/compose/
[v8debug]: https://chromedevtools.github.io/debugger-protocol-viewer/v8/
[vsdebug]: https://code.visualstudio.com/Docs/editor/debugging
[passport]: http://passportjs.org/
[redis]: https://redis.io/
[loader]: https://github.com/facebook/dataloader
[validator]: https://github.com/chriso/validator.js
[mailer]: https://nodemailer.com/
[hbs]: http://handlebarsjs.com/
[typescript]: https://github.com/Microsoft/TypeScript
