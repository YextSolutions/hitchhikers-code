---
name: Custom CTA icon
keywords: cta, icon, custom, image, url, iconurl
dateUpdated: 4/26/2021
product: Answers
categories: Frontend, Card Customizations
communityLinks:
imageURL:
---

## Overview
Typically, the icon associated with the CTA on an Answers card is defined through the ```iconName``` parameter within the CTA, using one of the pre-defined icons from the [icon library](https://github.com/yext/answers-search-ui#icon-component). However, if you wish to use a custom image as the CTA icon, you can do so by defining the ```iconUrl``` parameter.

## The Code
In the component.js file of your custom Answers card, edit the applicable CTA section where you would like to add the custom icon, like below. Note that, in this example, CTA2 is being edited, but this process can be 

**Before**

```js
CTA2: { // The secondary call to action for the card
        label: 'UberEats',
        iconName: 'chevron',
        url: profile.c_uberEatsURL,
        target: '_top',
        eventType: 'CTA_CLICK',
        eventOptions: this.addDefaultEventOptions(),
        // ariaLabel: '',
      }
```

**After**

```js
CTA2: { // The secondary call to action for the card
        label: 'UberEats',
        iconUrl: 'https://www.logolynx.com/images/logolynx/32/32ea592d61673edf18f39f3d8f9c1d4f.png',
        url: profile.c_uberEatsURL,
        target: '_top',
        eventType: 'CTA_CLICK',
        eventOptions: this.addDefaultEventOptions(),
        // ariaLabel: '',
      }
```
This would change the icon next to the CTA "UberEats" from a standard chevron to the logo saved at the specified URL.

## The Result

The custom icon now appears next to the CTA:

![image](https://user-images.githubusercontent.com/77289753/116117673-80b56000-a68a-11eb-80c2-38a78eb650a5.png)
