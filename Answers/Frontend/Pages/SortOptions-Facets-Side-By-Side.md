---
name: SortOptions and Facets Side-by-Side
description: Adjusting filters wrapper so sortoptions and facets appear next to each other rather than stacked
keywords: SortOption, Sorting, Filter, Facet
---
SortOptions, Facets and Filters appear stacked by default in the vertical page:
![image|510x296](upload://b4dENhlz9NKSGsytIPNTMRXA6RQ.png)    

To have them appear next to each other, you can use css to format the 'filtersWrapper' div. First, you will need to uncomment the div that wraps the sorting and facets components in your 'providers.html.hbs' file and then set it to 'display:flex' in the 'answers.scss' file. For example I’ve called it Answers-searchOptions in these screenshots.

**providers.html.hbs:**
![image|499x152](upload://AoqLO38IT3MQ3Dr85lOP0Y0XSy9.png) 

**answers.scss:**
![image|282x100](upload://kDrqcql3fQyc2cSNfAVuf58qKgZ.png)  

That makes it look like this:
![image|612x215](upload://1sW0j7synVJkej6REKWjXOQdG56.png)   

You’ll probably want to tweak the padding on the components so they’re more aligned, and you can use width or flex-basis to make the components take up different amounts of space if you want.
