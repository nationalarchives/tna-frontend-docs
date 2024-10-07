# Setup

## CSS

Link the `nationalarchives/all.css` file in your project through the HTML.

This includes all the styles for things like components, typography and the grid system.

### Font Awesome

Optionally, you can include the `nationalarchives/font-awesome.css` file which enables you to use the free [Font Awesome icons](https://fontawesome.com/search?o=r&m=free) in your service.

## JavaScript

Including the `nationalarchives/all.js` file in your HTML will add a `TNAFrontend` object to the `window`. You can then initialise all the components with:

```js
// Initialise all the components
window.TNAFrontend.initAll()
```

### Analytics

If you require analytics, use `nationalarchives/all+analytics.js` in place of `nationalarchives/all.js` which includes extra support for tracking. See [analytics](./analytics.md) for more information.

## Other includes

Make sure to import the stylesheets from Typekit and Google Fonts to enable the use of Supria Sans, Open Sans and Roboto Mono:

```html
<link rel="preconnect" href="https://use.typekit.net">
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link rel="stylesheet" href="https://use.typekit.net/kaq6qqh.css">
<link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=Open+Sans:wght@400..700&family=Roboto+Mono:wght@400..500&display=swap">
```

### Favicon

TNA Frontend includes a favicon. To use it, copy the [nationalarchives/assets/images/favicon.ico](https://github.com/nationalarchives/tna-frontend/blob/main/src/nationalarchives/assets/images/favicon.ico) file into your static assets and include it in the HTML with:

```html
<link rel="shortcut icon" sizes="16x16 32x32 48x48" href="/static/assets/images/favicon.ico" type="image/x-icon">
```
