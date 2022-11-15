---
name: Embed static answers experience
description: Embed a static answers experience based on a query as website content.
keywords: Embed, stand-alone, seperate
dateUpdated: 10/5/2020
product: Answers
categories: Frontend, Pages Customizations
---

# Update
This Hitchhikers Code Bank page is being deprecated as part of the Fall '22 Release on November 16th 2022. Please reference our new [Search documentation](https://hitchhikers.yext.com/docs/search) for this content and post in the community with any questions.

---

1. **Create a second Answers Frontend Experience**. Because we need to add some additional customizations that are not desired for the main search, we'll need a separate frontend experience. This however can leverage the same Answers *backend* if you so choose.
2. **Add a page for your FAQs**. Here, we'll do something a bit different - instead of creating a `universal-standard` page named `index`, create a `vertical-standard` page named index. From our training, you'll note that this page will now automatically appear at the root of your site. Configure the index.json to point to your FAQs vertical.
3. **Add a default initial search**. Because you want certain FAQs to populate on landing, you can indicate a default search that should be run when someone lands on your page. This is only available for vertical pages.
```json
 "pageSettings": {
     "search": {
       "verticalKey": "faqs", // The vertical key from your search configuration
       "defaultInitialSearch": "faqs" // Enter a default search term
     }
```
3. **Hide your Navigation Bar**. You can do this by commenting out the relevant partials in your `index.html.hbs` file. 

Comment out both navigation partials below remove the navigation bar:
```
{{!-- {{> templates/vertical-standard/script/navigation }} --}}
{{!-- {{> templates/vertical-standard/markup/navigation }} --}}
```
You can also optionally remove the footer component
```
    {{!-- <div class="Answers-footer">
      {{> layouts/yext-logo }}
      {{> templates/vertical-standard/markup/locationbias }}
    </div> --}}
```
4. **Hide the Search Bar _*not recommended_**. You can optionally hide the search bar via the CSS below in your answers.scss file; however, we recommend keeping the search bar for easy discovery of FAQs.
```
.Answers-navWrapper {
  display: none
}
```

5. **Inject this onto your page**. Publish your site to the production domain of your choosing. Afterwards, you can inject your static answers component using a javascript snippet:
```
<div id="answers-container"></div>
<script src="[[production url]]/iframe.js"></script>
```
For more information on the integration, please see our integration site: https://answers-integration.netlify.app/create-search-results-page/

Your end result will look something like this! 
![image|689x456](https://aws1.discourse-cdn.com/turtlehead/optimized/2X/b/b0455078473d36b236b990af501d7cce00cc4278_2_1378x912.png) 
