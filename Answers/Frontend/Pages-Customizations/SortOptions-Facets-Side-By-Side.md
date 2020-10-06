---
name: SortOptions and Facets Side-by-Side
description: Adjusting filters wrapper so sortoptions and facets appear next to each other rather than stacked
keywords: SortOption, Sorting, Filter, Facet
---
SortOptions, Facets and Filters appear stacked by default in the vertical page:
![image|510x296](upload://b4dENhlz9NKSGsytIPNTMRXA6RQ.png)    

To have them appear next to each other, you can use css to format the 'filtersWrapper' div. First, you will need to uncomment the div that wraps the sorting and facets components in your 'providers.html.hbs' file and then set it to 'display:flex' in the 'answers.scss' file. For example I’ve called it Answers-searchOptions in these screenshots.

**providers.html.hbs:**
![image|499x152](https://aws1.discourse-cdn.com/turtlehead/original/1X/ff1146f3385c4337268fbdf688d1ac0ee3744d45.png) 

**answers.scss:**
![image|282x100](https://aws1.discourse-cdn.com/turtlehead/original/1X/90a0df40a771ff37748f8d9ae49acf6e05c4b1a5.png)  

That makes it look like this:
![image|612x215](https://aws1.discourse-cdn.com/turtlehead/original/1X/0a47850ba41b638b91a6ea08e12157620c921ebc.png)   

You’ll probably want to tweak the padding on the components so they’re more aligned, and you can use width or flex-basis to make the components take up different amounts of space if you want.
