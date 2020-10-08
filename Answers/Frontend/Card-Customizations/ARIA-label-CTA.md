---
name: ARIA label for CTA fields
description: Alter the ARIA label for a CTA field to correspond to the specific entity.
keywords: ARIA, CTA
dateUpdated: 10/8/2020
product: Answers
categories: Frontend, Card Customizations
---
You can add aria-labels to your CTAs in Jambo by updating the handlebars.

First fork the card and in the component.hbs file, update the HTML to include the aria-label attribute on the CTA (see below):

```hbs
<a class="HitchhikerCTA js-HitchhikerCTA{{#if modifiers}} {{modifiers}}{{/if}}" href="{{url}}"
    data-eventtype="{{eventType}}" data-eventoptions='{{json eventOptions}}'
    target="{{#if target}}{{target}}{{else}}_top{{/if}}"
    aria-label="{{ariaLabel}}">
```

More information on how to use aria-labels are outlined in [W3C’s guidelines 1](https://www.w3.org/WAI/GL/wiki/Using_aria-label_for_link_purpose).

In the component.js file for the card, add the ariaLabel in your CTAs under dataForRender and set it to the appropriate text / field, for example:

```js
CTA1: {
   label: "My CTA Label", 
   iconName: 'chevron', 
   url: "#",
   target: '_top', 
   eventType: 'CTA_CLICK', 
   eventOptions: this.addDefaultEventOptions(),
   ariaLabel: "Learn more about this product" //newly added label, can pull from the profile or be hardcoded 
},
```

This ariaLabel in dataForRender will be passed into the handlebars template for the card that you edited in step 2.

Generally this attribute makes sense to build in by default, I’ll make a request to do so (so you won’t need to edit the component.hbs file to configure the label).