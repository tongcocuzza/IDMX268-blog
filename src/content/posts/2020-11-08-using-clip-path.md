---
template: blog-post
title: Using clip-path
slug: /using-clip-path
date: 2020-11-08 10:56
description: using clip-path
featuredImage: /assets/krzysztof-maksimiuk-eicw5iuhpjg-unsplash.jpg
---
We can change the shape of images by using the `<clipPath>` SVG element or the `clip-path` CSS property.

”The [`clip-path`](https://developer.mozilla.org/en-US/docs/Web/CSS/clip-path) CSS property creates a clipping region that sets what part of an element should be shown. Parts that are inside the region are shown, while those outside are hidden.” 

“The [`<clipPath>`](https://developer.mozilla.org/en-US/docs/Web/SVG/Element/clipPath) SVG element defines a clipping path, to be used by the clip-path property.”

## Combining and Clipping

I cannot get over ***Jason Pamental***’s idea, which is a way to combine a relationship of text, image, and shape into a web design. Jason created a line of elliptical shape and it interacted with a masked background image and overlapping title text. I believe that it’s a great composition. So, I will combine his techniques to create my hero header by using both `<clipPath>` and `clip-path`.

## Let’s start

I followed along Jason’s steps by create two containers to the outer div is the full section and the inner div is for placing a background image. Then I set a CSS custom property so I can use the same value when clipping the image and the title.

```html
<body>
  <div class="diagonal__box">
    <div class="diagonal__box--background image"></div>
  </div>
</body>
```

```css
:root {
  --clip-shape: ellipse(210% 90% at 100% 0%);
  --text-color: #a7cc1d;
  --overlap-color: #fff;
}
```

## The ellipse() function

`ellipse(rx ry at cx cy);`
There are 2 shape radius parameters; rx for the length of the radius on the x-axis and ry for the y-axis, cx and cy are the coordinates for center of the ellipse.
	
`ellipse(210% 90% at 100% 0%)` defines an oval that its center is positioned at 100% horizontally and 0% vertically, with a radius 210% on the x-axis and 90% on the y-axis.

![](/assets/screenshot1-.png)

## Text Element

A title text will be on top of the background image. I didn’t add a “`contentedible=true`” in my h1 but the result came out the same. There are two parts; a main text and an overlapped text. First, it is to style the main text.

```html
<body>
  <div class="diagonal__box">
    <div class="diagonal__box--background image"></div>
    <h1 class="clipped-text" data-heading="THAILAND, 
    The Land of Smiles">THAILAND, The Land of Smiles</h1>
  </div>
</body>
```

```css
.clipped-text {
  color: var(--text-color);
  margin: 0;
  padding: 0 1rem 0 0;
  height: 100%;
  width: 100%;
  position: absolute;
  bottom: 0;
  right: 0;
  display: flex;
  flex-direction: row-reverse;
  align-items: flex-end;
  text-align: right;
  z-index: 3;
}
```

![](/assets/screenshot2.png)

Next, to make a contrasting color for the overlapped text and it will be stacked on top of the main text. I added a pseudo-element to it with the same attributes by using inherit.

```css
.clipped-text::after {
  content: attr(data-heading);
  color: var(--overlap-color);
  -webkit-clip-path: var(--clip-shape);
  clip-path: var(--clip-shape);
  margin: inherit;
  padding: inherit;
  height: inherit;
  width: inherit;
  position: inherit;
  bottom: inherit;
  right: inherit;
  display: inherit;
  flex-direction: inherit;
  align-items: inherit;
  text-align: inherit;
  z-index: 4;
}
```

![](/assets/screenshot3.png)

## The bottom

At the end, I created SVG path in figma.com and added it to HTML by using the <svg> element. Then, I applied the <image> element and now my image is part of the SVG. The image shows through the rectangles that I made.

![](/assets/screenshot4.png)

## CodePen Example

https://codepen.io/tongcocuzza/pen/WNxabYW

## Resources

* [The Magic of SVG Clip-path](https://dev.to/alvarosaburido/the-magic-of-svg-clip-path-1lf0)
* [Figure/ground composition with text, image, and color](https://rwt.io/typography-tips/figureground-composition-text-image-and-color)
* [Clipping in CSS and SVG – The clip-path Property and <clipPath> Element](https://www.sarasoueidan.com/blog/css-svg-clipping/#:~:text=The%20clip%2Dpath%20property%20is%20used%20to%20specify%20a%20clipping,in%20the%20CSS%20Shapes%20module.)
* Photo by [Krzysztof Maksimiuk](https://unsplash.com/@kmaksimi) on [Unsplash](https://unsplash.com/)