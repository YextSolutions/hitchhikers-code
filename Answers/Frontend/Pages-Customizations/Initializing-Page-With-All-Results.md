---
name: Initializing Answers Vertical Page With All Results
description: All results appear on a page when there is an empty vertical search
keywords: all results, blank search
dateUpdated: 10/5/2020
product: Answers
categories: Frontend, Pages Customizations
---

# Update
This Hitchhikers Code Bank page is being deprecated as part of the Fall '22 Release on November 16th 2022. Please reference our new [Search documentation](https://hitchhikers.yext.com/docs/search) for this content and post in the community with any questions.

---

To display results on an empty vertical search, you’ll want to take two steps:

**1. Set up your Search Bar component to allow empty search.**
On verticals, we will automatically show all results if a user conducts an empty search. By adding `"allowEmptySearch": true` , we allow this behavior. You’ll find this in the `componentSettings` object in your pages’s config.json file.

```
    "SearchBar": {
      "placeholderText": "Search for Stories", // The placeholder text in the answers search bar
      "allowEmptySearch": true
    },
```

**2. Set a default initial search to that empty search.**
Now that we’re allowing an empty search, we can set that as the default when someone lands on the page. You can find this within `pageSettings` in the `search` object.

```
  "pageSettings": {
     "search": {
       "verticalKey": "faqs", // The vertical key from your search configuration
       "defaultInitialSearch": "" // Enter a default search term
     }
  },  
```
