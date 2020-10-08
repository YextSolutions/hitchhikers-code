---
name: Conditional Formatting on CTA Icons
description: Change the icon that displays on CTA buttons conditionally based on the contents of their corresponding CTA labels. For example, if the label contains a substring “read”, then the icon will format magnifying_glass. If the label contains a substring “call”, then format a phone icon.
keywords: Call to Action, CTA, Conditional Format, Custom Formatters, CTA Icons, CTA Labels
dateUpdated: 09/24/2020
communityLinks: 
product: Answers
categories: Frontend, Custom Formatters

---
1. Add the below function to your static/js/formatters.js file
static listCTA(list) {

    if(!list) {
      return null;
    }
    let names = [];
      list.forEach(element => names.push(`<a href="${Formatter.generateCTAFieldTypeLink(element)}">${element.label}</a>`));
    return names;
  }
  
2. Use the formatter in a ‘list’ section on your card.

listItems: Formatter.listCTA(profile.c_contactLinks)

3. Update the handlebars template to display the HTML

To allow the HTML to display on the page, we need to ensure the Handlebars template treats it correctly. We do this by ensuring the element is surrounded by three braces {{{ }}}

Specifically for the listItems field ensure, it looks like the following:

<ul class="HitchhikerProfessionalStandard-list">
    {{#each card.listItems}}
    <li class="HitchhikerProfessionalStandard-listItem">{{{this}}}</li>
    {{/each}}
  </ul>
The end result will look like the below:

View the image below for final result:

![image|690x225](https://aws1.discourse-cdn.com/turtlehead/optimized/1X/cbeb9bae4d34329455a2e64f7ebcd9255c224fa4_2_1380x450.png) 
