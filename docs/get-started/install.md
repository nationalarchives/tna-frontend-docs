# Installing TNA Frontend

## npm

Install the frontend package from NPM with:

```sh
npm install @nationalarchives/frontend
```

## Compiled files

Each release (as of `v0.1.21-prerelease`) should contain a ZIP of the package.

Find the release you want on the `tna-frontend` [releases page](https://github.com/nationalarchives/tna-frontend/releases) and download the package from the "Assets" dropdown.

## CDN

The `@nationalarchives/frontend` package is available on [jsdelivr.com](https://www.jsdelivr.com/package/npm/@nationalarchives/frontend).

While you can use the CSS and JavaScript from there, the font files which includes the icon font will have to be hosted from your web application.

As a result, **if you require icons, using a CDN like jsdelivr.com is not the preferred method** for using the `tna-frontend` library.

Include the CSS in the `<head>` element of your page:

```html
<link
  rel="stylesheet"
  href="https://cdn.jsdelivr.net/npm/@nationalarchives/frontend@0.2.15/nationalarchives/all.css"
  integrity="sha256-WVAh+/5fHHcNqyOWkvwD52cXAg/ATlYdsNke+YvVbwQ="
  crossorigin="anonymous"
/>
```

Add the JavaScript to the end of your page just before your closing `</body>` tag:

```html
<script
  src="https://cdn.jsdelivr.net/npm/@nationalarchives/frontend@0.2.15/nationalarchives/all.js"
  integrity="sha256-D5Cf2TU0KX3FYuuPI1O3oAcKxPgS9QUcKWpIhd5fEOI="
  crossorigin="anonymous"
></script>
```

For more guidance, read [using CDNs from the TNA Engineering Handbook](https://nationalarchives.github.io/engineering-handbook/third-party/cdn/).
