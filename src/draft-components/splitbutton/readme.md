# Disclosure

A [disclosure widget](https://w3c.github.io/aria-practices/#disclosure) is essentially a button that shows and hides and adjacent section. For the purposes of this component, that section is a non-modal popup, but the same pattern could be used as an accordion with very little alteration.

The section controlled by the button can contain any sort of content: static text, interactive controls, etc. When used to show and hide supplementary text, a disclosure widget is an excellent alternative to a [tooltip](../tooltip). In a usability study, participants preferred a disclosure widget over a tooltip, when both provided additional information about a text input in a standard form.

## Semantics

The two important parts of a disclosure widget are the use of `aria-expanded` on the button element, and ensuring that the shown/hidden section is immediately adjacent to the button in the DOM.

Here is example markup for a disclosure widget:

```html
<button aria-expanded="true/false" type="button">More information</button>
<div aria-label="popup name" role="group" tabindex="-1">
  <button type="button">
    <span class="visuallyHidden">close</span>
  </button>
  Popup content goes here
</div>
```

## Interaction

In this component, focus is sent to the popup element when it is opened, but that is not strictly necessary. If focus *is* sent to the popup, it should have an accessible name defined through `aria-label` or `aria-labelledby`.

The `Escape` key and the popup's close button both will close the popup and return focus to the disclosure button. If creating an accordion with this pattern rather than a non-modal dialog, implementing `Escape` and a close button are optional.

The popup **must** be immediately following the disclosure button in the DOM, or tab order and screen reader scan mode will both be unexpected. If for whatever reason a popup overlay cannot be immediately adjacent to the button that triggers it, it should be a [modal](../modal) instead.

## Stencil JS Component

The `<sui-disclosure>` web component supports the following properties and events:

<!-- Auto Generated Below -->


## Properties

| Property           | Attribute            | Description                                                                                               | Type                       | Default          |
| ------------------ | -------------------- | --------------------------------------------------------------------------------------------------------- | -------------------------- | ---------------- |
| `buttonId`         | `button-id`          | (Optional) pass a string to be the primary button id                                                      | `string`                   | `undefined`      |
| `customTabIndex`   | `custom-tab-index`   | Optionally override the component's tabindex                                                              | `0 \| 1`                   | `0`              |
| `inCompoundGroup`  | `in-compound-group`  | Set to true if the button is within a compound widget like a toolbar or menu (changes arrow key behavior) | `boolean`                  | `false`          |
| `isCompoundButton` | `is-compound-button` | Set the keyboard behavior of the splitbutton to be one tab/arrow stop or two (defaults to 2)              | `boolean`                  | `false`          |
| `menuButtonLabel`  | `menu-button-label`  | Set the accessible name for the button that opens the menu (recommended)                                  | `string`                   | `'More options'` |
| `menuItems`        | --                   | Array of menu actions                                                                                     | `any[]`                    | `[]`             |
| `pressed`          | `pressed`            | (Optional) set pressed to make the primary button into a toggle button                                    | `boolean`                  | `undefined`      |
| `renderMenuItem`   | --                   | Optional custom render function for menu items (defaults to the menuItem string)                          | `(menItem: any) => string` | `undefined`      |


## Events

| Event           | Description                                     | Type                |
| --------------- | ----------------------------------------------- | ------------------- |
| `menuAction`    | Emit a custom event when a menu item is clicked | `CustomEvent<void>` |
| `primaryAction` | Emit a custom event when a menu item is clicked | `CustomEvent<void>` |


----------------------------------------------

*Built with [StencilJS](https://stenciljs.com/)*
