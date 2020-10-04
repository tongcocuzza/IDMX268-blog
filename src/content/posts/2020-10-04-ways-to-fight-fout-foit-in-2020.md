---
template: blog-post
title: Ways to fight FOUT & FOIT in 2020
slug: /ways-to-fight-fout-and-foit-in-2020
date: 2020-10-04 10:08
description: How to Fight FOUT & FOIT in 2020
featuredImage: /assets/jeroen-den-otter-plpo8kr6q9e-unsplash.jpg
---
Fonts are an important key for web content because fonts transmit words to users who will read them. To have good communication between web content and our users, a great web font design is crucial. However, going beyond the system fonts, like Arial, that do not need to be downloaded and, instead, choosing custom web fonts comes with negative impacts on loading performance because their heavy file sizes. Some of the issues are FOUT and FOIT.

**What is FOUT?**

A “FOUT” stands for “Flash of Unstyled Text” and is when a web page loads a system font initially and then swaps to the correct web fonts during the time the page is fully loaded. This behavior gives the reader a visual jolt as the fonts step in. It can be jarring and is considered giving the reader an imperfect experience.

**What is FOIT?**

A “FOIT” stands for “Flash of Invisible Text” and is a delay when the browser is loading a web page and it hangs on for the web font to be downloaded in order to display the text onto the page. For example, Safari will not display the text at all until the correct fonts are loaded. So, users see a blank page for few seconds before the page is fully loaded.

Hopefully, this delay time is unnoticeable, but sometimes it takes forever if the Internet connection is slow or with larger font files. In the article “*Part 4: Fixing FOUT with font loading & fallback tuning*”, Jason Pamental mentions that a standard timeout is 3 seconds for rendering the content in a fallback font before users abandon the site. Therefore, an effective way to manage FOUT and FOIT issues is by preloading optional fonts. Chris Coyier, the author of *CSS-Tricks*, recommends preloading fonts to tackle the issues.

Based on MDN Web Docs:

> “The `preload` value of the `<link>` element’s `rel` attribute lets you declare fetch requests in the HTML’s `<head>`, specifying resources that your page will need very soon, which you want to start loading early in the page lifecycle, before browsers’ main rendering machinery kicks in. This ensures they are available earlier and are less likely to block the page’s render, improving performance.”

For example, if you want to use the “Hepta Slab” font for your website, add this line:

`<link rel="preload" href="/fonts/HeptaSlab.woff" as=font/woff" crossorigin>`

Next step adding CSS `font-display: optional` property, which it

```
@font face {
  font-family: Hepta Slab;
  src: url(fonts/HeptaSlab.woff) format('woff');
  font-weight: 400;
  font-style: normal;
  font-display: optional;
}
```

Houssein Djirdeh explains in his article that the new font-display: optional behavior in Chrome 83 removes the possibility of layout shifting and FOUT. There is a 100ms timeout period for loading the custom font. If the 100ms block period has passed, the browsers will not load the custom font at all and use fallback font. So, the custom font will be available when the browsers quickly download less than the 100ms block period.

In the end, web developers want to have smooth websites for their users. Users experience some issues from time to time, often when connection speeds are poor. It is important that web developers know how to manage these issues. With this new great strategy of preloading optional fonts, their users will not have such a jarring experience.

**Resources:**

* [FightingFOIT and FOUT Together](https://css-tricks.com/fighting-foit-and-fout-together/)
* [If you really dislike FOUT, 'font-display: optional' might be your jam](https://css-tricks.com/really-dislike-fout-font-display-optional-might-jam/)
* [](https://css-tricks.com/really-dislike-fout-font-display-optional-might-jam/)[Prevent layout shifting and flashes of invisible text (FOIT) by preloading optional fonts](https://web.dev/preload-optional-fonts/)
* [Part 4: Fixing FOUT with font loading&fallback tuning](https://rwt.io/typography-tips/part-4-fixing-fout-font-loading-fallback-tuning)