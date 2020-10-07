---
name: Vertical centering of CTAs
keywords: CTA, vertically, align
dateUpdated: 10/7/2020
product: Answers
categories: Frontend, Card Customizations
---
With the default Handlebars template, the CTAs container will align with the details container within a card. If you’d like to change the alignment, you’ll need to modify the card template slightly.

If you want to shift the CTAs up to align them vertically within the card, rather than align them with the details container, you can move the title and subtitle into the ‘info’ div.

**template.hbs**
```hbs
<div class="HitchhikerProfessionalStandard {{cardName}}">
  {{> image }}
  <div class="HitchhikerProfessionalStandard-body">
    <div class="HitchhikerProfessionalStandard-contentWrapper">
      <div class="HitchhikerProfessionalStandard-info">
        {{> title }}
        {{> subtitle }}
        {{> details }}
        {{> list }}
        {{> phone }}
      </div>
      {{> ctas }}
    </div>
  </div>
</div>
```

You can then ensure the contentWrapper div extends the whole height of the card, and use justify-content and align-self to align the CTAs to the middle of the card.

**answers.scss**

```css
  .HitchhikerProfessionalStandard-contentWrapper {
    height: 100%;
  }

  .HitchhikerProfessionalStandard-ctasWrapper {
    justify-content: center;
    align-self: center;
  }
```