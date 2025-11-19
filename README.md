# css-anchor-positioning

1. Tooltip (hover-centered tooltip)
2. Side Popover (popover to the right)
3. Dropdown Menu (menu anchored to button)
4. Badge Indicator (badge pinned to a card corner)
5. Floating Label (label anchored to input)


The CSS `anchor-name`, `position-anchor`, and `anchor()` functions used in this code may be behind a flag or experimental in many browsers.


**`anchor-name`**
Defines a named anchor point on an element. It's a custom property (like CSS variables) that marks an element as an anchor. Example: `anchor-name: --my-btn;` makes that element referenceable by other positioned elements.


**`position-anchor`**
Specifies which anchor an absolutely positioned element should be positioned relative to. It references the anchor by name. Example: `position-anchor: --my-btn;` tells the browser to use the `--my-btn` anchor as the reference point instead of the nearest positioned ancestor.


**`anchor()`**
A function that retrieves a coordinate value from the referenced anchor. It takes a keyword like `top`, `bottom`, `left`, `right`, or `center` to get that specific edge or midpoint of the anchor element. Examples:
- `anchor(top)` — the top edge of the anchor
- `anchor(center)` — the vertical or horizontal center (depending on context)
- `anchor(right)` — the right edge


**How they work together:**
```css
.button {
  anchor-name: --btn;  /* Mark this as an anchor */
}

.tooltip {
  position: absolute;
  position-anchor: --btn;  /* Reference the anchor */
  bottom: calc(anchor(top) - 12px);  /* Position 12px above the anchor's top */
  left: anchor(center);  /* Align with the anchor's horizontal center */
}
```

The key benefit: positioning is **decoupled from the DOM tree**. The tooltip doesn't need to be a child of the button or even nearby in the HTML—it can be anywhere and still position itself relative to the button.