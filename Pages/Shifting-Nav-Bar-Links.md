---
name: Shifting Navigation Bar Links
description: Shift the links in the top Navigation Bar to the right hand side of the page
keywords: Nav, Navigation, Links, Text, Page
dateUpdated: 5/4/2020
product: Pages
---

In order to adjust the position of the nav bar's text, you should apply the CSS below to the div containing the links. This will shift the links in the top Navigation Bar to the right hand side of the page:

```css
.links-div {
    justify-content: flex-end;
}
```

As the code implies, this justifies content to the end of the container using the Flexbox layout. You can learn more about Flexbox [here](https://www.w3schools.com/css/css3_flexbox.asp).

![image|1379x141](../../../Images/nav-bar-shift.png)