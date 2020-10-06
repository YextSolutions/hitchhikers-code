---
name: Facet Styling Customization
description: Editing and styling various components of vertical facets
keywords: facet, filter, color, label, border
---

You’ll need to be on version 1.4 or above for this to work. For the filter buttons and filter button color, see some sample CSS below:

**Squaring Off Filter Button**
```css
  .yxt-FilterOptions-optionLabel:before {
    border-radius: 0;
  }
 ```
  
**Filter Button Color**
```css
  .yxt-FilterOptions-optionLabel:after {
    border-right: .0625rem solid var(--yxt-color-brand-primary);
    border-bottom: .0625rem solid var(--yxt-color-brand-primary);
  }
  ```
  
  For updating the Apply Filter and Reset Filter labels, there are options in the [Facet Component](https://github.com/yext/answers#facets-component) which you can add in your componentSettings on your vertical page config.
  
