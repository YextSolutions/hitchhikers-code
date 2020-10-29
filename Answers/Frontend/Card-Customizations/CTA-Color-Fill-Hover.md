---
name: CTAs with Color Fill on Hover
keywords: CTA, CTAs, color, colors, hover, fill
dateUpdated: 10/29/2020
product: Answers
categories: Frontend, Card Customizations

---

CTAs can be styled using css to fill with color from left to right (or right to left) using the following:

### The Code

```css
.HitchhikerCTA {
    border-radius: 30px;
    border: 1px solid #ddd;
    background: linear-gradient(to right, #1b64b9 50%, #fff 50%);
    background-size: 200% 100%;
    background-position: right bottom;
    transition: all .3s ease-out;
    
    &:hover{
      background-position: left bottom;
    }
  
    .HitchhikerCTA-iconLabel{   
      &:hover{
      color: white;
      } 
    }  
}
```

This sets the background as a linear gradient with a hard line between colors and then enlarges/stretches it using background-size. Then the gradient shifts from one side of the CTA to the other based on the changing background-position from the CTA object to the hover state. Lastly, transition adjusts the time it takes for the linear gradient to fully shift position.

If you want to also change the text color as the CTA fills, you will need to add a hover state to the CTA icon label.

### The Result

![image](https://aws1.discourse-cdn.com/turtlehead/original/2X/d/d73d52daa2844f8ce1dcf8e31cc98015c4606f86.gif)