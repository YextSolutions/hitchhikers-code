---
name: Formatter for Adding a Bulleted List of Linked Entity Names
description: If you’re wanting to add a list of the names in an entity list field (for example, a list of Linked Ingredients on a Recipe card), you’ll need to use a formatter to extract an array of names from the linked entity objects. Follow the instructions below!
keywords: List of Linked Entities, Bulleted List, Linked Entities
communityLinks: https://hitchhikers.yext.com/community/t/formatter-for-adding-a-bulleted-list-of-linked-entity-names/649
dateUpdated: 06/08/2020
product: Answers
categories: Frontend, Custom Formatters
---
If you’re wanting to add a list of the names in an entity list field (for example, a list of Linked Ingredients on a Recipe card), you’ll need to use a formatter to extract an array of names from the linked entity objects. Follow the instructions below!

1. Add the below function to your static/js/formatters.js file. The syntax of the formatter will depend on the version of the theme you're on. Take a look at the formatters in the theme/static/js/formatters-internal.js file if you are unsure.
```js
  static listNames(entityList) {
    if(!entityList) {
      return null;
    }
    let names = [];
    entityList.forEach(element => names.push(element.name));
    return names;
  }
}
```
Newer themes will use this format:
```js
  export function listNames(entityList) {
    if(!entityList) {
      return null;
    }
    let names = [];
    entityList.forEach(element => names.push(element.name));
    return names;
  }
```

2. Use the formatter in a ‘list’ section on your card.
```js
listItems: Formatter.listNames(profile.c_ingredients),
```

![image]The end result will look like the below:
(https://aws1.discourse-cdn.com/turtlehead/original/1X/f905b55e5e2af0de3d74f4335b9e703371b83172.png)

