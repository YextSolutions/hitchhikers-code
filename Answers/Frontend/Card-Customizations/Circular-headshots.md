---
name: Add circular headshots
keywords: headshots, photos, circular
dateUpdated: 10/7/2020
product: Answers
categories: Frontend, Card Customizations
---

## Overview
For cards with images, you may want to format images to be a consistent shape; for example, making them all consistently circular. While the best way to do so is to edit your original images themselves, you can do this via CSS.

## Background
The best way to accomplish this is to do so via the `object-fit` properties. Learn more about this property here: https://www.w3schools.com/css/css3_object-fit.asp.

The below CSS would make the images circular, focusing on the center of the image, with a standard size.

```css
.HitchhikerProductProminentImage-img {
    width: 100%;
    height: 200px;
    object-fit: cover;
    object-position: center;
    border-radius: 50%;
    padding: 1rem;
}
  ```
![image](../../../Images/circular-images-cards.png) 

Beware that the cropping won’t be foolproof.

If you would like to differentiate certain properties for the Desktop and Mobile experiences you can use [media queries](https://www.w3schools.com/css/css_rwd_mediaqueries.asp).

*Sample code using this techique below*

```css
.HitchhikerProductProminentImage-img {
    width: 100%;
    height: 200px;
    object-fit: cover;
    object-position: center;
    border-radius: 50%;
    padding: 1rem;

    @media only screen and (max-width: 768px) {
      border-radius: 0px;
      padding: 0px;
    }
}
```
![image](../../../Images/circular-images-mobile.png) 
