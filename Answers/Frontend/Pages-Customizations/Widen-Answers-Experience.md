---
name: Widen the Answers Experience Results
description: How to widen answers experience and resolve breakpoint issues
keywords: Size, Widen, Results, CSS
dateUpdated: 09/16/2020
product: Answers
categories: Frontend, Page Customizations
---

# Update
This Hitchhikers Code Bank page is being deprecated as part of the Fall '22 Release on November 16th 2022. Please reference our new [Search documentation](https://hitchhikers.yext.com/docs/search) for this content and post in the community with any questions.

---

You can widen the answers container using the variable `--hh-answers-container-width` in your answers-variables.scss file. This increases the width of both the search bar and the cards themselves.

Just know that if you change it, you’ll need to test across browsers/devices to confirm functionality! The width of the cards aligns with best practices for easier readability of paragraph-like text - if it’s too wide, it becomes harder for a user to keep track of their place while reading.

If you find there are breakpoint issues when viewing on various devices you can follow the below steps to resolve:

**1. Add an additional variable in your answers-variables.scss file.** We can use this to help adjust the mobile responsiveness across different breakpoints.
```
$breakpoint-custom-min: 1000px;
```

**2. Use media queries to adjust the width of the Answers-container class.** You can learn more about media queries here 2. Here, we’ll redefine the behavior at the existing breakpoint to only fill up to 100% of the width, and define the behavior once the width is greater than your hh-answers-container-width to set the width to that value (in this case, 1000px).
```css
@media (min-width: $breakpoint-mobile-min) {
    .Answers-container {
        width: 100%;
    }
  }

  @media (min-width: $breakpoint-custom-min) {
    .Answers-container {
        width: $breakpoint-custom-min;
    }
  }
```

Here, you can see how we’re overriding the styling (which would have set the width of the container to 1000px at the 768px breakpoint) to be 100% until we meet the threshold of the new answers-width value.

![image](https://aws1.discourse-cdn.com/turtlehead/optimized/2X/0/08d17236265d6f59d64e833d1b88c7587e3bf1ea_2_690x352.gif)
