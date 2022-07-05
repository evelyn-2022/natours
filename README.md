# My Notes

## Overview

This is the first project from the udemy course [Advanced CSS and Sass: Flexbox, Grid, Animations and More!](https://www.udemy.com/course/advanced-css-and-sass/). I will list what I learned here for future reference.

## What I learned

- Reseting and using inheritance to define font properties.
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

  `top` and `left`: the percentages are relative to the parent
  `transform`: the percentage is relative to **the element itself**
