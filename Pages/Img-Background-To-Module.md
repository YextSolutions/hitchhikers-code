---
name: How to add a image background to a module
description: Adding an image behind a text block module in Page Builder
keywords: Module, Image, Background, Pages
dateUpdated: 2/19/2020
product: Pages
---
You can add an image to the background of a Page Builder module by using the following steps:

1. For the module you want to edit, click the “Edit CSS” button in the top right of the module edit screen.

2. From there, you can use the background-image property to add in the background that you want to the “container” class:

```css
.container {
text-align: center;
background-image: url(“https://website.com/image.png”);
```