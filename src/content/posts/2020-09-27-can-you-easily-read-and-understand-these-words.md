---
template: blog-post
title: Can you easily read and understand these words?
slug: /can-you-easily-read-and-understand-these-words
date: 2020-09-26 19:35
description: Accessible Web Typography
featuredImage: /assets/fontsize.png
---
**Why is accessible web typography important?**

“**Accessibility** can be viewed as the "ability to access" and benefit from some system or entity. The concept focuses on enabling access for people with disabilities, or special needs, or enabling access through the use of assistive technology; **however, research and development in accessibility brings benefits to everyone**” (Wikipedia).

“**Typography** is the art and technique of arranging type to make written language legible, readable, and appealing when displayed” (Wikipedia).

In a nutshell, everyone will be able to access information and benefit from a clean and clear web typography. Furthermore, the Web and the Internet are important resources in our daily life. The main part of web accessibility is typography because users get information most often by reading the content of a website. So, the appearance of text should be designed to be comfortable to read.

**Let’s take a look at setting base font size in relative units:**

Base font size is the font size that all other font sizes will be based upon. In general, 16 px is the browser default font size.

In "5 Keys to Accessible Web Typography" Matej Latin said, “The best practice is to set the *font-size* on the *html* using % (or other relative unit), and then set all the other elements to either *em* or *rem* which will be relative to the body size.”

For example,

```
html {
  font-size: 100%; /* this defaults to 16 pixels */
}
h1 {
  font-size: 3rem; /* 48px */
}
h2 {
  font-size: 2.25rem; /* 36px */
}
h3 {
  font-size: 1.75rem; /* 28px */
}
h4 {
  font-size: 1.125rem; /* 18px */
}
```

Now that we have the initial values that might work well on a mobile device, we can use them to adjust the sizes on larger screen by using a simple media query.

```
html {
  font-size: 100%; /* this defaults to 16 pixels */
}

@media (min-width: 768px) {
  html {
    font-size: 112.5%; /* (112.5/100) * 16px = 18px */
  }
}
```

In this example, the body font size is 18 px, heading 1 is 3x18 = 54px, heading 2 is 2.25x18 = 40.5px, heading 3 is 1.75x18 = 31.5px, heading 4 is 1.125x18 = 20.25px.

The relative unit called *rem* is a "root" em which gets its font size whatever size that we set as a base font size.

Unlike the relative units, the *pixel* is an absolute unit. Its real-world size is determined by the device's manufacturer and that cannot be changed by the developer.

Some users need to enlarge the web content to be able to read it. This is why it is very important that we set the base font size in a relative unit. by setting the base font in CSS to 16 pixels, the developer will overwrite the browser's default font size setting. Users are forced to read the text at 16 pixels instead of s preferred larger font size.