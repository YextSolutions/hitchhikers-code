---
name: Updating Font Color for Nav Bar
description: changing the base color of the navigation bar text
keywords: Borders, Universal Search, Results, CSS
dateUpdated: 10/29/2020
product: Answers
categories: Frontend, Page Customizations
---

# Update
This Hitchhikers Code Bank page is being deprecated as part of the Fall '22 Release on November 16th 2022. Please reference our new [Search documentation](https://hitchhikers.yext.com/docs/search) for this content and post in the community with any questions.

---
To change the color of the nav bar text so that it does not impact the color change on hover and when a vertical is selected, you can add the following to the answers.scss file: 

```css
--yxt-nav-text-color: white; 
```

The result (when hovering on the classes vertical):

![image|537x65](../../../Images/nav-text-color-variables.png)

You could also target the following class in the answers.scss file, but it will remove the default color change on hover and when a vertical is selected:

```css
.yxt-Nav-item.is-active {
    color: orange;
```
The result:

![image|564x53](../../../Images/nav-text-color-answers.scss.png)
