---
name: ARIA label for CTA fields
description: Alter the ARIA label for a CTA field to correspond to the specific entity.
keywords: ARIA, CTA
dateUpdated: 10/8/2020
product: Answers
categories: Frontend, Card Customizations
---

## Overview
Aria labels are helpful components added for accessibility so that screen readers can understand the page content. You can add aria-labels to your CTAs in Jambo by commenting in the `ariaLabel` attribute in your forked card's component.js file. 

More information on how to use aria-labels are outlined in [W3C’s guidelines 1](https://www.w3.org/WAI/GL/wiki/Using_aria-label_for_link_purpose).

## Instructions
First, fork the card. In the component.js file for the card, comment in the ariaLabel in your CTAs under dataForRender and set it to the appropriate text / field, for example:

```js
    CTA1: {
    label: 'RSVP', // The CTA's label
    iconName: 'calendar', // The icon to use for the CTA
    url: profile.ticketUrl || profile.website, // The URL a user will be directed to when clicking
    target: '_top', // Where the new URL will be opened
    eventType: 'RSVP', // Type of Analytics event fired when clicking the CTA
    eventOptions: this.addDefaultEventOptions(),
    ariaLabel: 'Learn more about this product', // Accessible text providing a descriptive label for the CTA
    },
```