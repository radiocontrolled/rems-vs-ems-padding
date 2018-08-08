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
An EM represents a size relative to its parent element's font size. i.e. a calculated font-size.

### Advantages
Allows for more modularity of components, because spacing will be relative to local font size. 

### Disadvantages
In the case of an application like Simorgh that has a lot of nested components, implementing padding in EMs could be trickier in terms of making sure components don't compound or inherit padding inadvertantly.  

Less easy to understand: 
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
            padding-bottom: 1em; /* 12px - confusing! because it's relative to the current font-size, 0.5em, which is 12px. */
            background: lightblue;
        }

    </style>

    <div class="parent">
        <h1>I am a heading and I should be 32px</h1>
        <div class="child">
            I am the child and I should be 12px
        </div>
    </div>

```


Further reading: 
https://developer.mozilla.org/en-US/docs/Web/CSS/length
https://engageinteractive.co.uk/blog/em-vs-rem-vs-px
https://zellwk.com/blog/rem-vs-em/



