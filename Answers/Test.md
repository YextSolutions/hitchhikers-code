---
name: test
description: Walkthrough of the card updates needed to add a conditional CTA.
keywords: Boolean, HBS, Accepting New Patients
---

W
test
test
test


TMENT',
        eventOptions: this.addDefaultEventOptions(),
        // ariaLabel: '',
      }
```

**template.hbs**
The next step is to use this boolean to only show the tertiary CTA when `acceptingNewPatients` = true.

We can do this using an `if` statement in handlebars. We'll check if card.acceptingNewPatients evaluates to true; if so, we'll add the tertiary CTA. You can see the modifications to the CTA partial below:
```
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

This will hide the CTA if acceptingNewPatients is not populated or false, and show it if it's true. Let us know if this works!