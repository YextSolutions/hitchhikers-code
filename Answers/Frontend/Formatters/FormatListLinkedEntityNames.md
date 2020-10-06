---
name: Formatter for Adding a Bulleted List of Linked Entity Names
description: If you’re wanting to add a list of the names in an entity list field (for example, a list of Linked Ingredients on a Recipe card), you’ll need to use a formatter to extract an array of names from the linked entity objects. Follow the instructions below!
keywords: List of Linked Entities, Bulleted List, Linked Entities, 
---
If you’re wanting to add a list of the names in an entity list field (for example, a list of Linked Ingredients on a Recipe card), you’ll need to use a formatter to extract an array of names from the linked entity objects. Follow the instructions below!

1. Add the below function to your static/js/formatters.js file

  static listNames(entityList) {
    if(!entityList) {
      return null;
    }
    let names = [];
    entityList.forEach(element => names.push(element.name));
    return names;
  }
}

2. Use the formatter in a ‘list’ section on your card.
listItems: Formatter.listNames(profile.c_ingredients),

The end result will look like the below:
image
image
700×193 16.8 KB
