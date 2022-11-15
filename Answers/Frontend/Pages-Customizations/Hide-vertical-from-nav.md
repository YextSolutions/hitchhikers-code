---
name: Hide vertical from nav bar
keywords: Vertical, hide, links
dateUpdated: 10/29/2020
product: Answers
categories: Frontend, Page Customizations

---

# Update
This Hitchhikers Code Bank page is being deprecated as part of the Fall '22 Release on November 16th 2022. Please reference our new [Search documentation](https://hitchhikers.yext.com/docs/search) for this content and post in the community with any questions.

---

## Option 1

Remove your links.html.hbs and links.json files, and place the configuration for your links vertical in your index.json file, under verticalsToConfig.

```js
    "links": { // The vertical key from your search configuration
      // "label": "", // The name of the vertical in the section header and the navigation bar
      // "verticalLimit": 15, // The result count limit for vertical search
      // "universalLimit": 5, // The result count limit for universal search
      "cardType": "link-standard", // The name of the card to use - e.g. accordion, location, customcard 
      "icon": "link", // The icon to use on the card for this vertical
      "universalSectionTemplate": "standard"
    }
```
![image|2096×1382](https://aws1.discourse-cdn.com/turtlehead/optimized/2X/7/70ee862880fce2558ef16bf22b5a0322214c9bc9_2_1035x681.png)

You likely would also want to hide the View All button in the Links vertical, so that users aren’t directed to a dead page. You can use the following css as an example.
```css
.HitchhikerResultsStandard--links .HitchhikerResultsStandard-viewMore {
    display: none;
}
```
*Impact: Links would only show in Universal search, and there would be no vertical page for Links.*

## Option 2

Keep your links.html.hbs and links.json files to maintain the page for the Links vertical. Add the following object to your index.json file.

```js
  "excludedVerticals": [
    "links"
 ]
```
![image|2108×1302](https://aws1.discourse-cdn.com/turtlehead/optimized/2X/2/2309f0ca6db0abc2d4542a710608ae92f395fc05_2_1035x639.png)

*Impact: This will hide the Links tab in the navigation bar, but users will still be able to navigate to view more than 10 links in the vertical by clicking “View More”*
