---
name: Wrap CTA
description: Wrap a long CTA for a specific vertical.
keywords: CTA, Wrap, vertical
dateUpdated: 10/6/2020
imageURL: 
communityLinks: 
product: Answers
categories: Frontend, Card Customizations
---

There are situations where you might want to wrap CTAs for a specific vertical if they are particularly long. This could be both from UI perspective but also to create cleaner experiences on mobile.

The below code is for the FAQ card type. 

```css
.HitchhikerFaqAccordion {
    
    .HitchhikerCTA-iconLabel
    {
        white-space: normal;
        text-align: left
    }
}
```

The key property here is white-space, which specifies how white-space inside an element is handled.

You can modify top level property of the above code (in this case .HitchhikerFaqAccordion) to target the relevant vertical.

