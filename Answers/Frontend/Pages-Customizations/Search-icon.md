---
name: Change icon in search bar
keywords: search, icon, yext, logo
dateUpdated: 10/29/2020
product: Answers
categories: Frontend, Page Customizations
---
## Overview

This code snippet allows the user to update the icon in the right hand of the search bar from the standard Yext logo to a custom image in a JAMBO experience.

*Note: this should only be done for paid clients; AFTs should always have the Yext logo in the search bar unless there has been executive approval*

## The Code

1. Add a custom image to your static/assets/image folder [full instructions here](https://hitchhikers.yext.com/modules/ans160-core-frontend-adding-pages-and-cards/07-assets-and-static-files/)

2. In each vertical .js file you'll see a search bar configuration: 

```json
"SearchBar": {
      "placeholderText": "Search...",
      "allowEmptySearch": true
}
```

3. Add in your custom image using “customIconUrl”
```json
"SearchBar": {
      "placeholderText": "Search...", 
      "allowEmptySearch": true,
      "customIconUrl": "static/assets/images/[[imageurl]]"
```

4. Repeat this process for each vertical .json file

Your search bar image should now be updated for Answers Site
