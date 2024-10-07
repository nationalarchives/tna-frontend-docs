# Configure

## CSS

To build your own CSS using TNA Frontend, you can create your own SCSS file and import only what is needed.

Use the `@use` command to import variables and modify them before you import the main `all` styles.

Nearly all the variables in the [TNA Frontend variables directory](https://github.com/nationalarchives/tna-frontend/tree/main/src/nationalarchives/variables) can be modified although modifications should be applied with caution.

```sass
/* OPTIONAL: Override any variables */
@use "node_modules/@nationalarchives/frontend/nationalarchives/variables/assets" with (
  $tna-font-path: "/MY_CUSTOM_FONTS_PATH",
  $fa-font-path: "/MY_CUSTOM_FONT_AWESOME_PATH"
);

/* Include all the styles */
@use "node_modules/@nationalarchives/frontend/nationalarchives/all";
```

> If you build the SCSS with `sass --load-path=node_modules ...` then you can remove the `node_modules/` prefix from the paths above, instead simply importing your modules with `@nationalarchives/frontend/nationalarchives/...`.

## JavaScript

You can use TNA Frontend in your own JavaScript build process by importing either the uncompiled `all.mjs` or `all+analytics.mjs` files:

```js
import { initAll } from "@nationalarchives/frontend/nationalarchives/all.mjs";

initAll();
```

## Other imports

The format of the Google Fonts stylesheet could change based on your SASS settings. The format is:

`https://fonts.googleapis.com/css2?family=#{$main-font-family-name}:wght@#{$main-font-weight}..#{$main-font-weight-bold}&family=#{$detail-font-family-name}:wght@#{$detail-font-weight}..#{$detail-font-weight-bold}&display=swap`
