# Adding a new component

1. Create a new directory in `src/nationalarchives/components`
1. Create an `_index.scss`, `[myComponent].scss`, `fixtures.json`, `macro-options.json`, `macro.njk`, `template.njk` and a `[myComponent].stories.js` in the directory using other components as a guide
1. Add the component SCSS to `src/nationalarchives/components/_all.scss`
1. Update `tasks/test-package.js` to check for the files as part of the CI - `...componentFiles("myComponent")`
1. Set the macro in `macro.njk` to be `tnaMyComponent` where "MyComponent" is the name of your component
1. Add the component import and macro to the prototype kit test in `.github/workflows/ci.yml`

## Files

- `_index.scss` - Simply includes `@use "myComponent";` so we can include this directory within SASS and have it reference the styles in `[myComponent].scss`
- `[myComponent].scss` - this file gets built as a standalone file as well as being included in all styles and is where you can add your [BEM](https://getbem.com/) SCSS styles for the component
- `fixtures.json` - these are snapshots of the rendered component's HTML in different scenarios which can be used by other implementations to test against
- `macro-options.json` - the options for the component which are rendered in the Design System as well as being copied in to the Storybook controls
- `macro.njk` - the Nunjucks macro easily allows us to include components in the prototype kit and other applications such as the Design System
- `template.njk` - this is the HTML for the component, written in [Nunjucks](https://mozilla.github.io/nunjucks/)
- `[myComponent].stories.js` - the stories that get rendered to Storybook

## If you need JavaScript

1. Create a `[myComponent].mjs` file in the component directory
1. Ensure the top level element in your component has the attribute `data-module="tna-my-component"`
1. Import and initialise your component as part of the `initAll` function in `src/nationalarchives/all.mjs`
1. Update the check in `tasks/test-package.js` to add the JavaScript class to check for
1. If your component uses JavaScript, ensure you add interaction tests using `@storybook/testing-library`
