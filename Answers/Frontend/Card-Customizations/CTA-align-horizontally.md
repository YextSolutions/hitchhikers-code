---
name: Align CTAs Horizontally
keywords: CTA, align, horizontal
dateUpdated: 10/29/2020
product: Answers
categories: Frontend, Card Customizations

---

The below code will allow you to align two CTAs horizontally on a card. 

```css
.HitchhikerFaqAccordion-ctasWrapper {
    flex-direction: row;
    flex-wrap: wrap;
    justify-content: space-evenly;
    display: flex;
}
```

![image|712x477](../../../Images/side-by-side-ctas.png)

We recommend you test this on mobile though, and make sure it’s appearing as desired. You might want to make sure the CTAs are ```flex-direction: column ``` on smaller breakpoints.