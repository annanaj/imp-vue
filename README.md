# Just a Vue playground to test things

* Vue 3
* Vite
* Vite Router for routing
* Vite Dev Tools
* Vitest for unit tests
* Cypress for e2e testing
* Eslint and Prettier to watch and format


## Project Setup

```sh
yarn install
```

### Compile and Hot-Reload for Development

```sh
yarn dev
```

### Compile and Minify for Production

```sh
yarn build
```

### Run Unit Tests with [Vitest](https://vitest.dev/)

```sh
yarn test:unit
```

### Run End-to-End Tests with [Cypress](https://www.cypress.io/)

```sh
yarn test:e2e:dev
```

This runs the end-to-end tests against the Vite development server.
It is much faster than the production build.

But it's still recommended to test the production build with `test:e2e` before deploying (e.g. in CI environments):

```sh
yarn build
yarn run test:e2e
```

### Lint with [ESLint](https://eslint.org/)

```sh
yarn lint
```
