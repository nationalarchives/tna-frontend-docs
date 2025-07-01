# Accessibility

## Accessibility acceptance criteria

For now, we are mirroring the accessibility acceptance criteria from GOV.UK:

https://github.com/alphagov/govuk-frontend/blob/main/docs/contributing/test-components-using-accessibility-acceptance-criteria.md

## Accessibility issues you should not need to fix

Sometimes automated accessibility testers will raise issues with some of the TNA Frontend components. This is a list of the known issues raised:

### Colour contrast ratio thresholds

#### Header

In Storybook, the AXE testing plugin raises the error:

> Element's background color could not be determined because it is overlapped by another element

This is in reference to the "Menu" text in the expand/contract button shown on mobile devices.

Text text itself is visually hidden and so the contrast of the text cannot be verified.

#### Hero caption icons

In Storybook, the AXE testing plugin raises the error:

> Element's background color could not be determined because it is overlapped by another element

This is most likely due to the fact that in the "i" icon, there is the text "Image caption" and we visually hide everything after the first letter.

The full text is available for screen readers but visually we only need the "i" icon so the contrast of the rest of the text cannot be verified.

#### Pagination ellipses

In Storybook, the AXE testing plugin raises the error:

> Element content contains only non-text characters

The testing tool cannot detect the colour contrast between the background and non-text characters and the ellipses used in the pagination component are classed as non-text.

This is not a failure because the ellipses don't have to be readable. They are there to show that there are "missing" pages in the list and so are only presentational.
