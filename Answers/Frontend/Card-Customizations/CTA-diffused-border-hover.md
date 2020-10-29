---
name: CTAs with Diffused Border on Hover
keywords: CTA, CTAs, colors, border, borders, color, hover
dateUpdated: 10/29/2020
product: Answers
categories: Frontend, Card Customizations
thumbnail: https://aws1.discourse-cdn.com/turtlehead/original/2X/5/5eeca641d491fb33608094f4a06137bc32764d05.gif
---
To get this effect, you will first need to create a solid border around the CTA. Then you will add a ```box-shadow``` to the hover state to create that diffused look surrounding the border. The first portion of the ```box-shadow``` is ```inset```, which affects how much the color diffuses/casts a shadow inward towards the CTA label. The second portion affects how much the shadow casts outward. Here is the CSS you can add to your ```answers.scss``` file:

### The Code:

```css
.HitchhikerCTA {
  border: 1px solid black;

  &:hover { 
    box-shadow: 0 0 6px 0 black inset, 0 0 10px 1px black;
    }
  }
```
### The Result:

![image](https://aws1.discourse-cdn.com/turtlehead/original/2X/5/5eeca641d491fb33608094f4a06137bc32764d05.gif) 

*You can toggle with the box-shadow depending on how large and opaque you want the diffused border to be*


