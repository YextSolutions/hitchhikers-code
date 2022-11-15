---
name: SortOptions and Facets Side-by-Side
description: Adjusting filters wrapper so sortoptions and facets appear next to each other rather than stacked for vertical-map pages
keywords: SortOption, Sorting, Filter, Facet
dateUpdated: 10/5/2020
product: Answers
categories: Frontend, Pages Customizations
--- 

# Update
This Hitchhikers Code Bank page is being deprecated as part of the Fall '22 Release on November 16th 2022. Please reference our new [Search documentation](https://hitchhikers.yext.com/docs/search) for this content and post in the community with any questions.

---
To have them appear next to each other, you can add a div that wraps the sorting and facets components in your 'providers.html.hbs' file and then format it with `display:flex` in the `answers.scss` file. For example I’ve called it Answers-searchOptions in the example below:

**providers.html.hbs:**
```
<div class="Answers-resultsWrapper">
        <div class="Answers-resultsColumn">
          {{> templates/vertical-map/markup/spellcheck }}
          <div class="Answers-searchOptions">
            {{> templates/vertical-map/markup/sortoptions }} --}}
            {{> templates/vertical-map/markup/facets }}
          </div>
```    

**answers.scss:**
```
  &-searchOptions {
    display: flex;
  }
```    

The result will look like this:

![image|612x215](https://aws1.discourse-cdn.com/turtlehead/original/1X/0a47850ba41b638b91a6ea08e12157620c921ebc.png)   

You’ll probably want to tweak the padding on the components so they’re more aligned, and you can use width or flex-basis to make the components take up different amounts of space if you want.
