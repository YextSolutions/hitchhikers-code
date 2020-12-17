---
name: Modify CSS of a class without affecting other verticals using the same class
keywords: target, css
dateUpdated: 12/17/2020
product: Answers
categories: Frontend, Card Customizations
communityLinks:
imageURL:
---

## Overview

If you have multiple verticals that fork the same card (e.g., *leadershipoverride* and *articleoverride* both forking the product prominent image card), you can make CSS changes to one card without affecting the other by nesting all of your CSS selectors under .[CARD_TYPE].[CUSTOM_CARD_NAME].

## The Code

Below is an example of a change that would impact the *leadershipoverride* card but not the *articleoverride* card, even though they are both forked from the ProductProminentImage card. 

```css
  .HitchhikerProductProminentImage.leadershipoverride {
    justify-content: space-between;

    .HitchhikerProductProminentImage-bottom {
      padding: var(--yxt-base-spacing);
      padding-top: 0px;
    }
  }
```
