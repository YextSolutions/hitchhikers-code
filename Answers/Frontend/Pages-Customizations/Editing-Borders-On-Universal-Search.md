---
name: Universal Search Results with Only Top and Bottom Borders
description: Editing CSS to only have a top and bottom border rather than having all borders around each result card and header.
keywords: Borders, Universal Search, Results, CSS
dateUpdated: 10/29/2020
product: Answers
categories: Frontend, Page Customizations
---

You can style the universal search results to have only top and bottom borders using the code below:

```css
.HitchhikerResultsStandard-title {
border-left: none;
border-right: none;
border-top: none;
border-bottom: 1px solid #c5bbb1;
}

.HitchhikerResultsStandard-titleLabel {
border-left: none;
border-right: none;
border-top: none;
border-bottom: none;
}

.HitchhikerResultsStandard-Card {
border-left: none;
border-right: none;
border-top: none;
border-bottom: 1px solid #c5bbb1;
padding-bottom: 30px;
padding-top: 7px;
}

.HitchhikerResultsStandard-viewMore {
border-left: none;
border-right: none;
border-bottom: none;
border-top: none;
}

.yxt-Card {
border-left:none;
border-right: none;
border-top: none;
border-bottom: 1px solid #c5bbb1;
}
```


The result will look like this:

![image|1171x435](../../../Images/top-bottom-results-border.png)