---
template: blog-post
title: CSS Shapes
slug: /css-shapes
date: 2020-10-18 14:53
description: CSS Shapes
featuredImage: /assets/screenshot.png
---
In this article I want to introduce the CSS Shapes which I will use for flowing text content around shapes other than just the rectangle box shape layout. Since our computers or devices’ screens are rectangle, to make our web page’s appearance more interesting I believe that CSS Shapes is a great choice.

**Basic Shapes Function**

The `shape-outside` property is used to define a shape that text content will flow around. Typically, the shapes are circle, ellipse, or polygon.

Shapes can be created using one of the following basic shapes functions applied to the object element:

```css
.object {
  shape-outside: circle();
}
```

more function values:

```css
shape-outside: ellipse();
shape-outside: url();
shape-outside: inset();
shape-outside: polygon();
```

**How it works**

Here I have an example that I built and used CSS. There are `h1` “Vanilla Cupcakes”, `img` - an image of a cupcake, and `p` - a paragraph.

```html
<h1>Vanilla Cupcakes</h1>

<img src="/image/cupcake.png" alt="A vanilla cupcake with maple buttercream"/>

<p>
  I love baking when I have a free time but I am not a profession. So, I get
  most of great recipes from watching YouTube channels. I modified this
  cupcake recipe from Gracious Treatz Channel and added my cupcakes with
  some chocolate chunks which I like Nestle semi-sweet chocolate chunks.
</p>
```

Then I floated the image to the left and, as you can see, the text is evenly spaced on the top and right of the image using the margin property.

```css
img {
  float: left;
  margin-right: 2em;
  margin-bottom: 0.5em;
}
```

![](/assets/screenshot-1.png)

**circle()**

Next, I added one line of code `shape-outside: circle();` this is the way we tell the browser to run the text content in a circle not in a box and it wraps around that cupcake image in a circle shape.

```css
img {
  float: left;
  margin-right: 2em;
  margin-bottom: 0.5em;
  shape-outside: circle();
}
```

![](/assets/circle2.png)

**ellipse()**

This is an example of `shape-outside: ellipse();` look at the inside shape, it was changed to oval shape.

![](/assets/ellipse.png)

**url()**

The `shape-outside: url(cupcake.png); `CSS declaration tells the browser to extract a shape from the image.

![](/assets/url.png)

**inset()**

The `inset()` allows us to provide values on how much we want the text content to overlap the shape. I added background-color because it’s easier to visualize.

```css
img {
  float: left;
  margin-right: 2em;
  margin-bottom: 0.5em;
  background-color: lightpink;
  shape-outside: inset(100px); /* set all four sides */
}
```

![](/assets/inset.png)

```css
img {
  float: left;
  margin-right: 2em;
  margin-bottom: 0.5em;
  background-color: lightpink;
  shape-outside: inset(40px 60px 80px 100px); /* top right bottom left */
}
```

![](/assets/trbl.png)

**polygon()**

The `polygon()` is flexible. It can be used to cut out shapes around images. The format is `polygon(x1 y1, x2 y2, x3 y3, …)` In this function each pair specifies the position of a point and a set of points make up a shape. In my example, I will make a triangle shape.

```css
img {
  float: left;
  margin-right: 2em;
  margin-bottom: 0.5em;
  background-color: lightpink;
  shape-outside: polygon(0px 0px, 532px 446px, 0px 446px);
}
```

The first point is `0px 0px`, the top left point. The second point is `532px 446px`, which is the bottom right point. The third point is `0px 446px`, which is the bottom left point.

![](/assets/polygon.png)

**Wrapping Up**

A webpage design doesn’t have to be in a box layout. We can think **out of the rectangle box** by using CSS Shapes to design irregularly shaped layouts. It will have a great effect to the user experience.

**Resource:**

* [Obliterate Boxiness with CSS Shapes](https://www.youtube.com/watch?v=pOB75oTNhw0)
* [Getting Started with CSS Shapes](<-	https://www.html5rocks.com/en/tutorials/shapes/getting-started/#toc-polygon>)
* [Shape-outside](https://developer.mozilla.org/en-US/docs/Web/CSS/shape-outside)