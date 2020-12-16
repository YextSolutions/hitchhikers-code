---
name: Result Cards with Rounded Corners
description: Editing product prominent image result cards to have rounded borders
keywords: image, borders, CSS, grid
dateUpdated: 12/8/2020
product: Answers
categories: Frontend, Card Customizations
---

In order to achieve rounded corners on results cards, you can use the code listed below. Be sure to edit the class name if you’re using a different card.

1. Add the following to your answers.scss file within .Answers {}

```css
.HitchhikerProductProminentImage {
  border-radius: 25px;
}

.HitchhikerProductProminentImage-img {
  border-radius: 25px 25px 0 0;
}
```

2. Add the following outside of .Answers {}

```css
.AnswersVerticalGrid .Hitchhiker-3-columns .yxt-Card-child,
.HitchhikerResultsGridThreeColumns-Card--universal {
  border-radius: 25px;
}
```
The result will look like this:

![image](https://aws1.discourse-cdn.com/turtlehead/original/2X/3/346d0981492a9f17872f22e960b4e4c297afb92e.jpeg)


