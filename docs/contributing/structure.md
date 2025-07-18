# Structure

The layers of the TNA frontend SCSS library is built as:

1. [Variables](#variables)
1. [Tools](#tools)
1. [Libraries](#libraries)/[Utilities](#utilities)
1. [Components](#components)
1. [Overrides](#overrides)

## Variables

TNA frontend variables are defined in `src/nationalarchives/variables`.

Lots of variables can be modified but some are fixed, such as our brand colours.

An example fixed variable is `$relative-1rem-px` where we set the value of `1rem` to `16px` which makes it easier to define widths as a function of `1rem` as we mostly work on a 4px grid:

| Pixels | REM         |
| ------ | ----------- |
| `1px`  | `0.0625rem` |
| `2px`  | `0.125rem`  |
| `4px`  | `0.25rem`   |
| `8px`  | `0.5rem`    |
| `16px` | `1rem`      |
| `32px` | `2rem`      |
| `64px` | `4rem`      |

An example of a variable that can be modified is `$body-font-size-px` which we set to `18px` by default. This font size might not be right for all services so we have allowed it to be modified.

## Tools

The tools provided are reusable `@mixin` and `@function` blocks to make writing styles easier. They are defined in `src/nationalarchives/tools`.

Tools rely directly on variables and can be used throughout the frontend library.

As an exmaple, `colour-font()` will apply a font colour in a way that should work for all browsers and takes into consideration the light/dark theme used.

## Libraries

The libraries in `src/nationalarchives/lib` are a mix of third party libraries as well as some TNA ones.

They can join up tools to make larger, more useful elements.

## Utilities

The utilities in `src/nationalarchives/utilities` are some global styles that aren't associated with a specific component.

This layer is where we define some general purpose elements such as:

- The `tna-template` and `tna-template__body` elements
- Headings and heading groups
- Lists (`<ul>`, `<ol>` and `<dl>`)
- Chips
- Columns
- Forms and form elements
- Tables

These elements all adhere to the [BEM methodology](https://getbem.com/).

There are also some classless elements that are styled at this level:

- `<p>` elements
- Inline `<strong>` and `<small>` elements
- `<a>` elements
- Media elements (`<img>`, `<svg>`, `<picture>`, `<video>` and `<canvas>`)
- `<hr>` elements

Utilities should not implement any `!important` rules.

## Components

The most prominent layer of styling, the components in `src/nationalarchives/components` should use the tools already defined.

Components shouldn't use variables directly. They shouldn't use static values for colour unless the colour of that component will never change, for example the message component which is always yellow.

Some components may use utilities such as headings. Where these styles have already been defined, they should not be redefined. The heading in a cookie banner should use the existing `tna-heading` and `tna-heading--m` styles that already exist rather than implimenting its own.

Components should not implement any `!important` rules. There are exceptions such as the skip link that needs to be visually hidden in a way that it is still available for someone navigating a site with a keyboard.

Components should not care about the context or layout within which they are used. As an example, a breadcrumb _could_ be placed within a card or a footer element although in reality we wouldn't allow this.

## Overrides

Overrides start with `tna-!--` and can only be used in HTML classes. They have `!important` rules.

Examples of overrides are:

- Spacing (margin, padding etc.)
- No focus style (`.tna-!--no-focus-style`) for items such as the target element of a skip link
- Visibly hidden content (used to add extra descriptions which appear for screenreaders only)
