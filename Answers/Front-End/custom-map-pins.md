---
name: Adding Custom Map Pins & Ordinals to Indicate Different Location Types
description: 
keywords: Custom Partials, Map Pins, Mapbox
thumbnailImageURL: https://github.com/amanifarooque/hitchhikers-code/blob/master/Images/Custom-Map-Pins.png
dateAdded: 09/28/2020
dateUpdated: 09/28/2020
---

## Introduction
Often times, we'll feature multiple types of locations on a single vertical - for example, Locations and ATMs. In order to differentiate these location types, we can add three things:

1. Custom Map Pins on the Map to Indicate Location Type
2. Corresponding Ordinals on the Location Cards
3. Legend to Define Mappings

## Adding the Custom Map Pins
For this, we'll need to override the theme. Override your `templates > universal-standard > script > map-pin.hbs` and `templates > vertical-map > script > map-pin.hbs` files and replace them with the below contents.

This checks for the Entity Type of the entity, but you can base this logic after any field. Make sure to replace the [[REPLACE_ME]] values with the desired font and background color for the map pins.

```
(item, config, marker) => {
        config.label = {
          text: marker.label.toString(),
          color: 'white'
        };

      let wrapper = document.createElement('div');

      if (item.type === 'location') {
        wrapper.innerHTML = `<svg width="24px" height="34px" viewBox="0 0 24 34" version="1.1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink">
        <g id="Styles" stroke="none" stroke-width="1" fill="none" fill-rule="evenodd">
            <g id="Elements/Buttons/MapPins/Pins/Branch/Normal">
                <circle id="Oval" stroke-opacity="0.25" stroke="#000000" fill="[[REPLACE_ME_BACKGROUND_COLOR]]" cx="12" cy="17" r="11.5"></circle>
                <text id="Index" font-family="[[REPLACE_ME_FONT]]" font-size="12" font-weight="bold" line-spacing="12" fill="#FFFFFF" dominant-baseline="middle" text-anchor="middle" x="50%" y="50%">
                    ${marker.label}
                </text>
            </g>
        </g>
        </svg>`
      } else {
        wrapper.innerHTML = `<svg width="24px" height="34px" viewBox="0 0 24 34" version="1.1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink">
        <g id="Styles" stroke="none" stroke-width="1" fill="none" fill-rule="evenodd">
            <g id="Elements/Buttons/MapPins/Pins/ATM/Normal">
                <rect id="Rectangle" stroke-opacity="0.25" stroke="#000000" fill="[[REPLACE_ME_BACKGROUND_COLOR]]" x="0.5" y="5.5" width="23" height="23"></rect>
                <text id="Index" font-family="[[REPLACE_ME_FONT]]" font-size="12" font-weight="bold" line-spacing="12" fill="#FFFFFF" dominant-baseline="middle" text-anchor="middle" x="50%" y="55%">
                    ${marker.label}
                </text>
            </g>
        </g>
        </svg>`
      }

      config.wrapper = wrapper;

      return config;
    }
```
## Adding the Custom Ordinals
In order to update the styling of the ordinals on the card, we need to employ similar logic to add a class we can target with styling based off the entity type.

In the component.js of your custom location card, we'll define a new variable `type` that will store the type of the card.

```
type: profile.type == "location" ? "location " : "atm",
```

In your template.hbs, replace the `ordinalAndTitle` inline partial with the below code. This will add a class depending on the card type, either `ordinal--location` or `ordinal--atm`.
```
{{#* inline "ordinalAndTitle"}}
{{#if (any displayOrdinal card.title)}}
<div class="HitchhikerLocationStandard-ordinalAndTitle">
  {{#if displayOrdinal}}
  <div class="HitchhikerLocationStandard-ordinal {{#if card.type}}ordinal--{{card.type}}{{/if}}">
    {{result.ordinal}}
  </div>
  {{/if}}
  {{> title }}
</div>
{{/if}}
{{/inline}}
```

Lastly, add styling to modify the map pin depending on the class. For this use case, we'll just turn the ATM ordinals into squares.

```
.ordinal {
   &--atm {
     border-radius: 0;
   }
} 
```

## Adding the Legend
In your location page's handlebars file, add the below 4 lines of HTML underneath the `templates/vertical-map/markup/map` partial.
```
{{> templates/vertical-map/markup/map }} //exists in your file - place the HTML below in your file to add the legend
<div class="Answers-legend">
  <div class="Answers-legendItem Answers-legendItem--branches">Branches</div>
  <div class="Answers-legendItem Answers-legendItem--atms">ATMs</div>
</div>
```
This will add the HTML for the legend.

### Legend CSS Styling
The following accomplishes a few things:

* Fixes the legend to the top right of the map
* Hides the legend on mobile
* Sets the color and shape of the icons for each item 

Add this to your answers.scss file.

```css
.AnswersVerticalMap .Answers
{
  &-resultsWrapper
  {
    display: flex;
    flex-grow: 1;
    position: relative;

    .Answers-legend {
      position: absolute;
      top: 0;
      right: 0;
      display: flex;
      padding: 1rem;
      background-color: #fff;

      @media only screen and (max-width: $breakpoint-mobile-max)  {
        display: none;
      }

      &Item {
        font-size: .875rem;
        line-height: 1.14;
        display: flex;
        align-items: center;
      }

      &Item:before {
        content: "";
        display: inline-block;
        width: 1rem;
        height: 1rem;
        margin-right: .375rem;
      }

      &Item:not(:last-child) {
        margin-right: 1.5rem;
      }

      &Item--branches:before {
        background-color: var(--yxt-color-brand-primary);
        border-radius: 50%;
      }

      &Item--atms:before {
        background-color: var(--yxt-color-brand-primary);
        border-radius: 0;
      }
    }
  }
}

```
Once complete, your vertical will look like the below!

![image|690x225](/Images/Custom-Map-Pins.png) 
