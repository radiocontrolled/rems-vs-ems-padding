# REMs vs EMs
EMs and REMs is are both flexible / rezisable.


## REMs

The REM unit represents a size relative to the root element (e.g., the `font-size` of `<html>`). Combined with the root element's font-size, a REM represents the root element's initial value. 

### Advantages

#### Ease of understanding 
When we create a constant expressed in REMs (e.g. `export const GEL_SPACING = '0.5rem'`) that value, or values based of of that value, stay constant, which adds simplicity from a developer perspective.

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


### Disadvantages
In the case of an application like Simorgh that has a lot of nested components, implementing padding in EMs could be trickier in terms of making sure components don't compound padding inadvertantly.  

## Accessibility
With REMs and EMs, for a11y, we need to set font size as a percentage on the `<html>` element, e.g. "62.5% of 16px" for the "typical" browser font size (1)[https://engageinteractive.co.uk/blog/em-vs-rem-vs-px]

Further reading: 
https://developer.mozilla.org/en-US/docs/Web/CSS/length



