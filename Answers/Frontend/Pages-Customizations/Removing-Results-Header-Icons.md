---
name: Removing Icons from All Headers
description: Remove icons next to each vertical label in the universal search
keywords: Icons, Header, Results Bar, Title, CSS
dateUpdated: 10/29/2020
product: Answers
categories: Frontend, Page Customizations
---

# Update
This Hitchhikers Code Bank page is being deprecated as part of the Fall '22 Release on November 16th 2022. Please reference our new [Search documentation](https://hitchhikers.yext.com/docs/search) for this content and post in the community with any questions.

---
The easiest way to hide the header or results title bar icon is via CSS. You can add the following to the answers.scss file to hide it:

### **Standard Universal Template**
```css
.HitchhikerResultsStandard-title{
    .Icon{
        display: none;
    }
}
```

### **Two Column Grid Template**
```css
.HitchhikerResultsGridThreeColumns-title{
    .Icon{
        display: none;
    }
}
```

### **Two Column Grid Template**
```css
.HitchhikerResultsGridThreeColumns-title{
    .Icon{
        display: none;
    }
}
```

The result will look like this:

![image|1062x212](../../../Images/remove-icon-header.png)
