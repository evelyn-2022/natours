# My Notes

## Overview

This is the first project from the udemy course [Advanced CSS and Sass: Flexbox, Grid, Animations and More!](https://www.udemy.com/course/advanced-css-and-sass/). I will list what I learned here for future reference.

## What I learned

Reseting and using inheritance to define font properties:

```css
/* Reset */
*,
*::after,
*::before {
  margin: 0;
  padding: 0;
  box-sizing: inherit;
}

/* The root font size is set in html */
html {
  font-size: 62.5%; /* 10/16 = 62.5% */
  /* Why use percentage instead of pixels: 
  By using pixels, we can override the browser font size that the user can manually change in the settings */
}

/* To make use of inheritance, we always define font-family in body, not in universal selector */
body {
  font-family: "Lato", sans-serif;
  font-weight: 400;
  line-height: 1.7;
  color: #777;
  padding: 3rem;
  box-sizing: border-box;
  /* We use rem instead of pixel values, 
  because instead of redefining all the values when screen size changes, 
  we only need to change root font size */
}
```

---

[`clip-path`](https://developer.mozilla.org/en-US/docs/Web/CSS/clip-path)
A useful website for creating clip-path: https://bennettfeely.com/clippy/

---

How to set an element to the absolute center of its parent element

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

---

`backface-visibility`: sometimes in animations, it might seem a bit shaky (like moving up a bit at the end), we can fix that by adding `backface-visibility:hidden` to the element.

---

🟡 Difference between `block` and `inline-block`:

- `display: block`:
  - takes entire width of the parent;
  - treated as though it were **text**, which in turn means most properties that usually apply to text would also apply to an inline-block These propertirs include `text-indent`, `text-align` and `vertical-align`, among others.
  - To center an inline element, we can't use `margin-inline: auto` on the element itself, instead, we should use `text-align: center` on its parent element.
- `display: inline-block`: wraps around its content

---

`::after` and `::before` pseudo elements:
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

---

`animation-fill-mode: backwards`
The animation will apply the values defined in the first relevant keyframe as soon as it is applied to the target, and retain this during the `animation-delay` period. The first relevant keyframe depends on the value of `animation-direction`.
| `animation-direction` | first relevant keyframe |
| ---- | ----|
|`normal` or `alternate`| 0% or from|
|`reverse` or `alternate-reverse`| 100% or to|

---

Stacking context:

Apart from z-index, an opacity value different from 1, a transform, a filter or other properties, will also create new stacking contexts. That's why sometimes, even with the z index set on a positioned element, the stacking order doesn't work as expected.

---

SCSS built-in color function:

```scss
$color-primary: #7ed56f;
.btn {
  background-color: darken($color-primary, 15%);
}
```

It also has `lighten` function which will make color lighter.

Passing argument into mixins:

```scss
@mixin style-link-text($color) {
  text-decoration: none;
  text-transform: uppercase;
  color: $color;
}
```

Functions:

```scss
@function divide ($a, $b) {
  return $a/$b;
}

nav{
  margin: divide(60, 2) * 1px;
}
```

Extends:

```scss
%btn-placeholder {
  text-align: center;
  display: inline-block;
  padding: 5px;
}

.btn-main {
  @extend %btn-placeholder;
  background-color: $color-primary;
}

.btn-hot {
  @extend %btn-placeholder;
  background-color: red;
}
```

Difference between `mixin` and `extend`: in the compiled code, `extend` copies the selector, while `mixin` copies the whole code block

```scss
// extend
.btn-main,
.btn-hot {
  text-align: center;
  display: inline-block;
  padding: 5px;
}

.btn-main {
  background-color: $color-primary;
}

.btn-hot {
  background-color: red;
}

// mixin
.btn-main {
  text-align: center;
  display: inline-block;
  padding: 5px;
  background-color: $color-primary;
}

.btn-hot {
  text-align: center;
  display: inline-block;
  padding: 5px;
  background-color: red;
}
```

We should only use `extend` if the rules we are extending are inherently and thematically related.
