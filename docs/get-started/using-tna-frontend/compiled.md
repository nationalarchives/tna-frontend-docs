# Using the compiled TNA Frontend files

Each release (as of `v0.1.21-prerelease`) should contain a ZIP of the package.

Find the release you want on the `tna-frontend` [releases page](https://github.com/nationalarchives/tna-frontend/releases) and download the package from the "Assets" dropdown.

Including the `all.js` file in your page will add a `TNAFrontend` object to the `window`. You can initialise all the components with:

```js
TNAFrontend.initAll()
```
