---
name: Setting up Linked Entity Fields in Search
description: Best practices for setting up linked entities to appear in search
keywords: linked entity, custom field, subfield
dateUpdated: 10/6/2020
product: Answers
categories: Backend, Searchable Fields
---
## Overview
For certain entity relationships, it might be useful to be able to search by linked entity names. For example, if you have a Recipe entity with linked Ingredients, you might want to search by a linked Ingredient to surface Recipes using it. See below for how to implement.

## Instructions
To make linked entities searchable, you can use the name subfield of the custom linked entity fields that you created. As an example, if the custom field you want to be searchable for providers is c_linkedSpecialties then you will need to add the following to `Answers > Experiences > Search Configuration`:

```
      "searchableFields": {
        "c_linkedSpecialties.name": {
          "textSearch": true
        },
```

Note that only the name property is available to be searchable from the linked entity. Similarly, you can only access the name of a linked entity on the front-end.
