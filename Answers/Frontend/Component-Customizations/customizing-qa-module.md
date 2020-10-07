---
name: Overriding the Q&A Component for Analytics Tracking on Links
description: 
keywords: Custom Partials, Q&A Component, Custom Analytics
imageURL: 
dateUpdated: 10/1/2020
communityLinks: 
product: Answers
categories: Frontend, Component Customizations
---

## Introduction
One use case we've encountered is adding custom tracking to links in the description of the Q&A Module. 

![image](/Images/QA-Submission-Example.png) 

Whenever you want to make an update to the _template_ of a component, you'll need to take a few steps to override the template. The [Overriding Component Layouts](https://hitchhikers.yext.com/modules/ans325-changing-page-card-structure/04-component-layout/) unit has some context, but we'll walk through the specific example of adding event tracking to the links in the Q&A description. As a note, this will require a good understanding of Handlebars and the Answers Javascript Library to complete successfully.

## Adding Custom Partials
The base Question Submission handlebars template can be found in the Answers  Javascript Library here: https://github.com/yext/answers/blob/master/src/ui/templates/questions/questionsubmission.hbs

For this example, we don't want to change too much of the partial itself, so we'll use this as a starting point and tweak from there.

First, create two files in your `partials` folder - `customQA-universal.hbs` and `customQA-vertical.hbs`.

![image](/Images/QA-Partials-Example.png) 

Next, copy/paste the contents of the Q&A template from the Answers Library above into these two files, as our starting point.

Find where it's referencing the `{{{_config.description}}}`. This is injecting what you've determined in `componentSettings` of your page as the description. Here, we'll hardcode the description in the template itself.

Replace the `{{{_config.description}}}` line with the below (separate snippets for each file):

**customQA-universal.hbs**
```hbs
If you need to contact us urgently, please call toll-free 
<a href="tel:1866-800-999"
data-eventtype="TAP_TO_CALL"
data-eventoptions='{"searcher": "UNIVERSAL", "entityId": "ORG-1", "verticalKey": "QASubmission", "ctaLabel": "qa-call"}'> 1-866-800-999</a>, 
email 
<a href="mailto:help@brand.com"
data-eventtype="EMAIL"
data-eventoptions='{"searcher": "UNIVERSAL", "entityId": "ORG-1", "verticalKey": "QASubmission", "ctaLabel": "qa-email"}'>
    help@brand.com
</a> 
or use our chat function for immediate support.
```

**customQA-vertical.hbs**
```hbs
If you need to contact us urgently, please call toll-free 
<a href="tel:1866-800-999"
data-eventtype="TAP_TO_CALL"
data-eventoptions='{"searcher": "VERTICAL", "entityId": "ORG-1", "verticalKey": "QASubmission", "ctaLabel": "qa-call"}'> 1-866-800-999</a>, 
email 
<a href="mailto:help@brand.com"
data-eventtype="EMAIL"
data-eventoptions='{"searcher": "VERTICAL", "entityId": "ORG-1", "verticalKey": "QASubmission", "ctaLabel": "qa-email"}'>
    help@brand.com
</a> 
or use our chat function for immediate support.
```

The `data-eventoptions` is passing the relevant data needed to succesfully fire the analytics event. Make sure that the `entityId` aligns to the ID of your Organization entity that's linked to the Q&A module.

## Using this Template in the QA Submission Component
Now, we'll need to override all page templates using the Q&A Submission component to make sure it references this new partial. If you're planning on using the Q&A module across all your pages, you'll need to do this for each variation of page template - here, we're modifying `universal-standard`, `vertical-standard`, `vertical-grid`, and `vertical-map` to override the `script > qasubmission.hbs` file.

![image](/Images/QA-OverrideTemplate-Example.png) 

Replace the contents of the file with the below:

**Universal Pages**
```js
ANSWERS.addComponent('QASubmission', Object.assign({}, {
    container: '.js-answersQASubmission',
    template: `{{{read 'partials/customQA-universal' }}}`,
}, {{{ json componentSettings.QASubmission }}}));
```

**Vertical Pages**
```js
ANSWERS.addComponent('QASubmission', Object.assign({}, {
    container: '.js-answersQASubmission',
    template: `{{{read 'partials/customQA-vertical' }}}`,
}, {{{ json componentSettings.QASubmission }}}));
```

This is just telling the template to use your new partials instead of the default template.

Now, you'll be able to see clicks associated with these actions. Make sure to confirm by inspecting the Analytics events fired and looking in the platform to see if these clicks are being associated to the right organization & associated with the right event type. 

Because this requires overriding the theme heavily, make sure to be careful for any theme upgrades you pursue in the future.