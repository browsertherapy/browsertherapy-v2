---
title:  "Code Challenge: Tissue Contrast Illusion"
date: '2020-06-02'
updated: '2022-07-19'
---
The goal of this exercise is to replicate the Tissue Contrast Illusion in the browser. We've broken the problem into logical steps and provided sample code if you get stuck. *But*, keep in mind there are many (and possibly better) ways to solve this problem.

<iframe width="560" height="315" src="https://www.youtube.com/embed/9zMDmtWzBN8" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

Source: [Curiosity Stream](https://curiositystream.com/video/1259/brightness-and-contrast)

## Prerequisites
This activity should be approachable for beginners but some understanding of the following technologies will be beneficial: [HTML basics](https://developer.mozilla.org/en-US/docs/Learn/Getting_started_with_the_web/HTML_basics), [CSS basics](https://developer.mozilla.org/en-US/docs/Learn/Getting_started_with_the_web/CSS_basics) and the [CSS box model](https://developer.mozilla.org/en-US/docs/Learn/CSS/Building_blocks/The_box_model).

**Sandbox environments**: [Codepen.io](https://www.codepen.io) is a handy tool (one of many) that helps you code directly in the browser.
<!-- {:.notice--info} -->

## Topics covered
The sample code (below) further incorporates the following concepts and technologies: [Flexbox](https://css-tricks.com/snippets/css/a-guide-to-flexbox/), [viewport units](https://www.youtube.com/watch?v=_sgF8I-Q1Gs), [linear gradients](https://css-tricks.com/css3-gradients/), [transparent](https://css-tricks.com/almanac/properties/o/opacity/) [images](https://www.youtube.com/watch?v=33IinMVJf-M) and [absolute positioning](https://youtu.be/P6UgYq3J3Qs).

## Planning it out
Let's break down this exercise according to how elements need to overlap:

1. Two identical grey circles
2. **Under the circles**: split-colour background
3. **On top of the circles**: semi-transparent image.

These objectives are further broken down below. Remember: sample code is provided in case you get stuck but there are many ways to achieve the desired results.

### Sample code

**HTML Structure**
```html
<!-- The parent-child relationship of the `container` and `item`s is crucial to how Flexbox operates later. -->
<main class="container split-bg">
  <div class="item circle"></div>
  <div class="item circle"></div>
</main>
<!-- Placed at the end so that it sits on top when positioned later. -->
<div class="image"></div>
```

## Objective 1: Create and position two grey circles
<figure style="width: 500px" class="align-center">
  <img src="/images/posts/illusions/tissue-step-1.png" alt="Two grey patches">
  <figcaption>Two identical grey (50% black) patches, each centered in their half of the viewport (i.e. the viewable portion of a web page).</figcaption>
</figure> 

### Sample code

**Two grey circles**

```css
.circle {
  /* make it square */
  width: 30vmin;
  height: 30vmin;

  /* make it visible */
  background: grey;

  /* make it circular */
  border-radius: 50%;
}
```

**Coming from print?**: Check out this excellent video by Jen Simmons: [Designing for a Viewport](https://www.youtube.com/watch?v=QY3lTBZnJmE).
<!-- {:.notice--info} -->

**Pro tip**: Viewport units are amazing for global layout but try `em/rem` units for smaller page elements such as [cards](https://www.google.com/search?q=ux+card+pattern)).
<!-- {:.notice--info} -->

**Each circle, centred in their half of the viewport**

```css
.container {
  /* change default behaviour of `margin: auto` below */
  display: flex;

  /* explicitly set height to viewport; `margin: auto` needs room to work */
  height: 100vh;
}

.item {
  /* equally distribute extra horizontal/vertical space among flex items; block elements only do this for `margin-left` and `margin-right` */
  margin: auto;
}
```

**Getting fancy**: Check out the [Complete Guide to Flexbox](https://css-tricks.com/snippets/css/a-guide-to-flexbox/) for more ways to control your items with properties like `justify-content` and `align-items`.
<!-- {:.notice--info} -->

**Pro tip**: Flexbox is very handy for laying out [navigation menus](https://www.google.com/search?q=flexbox+navbar), [hero sections](https://www.google.com/search?q=flexbox+hero+sections) and [cards](https://www.google.com/search?q=flexbox+cards).
<!-- {:.notice--info} -->

## Objective 2: Add a split-colour background
<figure style="width: 500px" class="align-center">
  <img src="/images/posts/illusions/tissue-step-2.png" alt="Two grey patches">
  <figcaption>Two identical grey patches on a split-colour (very light and very dark) background. Notice the left circle appears slightly darker than the one on the right.</figcaption>
</figure> 

### Sample code

**Add a split-colour background**

```css
.split-bg {
  /* note: the final `background` declaration overrides the others,
  which are included for clarity but can safely be ignored */

  /* basic gradient; default gradient line direction: bottom to top (0deg)  */
  background: linear-gradient(white, black);

  /* change default direction: left to right (90deg) */
  background: linear-gradient(90deg, white, black);

  /* hide gradient area by adding identical colour stops */
  background: linear-gradient(90deg, white 50%, black 50%);
}
```

**Creative text effects**: [Mandy Michael](https://www.youtube.com/watch?v=lKRdfw4xcGo) uses this gradient technique in many of [her](https://codepen.io/mandymichael/pen/mNPvKo) [amazing](https://codepen.io/mandymichael/pen/MpqJMa) [designs](https://codepen.io/mandymichael/pen/peZgxW).
<!-- {:.notice--info} -->

## Objective 3: Overlap viewport with a semi-transparent image
<figure style="width: 500px" class="align-center">
  <img src="/images/posts/illusions/tissue-step-3.png" alt="Two grey patches">
  <figcaption>Ovelapping a semi-transparent image over top of the viewport enhances the effect of the illusion.</figcaption>
</figure> 

### Sample code
**Add a viewport-sized CSS image**

```css
.image {
  /* explicitly set element size to viewport */
  width: 100vw;
  height: 100vh;
  
  /* add full-size, centered background image to element */
  background-image: url('https://picsum.photos/500/500');
  background-size: cover;
  background-position: center;
}
```

**Alternate Solution**: Another valid option is to use an HTML image using an `img` element with the `object-fit` property.
<!-- {:.notice--info} -->

**Overlap the image**

```css
.image {
  /* create a new block formatting context and enable `top` and `left` */
  position: absolute;

  /* explicitly move top-left corner of image to top-left corner of <body> */
  top: 0;
  left: 0;
}
```

**Extra Points**: Absolute positioning is the classic method. Try using a newer technique: [explicit item placement with CSS Grid](https://youtu.be/EashgVqboWo). Each have their advantages depending on your situation.
<!-- {:.notice--info} -->

**Make the image semi-transparent**

```css
.image {
  /* set element opacity to 50% */
  opacity: 0.5;
}
```
**More Transparency**: `opacity` isn't the only way to create transparency in CSS. Gradients accept `transparent` as a colour keyword and you can add an alpha channel to `rgb()` or `hsl()` when defining a colour.
<!-- {:.notice--info} -->

## Cleaning things up with resets
A "reset" is CSS we add to change default browser behaviour to either:

1. make our projects more consistent across browsers, or 
2. be lazy because we're tired of setting the same parameters for every project. 

For example, you might currently see an irritating horizontal (and/or vertical) scroll bar in your browser window while working through this exercise. This is because most browsers add a default margin to their body tag. When we set the `width` and `height` of an element to fill the viewport, this `margin` is added to the final size of the page (hence, a scroll bar).

Below are two resets that most professional developers will use in every project (there are many more).

### Sample code

**Reset default margins**

```css
body {
  /* remove pesky scroll bars */
  margin: 0;
}
```

**Reset default `box-sizing`**

```css
* {
  /* make size calculations take 'padding' and 'border' into account */
  box-sizing: border-box;
}
```
**Optional**: `box-sizing` doesn't apply to the sample code as written but elements with added `padding` and `border` might benefit from this handy reset.
<!-- {:.notice--info} -->

**Pro tip**: Many professional developers will use a reset library such as [normalize.css](https://necolas.github.io/normalize.css/) to ensure consistent results with their projects.
<!-- {:.notice--info} -->

## Mobile Considerations
Sure, this illusion seems to work on the laptop but what if you want to text a link to your mom? Try adding a media query that declares the following CSS when the viewport is in the portrait orientation:

1. Place the circles vertically so one is above the other;
2. Change the gradient line direction to run from top to bottom.

### Sample code

**Add support for portrait orientation**

```css
@media (orientation: portrait) {
  /* Apply these styles when the screen is in 'portrait' orientation */
  .container {
    /* place circles in an up/down orientation */
    flex-direction: column;
    
    /* change the direction of the split-colour background to match the new direction */
    background: linear-gradient(180deg, white 50%, black 50%);
  }
}
```
**One nail, two hammers**: Using `display: grid` instead of `flex-direction: column` produces the same results. Why? Because CSS.
<!-- {:.notice--info} -->

## Final Demo


<p class="codepen" data-height="300" data-default-tab="html,result" data-slug-hash="MWKaode" data-user="browsertherapy" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/browsertherapy/pen/MWKaode">
  Exercise Spoilers: Tissue Contrast Illusion</a> by Tony Grimes (<a href="https://codepen.io/browsertherapy">@browsertherapy</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>