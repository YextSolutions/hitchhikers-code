---
name: Prominent image unification
description: Unify the sizes of images when using the prominent image card.
keywords: image, size, prominent image, CSS
dateUpdated: 10/8/2020
product: Answers
categories: Frontend, Card Customizations
---

Often when using the prominent image card images will not be uniform in size. To address this use the below CSS in your answers.scss file.

```css
.HitchhikerProductProminentImage-imgWrapper {
    justify-content: center;
    padding: .5rem;
}
.HitchhikerProductProminentImage-img {
    width: auto;
    height: 200px;
    object-fit: cover;
    object-position: center;
}
```

This will standardize your images to all have a height of 200px, with a .5rem border around your images. The `object-fit` properties help define the behavior of the image if it isn't inherently the fixed dimensions - more information here: https://www.w3schools.com/css/css3_object-fit.asp