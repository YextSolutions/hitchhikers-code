---
name: Formatter for Adding a Bulleted List of Call to Action Links
description: To add a list of links from a custom field made up of a list of Call to Actions (for example, a list of ways to contact someone on a Professional card), you’ll need to use a formatter to extract an array of items from the list of Call to Actions.
keywords: Call to Action, Bulleted List, List of Links, Custom Formatters
dateUpdated: 10/5/2020

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

See below for final result:

![image|690x225](https://aws1.discourse-cdn.com/turtlehead/optimized/1X/cbeb9bae4d34329455a2e64f7ebcd9255c224fa4_2_1380x450.png) 
