---
name: Location Bias Styling
keywords: locaiton, bias, styling, format, css
dateUpdated: 10/29/2020
product: Answers
categories: Frontend, Pages Customizations
---

To alter the styling of the location bias component that sits at the bottom of the results page, you can use the below sample css as a starting point.

**Be sure to add this code OUTSIDE of the main Answers class**

```css
.yxt-LocationBias {
  strong {
    color: black;
  }
}

.yxt-locationBias-locSource {
  color: black;
}

.yxt-locationBias-updateLoc {
  text-decoration: underline;
  color: black;
  text-decoration-color: #ffb500;
  font-weight: bold;
  &:hover{
    text-decoration: none;
  }
}
```

## Result

![image](https://aws1.discourse-cdn.com/turtlehead/optimized/2X/5/5109cac8e80ed1d1ff2d0f395f0f495963f47e0e_2_1035x357.png)