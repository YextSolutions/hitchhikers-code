---
name: Setting up Linked Entity Fields in Search
description: Best practices for setting up linked entities to appear in search
keywords: linked entitity, custom field, subfield
dateUpdated: 10/6/2020
product: Answers
categories: Backend, Searchable Fields
---

To make linked entities searchable, you can use the neme subfield of the custom linked entity fields that you created. As an example, if the custom field you want to be searchable for providers is c_linkedSpecialties then you will need to add the following to `Answers > Experiences > Search Configuration`:

```
      "searchableFields": {
        "c_linkedSpecialties.name": {
          "textSearch": true
        },
```
