# Using TNA Frontend with npm

Install the frontend package from NPM with:

```sh
npm install @nationalarchives/frontend
```

## CSS

From here, you have access to include the SCSS files from the package so you can compile the package yourself:

```css
/* OPTIONAL: Override any variables */
@use "node_modules/@nationalarchives/frontend/nationalarchives/variables/assets" with (
  $tna-font-path: "/MY_CUSTOM_FONTS_PATH",
  $fa-font-path: "/MY_CUSTOM_FONT_AWESOME_PATH"
);

@use "node_modules/@nationalarchives/frontend/nationalarchives/variables/grid" with (
  $largest-container-width: 90rem
);

@use "node_modules/@nationalarchives/frontend/nationalarchives/variables/typography" with (
  $body-font-size-px: 17
);

/* Include all the styles */
@use "node_modules/@nationalarchives/frontend/nationalarchives/all";
```

...or you can copy the compiled CSS files into your distribution as part of your build process:

- `node_modules/@nationalarchives/frontend/nationalarchives/all.css`
- `node_modules/@nationalarchives/frontend/nationalarchives/all.css.map`

> TIP:
>
> If you build the SCSS with `sass --load-path=node_modules ...` then you can remove the `node_modules/` prefix from the paths above, instead simply importing your modules with `@nationalarchives/frontend/nationalarchives/...`.

## JavaScript

```JavaScript
// Import all the JavaScript
import { initAll } from "@nationalarchives/frontend/nationalarchives/all.mjs";

// Initialise all the components
initAll();
```

...or you can copy any of the compiled JavaScript files into your distribution (see [using the compiled files](#using-the-compiled-files) from above):

- `node_modules/@nationalarchives/frontend/nationalarchives/all.js`
- `node_modules/@nationalarchives/frontend/nationalarchives/all.js.map`
