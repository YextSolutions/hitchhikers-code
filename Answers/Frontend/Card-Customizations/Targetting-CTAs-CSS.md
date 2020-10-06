---
name: Targetting specific CTAs using CSS
keywords: CTA, CSS, target, vertical
dateUpdated: 10/6/2020
---
You can use the parent/child relationships in the HTML of the cards to help target specific CTA classes, so you can modify CTAs in different verticals.

You’ll notice that the card is wrapped in classes that relate to the card type. For Restaurants, if I have a custom restaurant card, you’ll see there’s a restaurant class wrapping the card.
![image|2952×738] (https://aws1.discourse-cdn.com/turtlehead/original/2X/7/7153d363bd91b49da23c6b40e5870d934134c387.png2952×738)

Similarly, if you're using an event-standard card for an Events vertical, you'll see a event-standard class wrapping this div.

![image|2988×838] (https://aws1.discourse-cdn.com/turtlehead/optimized/2X/6/63e4443431435991c52489f3a8c68279d18c30bb_2_690x193.png)

In CSS, when you identify two classes with a space in-between, it will look for all instances of the second class nested within the first (here’s a refresher on CSS selectors).

So, you can add the following CSS:

```css
  .restaurant .HitchhikerCTA {
    color: white;
    background-color: black;
    padding: 1rem;
  }

  .event-standard .HitchhikerCTA {
    color: black;
    border: 1px solid black;
    padding: 1rem;
  }
  ```
  
To produce the following two CTA styles:
![image|1488×1704] (https://aws1.discourse-cdn.com/turtlehead/optimized/2X/2/2fde9530b007a4cb5b3020e30f24c78924f35634_2_436x500.png)