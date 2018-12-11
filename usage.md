<img src="./images/logo-colored.svg" align="right" width="100"/>

# TypeScript Modules

Most Toba libraries are published to _npm_ in their original TypeScript format. This has a few simple implications.

https://twitter.com/ausginer/status/1072183853207425025

### Bundling

Nothing should need to change for bundlers (Webpack, Rollup, etc.) already configured to handle TypeScript. They will traverse the dependency graph and transform as usual.

### Jest

Normally everything in `node_modules` is excluded from transformation which means TypeScript there will cause syntax errors.

To run Jest tests with [ts-jest](https://github.com/kulshekhar/ts-jest) the `jest.config.js` file must include a `transformIgnorePattern` that causes `./node_modules/@toba` modules _to be_ transformed (the double negative can be a little confusing).

```js
module.exports = {
   ...
   transformIgnorePatterns: [
      "<rootDir>/node_modules/(?!@toba)"
   ];
}
```
