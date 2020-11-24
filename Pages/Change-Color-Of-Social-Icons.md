---
name: Change Color of Social Icons 
description: Options to change the color of the social icons in the footer nodule of Page Builder
keywords: Social, Icon, Icons, Color, CSS
dateUpdated: 5/1/2020
product: Pages
---

You can use additional CSS filter functions to adjust the color of the social icons. The default code for social icons looks something like this:

```css
.social-icon { align-items: center; display: flex; justify-content: center; height: 45px; width: 45px;

    .icon-img {
        filter: invert(1); // make it black
    }
}
```

There are a couple options you can use to edit the color: 

1. You can erace the `filter` funtion and replace it with `color` like this:

```css
.icon-img {
    color: white;
}
```

2. You can utilize [this stackoverflow thread](https://stackoverflow.com/questions/7415872/change-color-of-png-image-via-css) and [this tool](https://codepen.io/sosuke/pen/Pjoqqp) to get the CSS filter function that will adjust a black icon to the desired color.

```css
.icon-img {
    filter: invert(41%) sepia(35%) saturate(2131%) hue-rotate(135deg) brightness(83%) contrast(102%); // make it #00866F
}
```

