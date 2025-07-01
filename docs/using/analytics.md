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

## Adding custom events

Once an instance of `GA4` has been created you can add listeners for your own events with the `addListeners` method.

```js
import {
  GA4,
  helpers,
} from "@nationalarchives/frontend/nationalarchives/analytics.mjs";

const analytics = new GA4({ id: "GTM-ABCD1234" });

analytics.addListeners(
  // The selector for the group
  ".etna-article__sidebar",

  // The human-readable name of the group, used to create tna.event.name
  // e.g. [tna.sidebar...]
  "sidebar",

  // An array of event objects to add within the group
  [
    {
      // The eventName is used to create tna.event.name
      // e.g. [tna.sidebar.section.jump_to]
      eventName: "section.jump_to",

      // The element selector to add the listener to
      // (optional - if undefined then add a listener directly to the group element)
      targetElement: ".etna-article__sidebar-item",

      // The event to listen for, e.g. click, change, focus, resize, keyup
      // https://developer.mozilla.org/en-US/docs/Web/API/Element#events
      on: "click",

      // Optional custom data which can be used at a later date
      // Properties can be:
      // - a static value
      // - a valueGetters helper (https://github.com/nationalarchives/tna-frontend/blob/main/src/nationalarchives/lib/analytics-helpers.mjs#L56-L72)
      // - a function (some helper functions are provided)
      data: {
        // Static value
        foo: "bar",

        // A valueGetter helper
        value: helpers.valueGetters.text,

        // A custom function called with the parameters:
        // - $el: the element that the event was triggered on
        // - $scope: the main group element
        // - event: the raw JavaScript event
        // - index: the index of the element within the group (e.g. the fourth matched element)
        // - instance: the index of the matched group element
        state: ($el) => ($el.checkVisibility() ? "visible" : "hidden"),
      },

      // Data to add to the event as defined by the analytics team
      // Can be static values, valueGetters or functions as with the data property
      rootData: {
        data_component_name: "sidebar",
        data_link: helpers.valueGetters.text,
        data_link_type: "link",
        data_position: helpers.valueGetters.index,
        data_section: ($el) => helpers.getClosestHeading($el),
      },
    },
  ],

  // Optional rootEventName which will be used in place of the eventName of each event
  // e.g. [tna.sidebarEvent]
  "sidebarEvent",

  // Optional rootDefaultData which will be merged in to the rootData of each event
  // Replaced by any values in the rootData
  {
    data_component_name: "sidebar",
  },
);
```

### `valueGetters` helpers

- `text`: The text of the triggered element
- `html`: The HTML of the triggered element
- `value`: The value of the triggered element (e.g. for use with `<input>` elements)
- `index`: The index of the element within the group (e.g. the fourth matched element)
- `instance`: The index of the matched group element (e.g. the second matched group element)
- `checked`: Returns `checked` or `unchecked` based on the state of a checkbox element
- `expanded`: Returns `open` or `closed` based on the `aria-expanded` property of the element
- `closestHeading`: The closest previous heading (`<h1>` to `<h6>` or `.tna-heading-...`) to the element
- `xpath`: The XPath of the element

## Static page properties

You can add meta elements to the page in order to add static tracking data when the analytics are initialised.

The `name` attribute can either start with `tna.` or `tna_root:`.

```html
<!-- Add a custom property of tna.page.wagtail.type -->
<meta name="tna.page.wagtail.type" content="collections.ExplorerIndexPage" />

<!-- Add a page_type property to the root of the tracking data -->
<meta name="tna_root:page_type" content="collections.ExplorerIndexPage" />
```

You can see examples of these in the `dataLayer` property of the `window` object in [Explore the collection](https://www.nationalarchives.gov.uk/explore-the-collection/).

## Working with cookies

[TODO]

## Delaying instantiation

[TODO]
