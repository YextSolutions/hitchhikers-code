---
name: Add circular headshots
keywords: headshots, photos, circular
dateUpdated: 10/7/2020
product: Answers
categories: Frontend, Card Customizations
---
The best way to accomplish this is to set the headshots as the background-image of it’s container. To do this, you will need to fork the professional-standard or professional-location card.

First, we’ll update the handlebars template to make the image a background image instead of placing the image directly on the page.

**template.hbs**

```hbs
{{#*inline 'image'}}
{{#if card.image}}
<div class="HitchhikerLocationStandard-imgWrapper">
  <img class="HitchhikerLocationStandard-img" src="{{card.image}}" alt="{{#if card.altText}}{{card.altText}}{{/if}}" />
</div>
{{/if}}
{{/inline}}
```

Then, we’ll add CSS to make the headshots circular.

```css
  .HitchhikerLocationStandard-imgWrapper
  {
    background-size: cover;
    background-position: center top;
    background-repeat: no-repeat;
    width: 6.25rem;
    height: 6.25rem;
    border-radius: 50%;
  }
  ```

This should produce the desired effect. Beware that the cropping won’t be foolproof.

If you would like to differentiate certain properties for the Desktop and Mobile experiences you can use [media queries](https://www.w3schools.com/css/css_rwd_mediaqueries.asp).

*Sample code using this techique below*

```css
@media only screen and (max-width: 768px) {
.HitchhikerLocationStandard-imgWrapper {
width: 7.25rem;
height: 5rem;
margin-right: 2rem;
}
}
```