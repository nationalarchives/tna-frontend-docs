# Using TNA Frontend from a CDN

The `@nationalarchives/frontend` package is available on [jsdelivr.com](https://www.jsdelivr.com/package/npm/@nationalarchives/frontend).

While you can use the CSS and JavaScript from there, the font files which includes the icon font will have to be hosted from your web application.

As a result, **if you require icons, using a CDN like jsdelivr.com is not the preferred method** for using the `tna-frontend` library.

Include the CSS in the `<head>` element of your page:

```html
<link href="https://cdn.jsdelivr.net/npm/@nationalarchives/frontend@0.1.18-prerelease/nationalarchives/all.css" rel="stylesheet" integrity="sha384-6Egfw6aX1Jrwuf+APn+BMPswroudkIQ6StU095OPkNCKLEzj7ksWGmYxjend8P7g" crossorigin="anonymous">
```

Add the JavaScript to the end of your page just before your closing `</body>` tag:

```html
<script src="https://cdn.jsdelivr.net/npm/@nationalarchives/frontend@0.1.18-prerelease/nationalarchives/all.js" integrity="sha384-sBkiMlxl9svXopGxNSMVAdALjzyvh6sQHp+21PE3LGfTxAEbG4EIpK" crossorigin="anonymous"></script>
<script>
  // Initialise all TNA components
  window.TNAFrontend.initAll();
</script>
```

...or use the module syntax:

```
<script type="module">
  import { initAll } from "https://cdn.jsdelivr.net/npm/@nationalarchives/frontend@0.1.18-prerelease/nationalarchives/all.js";
  initAll();
</script>
```

For more guidance, read [using CDNs from the TNA Engineering Handbook](https://nationalarchives.github.io/engineering-handbook/third-party/cdn/).
