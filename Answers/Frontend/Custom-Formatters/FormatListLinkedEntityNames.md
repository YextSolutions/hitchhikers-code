---
name: Formatter for Adding a Bulleted List of Linked Entity Names
description: If you’re wanting to add a list of the names in an entity list field (for example, a list of Linked Ingredients on a Recipe card), you’ll need to use a formatter to extract an array of names from the linked entity objects. Follow the instructions below!
keywords: List of Linked Entities, Bulleted List, Linked Entities
dateUpdated: 10/5/2020
---
If you’re wanting to add a list of the names in an entity list field (for example, a list of Linked Ingredients on a Recipe card), you’ll need to use a formatter to extract an array of names from the linked entity objects. Follow the instructions below!

1. Add the below function to your static/js/formatters.js file
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

2. Use the formatter in a ‘list’ section on your card.
```js
listItems: Formatter.listNames(profile.c_ingredients),
```

![image]The end result will look like the below:
(https://aws1.discourse-cdn.com/turtlehead/original/1X/f905b55e5e2af0de3d74f4335b9e703371b83172.png)

