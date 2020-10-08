---
name: Card shadow
description: Create a box shadow on a card when hovering.
keywords: card, shadow, CSS
dateUpdated: 10/8/2020
product: Answers
categories: Frontend, Card Customizations
---

To add a bit of pop to your cards in the form of a drop shadow you can use the below code.

```css
.[[card name]] {
    transition: box-shadow .3s;

    &:hover {
      box-shadow: 0 0 11px rgba(33,33,33,.2); 
    }
  }
```

You can learn more about how to use box shadows [here](https://www.w3schools.com/cssref/css3_pr_box-shadow.asp).