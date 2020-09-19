---
template: blog-post
title: Zippy, Zingy CSS Custom Properties & Media Queries
slug: /Zippy-Zingy-CSS-Custom-Properties-and-Media-Queries
date: 2020-09-19 13:32
description: CSS Custom Properties and Responsive Design
featuredImage: /assets/pankaj-patel-4oafasapftg-unsplash.jpg
---
Today more people access the web through their mobile devices; the desktop computer is not a primary way. So, it is all-important to get the right design and function that allows a website to be comfortably viewed and used on devices.

CSS custom properties, also known as CSS variables, are useful for managing layout, typography, and color. Variables reduce the problem of using properties and values repeatedly in CSS style sheet. If a developer wants to use a particular value of a property, they can do that by defining custom properties within the *:root* element. 

CSS media queries let us test for a particular feature. For example, it can test a viewport for a minimum width (min-width) and maximum width (max-width). The way to utilize media queries is to use an *@media* (“at-media”) ruleset in our CSS style sheet.

The way to utilize CSS custom properties in responsive design is to use variables to store values that change inside of media queries.

**Responsive Designing**

* **Typography**

From small-screen to wide-screen views, typography should be clear and pleasant to read. CSS custom properties allows us to adjust it for a range of viewport sizes.

\--------------------------------------------------------------------------------------------------------------

: root {

\-- font-size: 1rem;

}

@media (min-width: 1024px) {

:root {

\-- font-size: 2rem;

}

}

h1 {

Font-size: var (-- font-size);

}

\--------------------------------------------------------------------------------------------------------------

In this example, if the device is more than 1,024 pixels wide, heading1 displayed on devices will be larger.

* **Color**

Color is a powerful tool to attract a user’s attention. It is very important to choose the right colors. We can use CSS custom properties to keep the consistency of color values in our CSS.

\--------------------------------------------------------------------------------------------------------------

: root {

\-- body-background: #fff; /\* white \*/

}

@media (min-width: 1024px) {

:root {

\-- body-background: #ffff00; /\* yellow \*/

}

}

body {

background-color: var (-- body-background);

}

\--------------------------------------------------------------------------------------------------------------

In this example, if the device is more than 1,024 pixels wide, the background displayed on devices will be yellow.

These examples show a simple way of how CSS custom properties can be used in your responsive design workflow. The feature is that you don’t have to rewrite values repeatedly because the var () function allows you to redefine these values in other properties. So, it helps keep your @media queries nice and clean.