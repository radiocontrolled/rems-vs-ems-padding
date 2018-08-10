# REMs vs EMs
EMs and REMs is are both flexible / rezisable. This spike compares their use as units for spacing. 

## REMs
The REM unit represents a size relative to the root element (e.g., the `font-size` of `<html>`). Combined with the root element's font-size, a REM represents the root element's initial value. 

### Advantages
Spacing will be global across Simorgh

Ease of understanding: When we create a constant expressed in REMs (e.g. `export const GEL_SPACING = '0.5rem'`) that value, or values based of of that value, stay constant, which adds simplicity from a developer perspective.

```
// assumes the root font size is 16px, which is a common browser default

export const GEL_SPACING = '0.5rem'; // 8px
export const GEL_SPACING_DBL = GEL_SPACING * 2; // 16px 
export const GEL_SPACING_QUAD = GEL_SPACING * 4; // 32px
```

REMs offer the (seeming) easiest transition from our current code base's use of pixels for padding.

### Disadvantages
REMs are not supported in IE8: https://caniuse.com/#search=REMs

<hr/>

## EMs
"Represents the calculated font-size of the element. If used on the font-size property itself, it represents the inherited font-size of the element."(MDN)

### Advantages
Allows for more modularity of components, because spacing will be relative to local font size. 

### Disadvantages
Potential complexity of understanding due to nesting components, depending on how font size is implemented. It's harder to immediately understand what the current font size is that the EM is relative to: 
```
    <style>
        .parent {
            font-size: 16px;
        }

        h1 {
            font-size: 2em;
        }

        .child {
            font-size: 0.75em; /* 12px */
            padding-bottom: 1em; /* 12px - confusing! because it's relative to the current font-size, 
            0.5em, which is 12px. */
        }

    </style>

    <div class="parent">
        <h1>I am a heading and I should be 32px</h1>
        <div class="child">
            I am the child and I should be 12px
        </div>
    </div>

```

## a11y
* REMs and EMs are resisable. Both are established for use in production.
* Regardless of the unit chosen, we must set a default font-size in a resisable unit, i.e., `font-size: 100%` on the `html` element; supported user agents will allow text resizing (which will have a knock-on effect for padding/margin resizing). Setting a default font size in a resisable unit partially satisfies http://www.bbc.co.uk/guidelines/futuremedia/accessibility/html/resize-zoom.shtml; there isn't a standard per se for padding and margins.

## Further reading: 
<ul>
    <li>https://developer.mozilla.org/en-US/docs/Web/CSS/length</li>
    <li>https://engageinteractive.co.uk/blog/em-vs-rem-vs-px</li>
    <li>https://zellwk.com/blog/rem-vs-em/</li>
</ul>



