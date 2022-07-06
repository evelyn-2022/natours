# My Notes

## Overview

This is the first project from the udemy course [Advanced CSS and Sass: Flexbox, Grid, Animations and More!](https://www.udemy.com/course/advanced-css-and-sass/). I will list what I learned here for future reference.

## What I learned

- Reseting and using inheritance to define font properties:

```css
/* Reset */
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

/* To make use of inheritance, we always define font-family in body, not in universal selector */
body {
  font-family: "Lato", sans-serif;
  font-weight: 400;
  font-size: 16px;
  line-height: 1.7;
  color: #777;
  padding: 30px;
}
```

- [`clip-path`](https://developer.mozilla.org/en-US/docs/Web/CSS/clip-path)
  A useful website for creating clip-path: https://bennettfeely.com/clippy/
- How to set an element to the absolute center of its parent element

  ```css
  .parent-el {
    position: relative;
  }

  .child-el {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
  }
  ```

  - `top` and `left`: the percentages are relative to the parent
  - `transform`: the percentage is relative to **the element itself**

- `backface-visibility`: sometimes in animations, it might seem a bit shaky (like moving up a bit at the end), we can fix that by adding `backface-visibility:hidden` to the element.

- 🟡 Difference between `block` and `inline-block`:

  - `display: block`:
    - takes entire width of the parent;
    - treated as though it were **text**, which in turn means most properties that usually apply to text would also apply to an inline-block These propertirs include `text-indent`, `text-align` and `vertical-align`, among others.
    - To center an inline element, we can't use `margin-inline: auto`, instead, we should use `text-align: center`.
  - `display: inline-block`: wraps around its content

- `::after` and `::before` pseudo elements:
  `::after` creates a pseudo-element that is the **last child** of the selected element, `::before` the first child. They are inline by default.
  ```css
  .btn::after {
    content: "";
    display: inline-block;
    height: 100%;
    width: 100%;
    border-radius: 100px;
  }
  ```
  We need to specify the content of pseudo element, even when it's empty. Here, by setting height and width to 100%, we make it the same size as the selected element.
- `animation-fill-mode: backwards`
  The animation will apply the values defined in the first relevant keyframe as soon as it is applied to the target, and retain this during the `animation-delay` period. The first relevant keyframe depends on the value of `animation-direction`.
  | `animation-direction` | first relevant keyframe |
  | ---- | ----|
  |`normal` or `alternate`| 0% or from|
  |`reverse` or `alternate-reverse`| 100% or to|
