---
name: How to Adjust the Size of Custom Title Icons
description: Adjusting custom icons (from image URLs) next to the title bar label so they match sizing of standard icons and labels.
keywords: Title Bar, Custom Icon, Icon 
dateUpdated: 10/5/2020
product: Answers
categories: Frontend, Pages Customizations
---

# Update
This Hitchhikers Code Bank page is being deprecated as part of the Fall '22 Release on November 16th 2022. Please reference our new [Search documentation](https://hitchhikers.yext.com/docs/search) for this content and post in the community with any questions.

---
You can do this by adjusting the ‘width’ and ‘height’ property of the icon. Try the below:

```css
.yxt-Results-titleBar .Icon-image {
  width: 1.5em;
  height: 1.5em;
 }
```
