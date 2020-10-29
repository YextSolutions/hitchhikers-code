---
name: CTAs with Multicolor Gradient Borders
keywords: Gradients, CTA, CTAs, colors, border, borders, color
dateUpdated: 10/29/2020
product: Answers
categories: Frontend, Card Customizations
---
## Overview

You can use the learnings from [this post](https://hitchhikers.yext.com/community/t/the-basics-of-linear-gradients/1816) and tweak it to apply multiple colors to borders of CTAs. Rather than using ```background-image```, we will use ```border-image``` to apply a ```linear gradient```. It is important to note that ```border-image``` is not compatible with ```border-radius``` and therefore why most of these examples are square CTAs.

## Single Multicolor Border with Hover State

This example utilizes color gradients with hard lines. If you remove the percentages, the color transition will be smooth. You will apply a bottom border to the CTA and then again in the hover state making sure to adjust the colors to match the changing background color.

### The Code:

```css
.HitchhikerCTA {
    background-color: #0070b8;
    border-bottom: 3.5px solid;
    border-image: linear-gradient (to right, #0070b8 25%, #e6f5ff 25%, #e6f5ff 75%, #0070b8 75%) 1;
    
    &:hover{
        background-color: #003b61;
        border-image: linear-gradient (to right, #003b61 25%, #e6f5ff 25%, #e6f5ff 75%, #003b61 75%) 1;
    }
}
```

### The Result:
![image](https://aws1.discourse-cdn.com/turtlehead/original/2X/e/e5f2b35d39fad83cafe237f1692506e619301997.png)

*This applies to top and bottom borders only. You will need to add appropriate borders and then switch “to right” to “to bottom” for left and right borders to have this effect.*

## Multicolor Border that Covers Entire CTA
If you have a border set to cover the entire CTA, you can use the same logic as above. However, it will appear as if the top and bottom border are horizontally mirrored.

### The Code:
```css
.HitchhikerCTA {
    border: 3.5px solid;
    border-image: linear-gradient(to right, yellow, red , orange , green) 1;
 }
 ```

### The Result:

![image](https://aws1.discourse-cdn.com/turtlehead/original/2X/c/cf06fc85c48b2e99a0bd82584e66cd4169705d5f.png)

*If you want it to be vertically mirrored, switch “to right” to “to bottom”*

## Multicolor Border with Curved Edges

While ```border-image``` is not compatible with ```border-radius```, you can give the illusion of a curved multicolor border using a combination of ```background-image``` and ```box shadow```. The steps are as follows:

1. First you will create a multicolor CTA using linear-gradient for the background-image
2. Make sure you have a sizable transparent border
3. Use background-origin: border-box to make sure the gradient is positioned to cover the entire CTA including the border
4. Then you will apply a box-shadow of another color to cover the center of the button
5. You can also apply a hover to remove the box shadow and reveal the entire multicolor CTA

### The Code:
```css
.HitchhikerCTA {
    background-image: linear-gradient(to right, red, orange);
    border: solid 3px transparent;
    background-origin: border-box;
    box-shadow: 2px 1000px 1px #fff inset;

    &:hover{
         box-shadow: none;
    }
}
```
### The Result:
![image](https://aws1.discourse-cdn.com/turtlehead/original/2X/f/f19ae1dfce029337398dfaa4b1db3f024a5ddc15.png)