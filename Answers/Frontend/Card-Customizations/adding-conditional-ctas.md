---
name: Add a Conditional CTA Based on Boolean
description: Walkthrough of the card updates needed to add a conditional CTA.
keywords: Boolean, HBS, Accepting New Patients
dateUpdated: 10/5/2020
product: Answers
categories: Frontend, Card Customizations
---
## Overview
Take a scenario where you only want the “Book Appointment” CTA to show up on provider cards when that provider is accepting new patients, a field stored in the Knowledge Graph. Essentially, if  `acceptingNewPatients`=`true`, then display tertiary CTA.

This could bypass adding/removing information from the KG as doctors’ statuses change, so all you would have to do to would be toggle “Accepting New Patients” for the CTA to surface in Answers.

## Instructions
You can easily do this by adding a boolean to your component.js file, and modifying the handlebars template to *only* show the third CTA if that boolean evaluates to true.

**component.js**
The first step is to pass the information about whether a provider is accepting patients. Add an attribute in your component.js file to store whether or not a provider is accepting new patients. If you use the profile field, when this is marked as 'Yes', the boolean will evaluate to `true`; if it's marked as false *or* unpopulated, it will evaluate to `false`.
```js
acceptingNewPatients: profile.acceptingNewPatients,
```

You'll also need to provide the data mapping for the third CTA.
```js
CTA3: { // The tertiary call to action for the card
        label: 'Book Appointment',
        iconName: 'calendar',
        url: profile.c_primaryCTA.link,
        target: '_top',
        eventType: 'BOOK_APPOINTMENT',
        eventOptions: this.addDefaultEventOptions(),
        // ariaLabel: '',
      }
```

**template.hbs**
The next step is to use this boolean to only show the tertiary CTA when `acceptingNewPatients` = true.

We can do this using an `if` statement in handlebars. We'll check if card.acceptingNewPatients evaluates to true; if so, we'll add the tertiary CTA. You can see the modifications to the CTA partial below:
```hbs
{{#*inline 'ctas'}}
{{#if (any (all card.CTA1 card.CTA1.url) (all card.CTA2 card.CTA2.url)(all card.CTA3 card.CTA3.url))}}
<div class="HitchhikerLocationStandard-ctasWrapper">
  {{> CTA card.CTA1 ctaName="primaryCTA" }}
  {{> CTA card.CTA2 ctaName="secondaryCTA" }}
  {{#if card.acceptingNewPatients}}
   {{> CTA card.CTA3 ctaname="tertiaryCTA"}}
  {{/if}}
</div>
{{/if}}
{{/inline}}
```

This will hide the CTA if acceptingNewPatients is not populated or false, and show it if it's true.