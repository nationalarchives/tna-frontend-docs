# Analytics

TNA Frontend comes with an analytics library.

The library is set up to track basic interactions from lots of the components.

There is support for Google Analytics 4 but you can extend the event listener library with your own suite if you wish.

## Setup

### Compiled files

1. Include the `analytics.js` file that comes with TNA Frontend - this will set up a `TNAFrontendAnalytics` object in the `window`
1. Instantiate the GA4 class with `const analytics = new window.TNAFrontendAnalytics.GA4("my-id")` where `"my-id"` is the ID of your Google Analytics property
1. Ensure your analytics instantiation is done AFTER the initialisation of the TNA Frontend components (`TNAFrontend.initAll()`)

### Source files

1. Import the GA4 library with `import { GA4 } from "@nationalarchives/frontend/nationalarchives/analytics.mjs";`
1. Instantiate the GA4 class with `const analytics = new GA4("my-id")` where `"my-id"` is the ID of your Google Analytics property

### Working with cookies

[TODO]

## Adding custom events

[TODO]

## Static page properties

[TODO]

## Delaying instantiation

[TODO]
