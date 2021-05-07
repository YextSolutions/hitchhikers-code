---
name: Override Card HBS file to add custom HTML
keywords: card, custom card, add to card
dateUpdated: 05/07/2021
product: Answers
categories: Frontend, Card Customizations
communityLinks:
imageURL:
---

## Overview

Sometimes, we want to add a net-new component to a card in our Answers experience, or otherwise change the way the information on the card is layed out. This requires making changes to the card's Handlebars, or HBS, file.

Some use cases of this include:

* Adding a [third CTA](https://hitchhikers.yext.com/modules/ans325-changing-page-card-structure/02-card-layout/)
* Add an [additional list](https://hitchhikers.yext.com/modules/ans325-changing-page-card-structure/02-card-layout/) to the card
* Add an icon to the [distance label](https://hitchhikers.yext.com/modules/ans325-changing-page-card-structure/02-card-layout/)
* Add a custom label based on a field in the Knowledge Graph, like for which doctors offer video visits (see below)

## The Code

To begin creating a card for healthcare professionals with a custom label, begin by forking the card you wish to use for your professionals. In this example, we are forking the ```professional-standard``` card and calling it ```professional-override```

Update your ```providers.json``` file to use the new ```professional-override``` card.

Now, we need to update the ```component.js``` file for your new ```professional-override``` card so that we are bringing in the field from the Knowledge Graph that lets us know if the provider has video visits. We have added a Yes/No field called c_videoVisits to our Healthcare Professional entities to facilitate this logic. This custom field is set to "Yes" for one of our professionals, Sam Jones. Whenever c_videoVisits is set to "Yes", we want our videoVisits text to read "Video Visits Available". We can add this to our ```component.js``` file for your new ```professional-override``` underneath where we define the ```url```


```js
videoVisits: profile.c_videoVisits ? 'Video Visit Available' : null,
```

Then, open the ```template.hbs``` file for your new ```professional-override``` card. This is where we will add our new label to the card. Under ```{{> details }}```, add the code:
```hbs
{{#if card.videoVisits}}
        <div class="HitchhikerProfessionalStandard-videoVisits" style="display:inline-flex;">
          <div> <img src="https://a.mktgcdn.com/p/j38Wh9RPbHfgAKFHdF41oyHf0I2jGNjzbW2uaeRElAU/103x103.png" style="width: 15px;height: 15px;margin-right:5px;"></div>
            {{card.videoVisits}}
        </div>
        {{/if}}
```
This checks our component file to see if videoVisits is populated, and, if so, adds the video icon image available at the URL as well as the videoVisits text. Remember, in our config file for the card, we defined videoVisits to be populated with "Video Visits Available" whenever the field c_videoVisits in our Knowledge Graph is "Yes".

You can also update the formatting in the answers.scss file by adding:

```css
.HitchhikerProfessionalStandard-videoVisits
  {
  font-weight: bold;
  font-size: 12px;
  padding-top: 10px
}
```

## The Result

This code adds the icon and text "Video Visits Available" to providers if the associated Knowledge Graph field, c_videoVisits is "Yes".

![image](https://user-images.githubusercontent.com/77289753/117494449-542efd00-af42-11eb-9ab1-0dbdfcc48608.png)


## Additional Resources

Additional background on HTML is available on [Hitchhikers](https://hitchhikers.yext.com/modules/tech101-intro-to-html/)

If you want to learn even more about HTML , there are many resources online that can help supplement your knowledge.

* [W3Schools](https://www.w3schools.com/html/html_intro.asp)
* [Traversy Media’s Video for Beginners](https://www.youtube.com/watch?v=UB1O30fR-EE)
* [Code Academy](https://www.codecademy.com/learn/learn-html)

