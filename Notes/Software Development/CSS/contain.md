#performance #css

https://css-tricks.com/almanac/properties/c/contain/
#### Paint

The `paint` containment value informs the browser that none of the descendants of the element will be painted outside of the border-box of the element. If a descendant element is positioned to have a portion of its bounding box to be clipped by the contained element’s `border-box` then that portion shall not be painted. If a descendant element is positioned fully outside the contained element’s `border-box` then it is not painted at all. This is similar to applying `overflow: hidden;` to the element, but without the benefits of skipping or reducing needed calculations.

### Layout
The `layout` containment value informs the browser that none of the element’s descendants affect other elements on the page, nor do those other elements have any effect on the descendants of the contained element.

# Size
The `size` containment value informs the browser that none of the descendants need to be considered when performing layout calculations for the page. The contained element must have `height` and `width` properties applied, or it will collapse to zero pixels square. Only the element itself needs to be considered for page layout calculations as descendants cannot influence the size of the element. The contained element’s descendants are completely skipped in such calculations; as if it had no descendants at all.
![[Screenshot 2023-08-08 at 5.03.55 PM.png]]
![[Screenshot 2023-08-08 at 5.05.50 PM.png]]
![[Screenshot 2023-08-08 at 5.07.25 PM.png]]
The **`contain`** [CSS](https://developer.mozilla.org/en-US/docs/Web/CSS) property indicates that an element and its contents are, as much as possible, independent from the rest of the document tree. Containment enables isolating a subsection of the DOM, providing performance benefits by limiting calculations of layout, style, paint, size, or any combination to a DOM subtree rather than the entire page. Containment can also be used to scope CSS counters and quotes.

```
/* Keyword values */
contain: none;
contain: strict;
contain: content;
contain: size;
contain: inline-size;
contain: layout;
contain: style;
contain: paint;

/* Multiple keywords */
contain: size paint;
contain: size layout paint;
contain: inline-size layout;

/* Global values */
contain: inherit;
contain: initial;
contain: revert;
contain: revert-layer;
contain: unset;
```