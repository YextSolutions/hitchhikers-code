---
name: Adding a Custom Icon to FAQ Accordion Cards
description: Swapping out the default chevron on an faq-accordion card by using an icon URL 
keywords: custom icon, image, svg, css, toggle
dateUpdated: 12/14/2020
product: Answers
categories: Frontend, Card Customizations
---

You can change the toggle icon on the FAQ Accordion card from the default chevron to a custom icon using the following:

1.	Fork the faq-accordion card and modify the template.hbs file to include “iconUrl” rather than “iconName”. It should look like this:

```js
 <div class="HitchhikerFaqAccordion-icon js-HitchhikerFaqAccordion-icon{{#if card.isExpanded}} HitchhikerFaqAccordion-icon--expanded{{/if}}"
      data-component="IconComponent"
      data-opts='{"iconUrl": "https://www.brandname.com/themes/simple/images/arrow-down.svg"}'
      data-prop="icon">
    </div>
```

2.	To make the icon rotate like the default chevron does, you will need to add this code to the answers.scss file:

```css
.HitchhikerFaqAccordion-icon {
    transition: all 400ms ease-in-out;
}    

.HitchhikerFaqAccordion--expanded .HitchhikerFaqAccordion-icon {
    transform: rotate(-180deg);
}
```
**Based on the URL you’re including, you may also need to adjust the icons sizing

Here is what the end result will look like: 
![image](https://aws1.discourse-cdn.com/turtlehead/original/2X/d/d9be3baacb6d207dbccdd837983435eb6698a507.gif) 
