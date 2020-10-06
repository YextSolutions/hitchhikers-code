---
name: CTA Underline Hover Color not updating
description: Update the underline color of a CTA.
keywords: CTA, hover, color
---

You would do so with the property of text-decoration-color

Potential code would look like this:

```css
.HitchhikerCTA {
    color: #006FF0;
    &:hover{
       color: #006FF0;
       text-decoration-color: #006FF0; 
 
    }
  }
  ```

Text decoration is the key propery and specifies the decoration added to text.
