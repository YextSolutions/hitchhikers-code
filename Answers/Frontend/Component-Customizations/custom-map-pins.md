---
name: Adding Custom Map Pins & Ordinals to Indicate Different Location Types
description: A guide for adding custom map pins and ordinals to a map with multiple entity types
keywords: Custom Partials, Map Pins, Mapbox
imageURL: https://github.com/amanifarooque/hitchhikers-code/raw/master/Images/Custom-Map-Pins.png
dateUpdated: 5/6/2021
product: Answers
categories: Frontend, Component Customizations
---

## Introduction
Often times, we'll feature multiple types of locations on a single vertical - for example, Bank Branches and ATMs. In order to differentiate these entity types, we can add three things:

1. Custom map pins to indicate entity type - in this example we will change both the shape and color of the pin depending on the entity type
2. Corresponding ordinals on the location card within universal search
3. Legend to define mappings in vertical search

**Note:** in this example, we are utilizing SVG code to create a square pin and a circular pin. If you would like to use your own custom pins, simply replace the SVG code snippets in each step with your own.

## Adding the Custom Map Pins for Universal Search
For this, we'll need to override the theme. Override your `templates > universal-standard > script > map-pin.hbs` file and replace it with the code below.

This checks for the Entity Type, in this case to determine if the entity is a location or an ATM, but you can base this logic on any field. Make sure to replace the [[REPLACE_ME]] values with the desired font and background color for the map pins.

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
                <circle id="Oval" stroke-opacity="0.25" stroke="#000000" fill="[[REPLACE_ME_BACKGROUND_COLOR 1]]" cx="12" cy="17" r="11.5"></circle>
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
                <rect id="Rectangle" stroke-opacity="0.25" stroke="#000000" fill="[[REPLACE_ME_BACKGROUND_COLOR 2]]" x="0.5" y="5.5" width="23" height="23"></rect>
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
## Adding the Custom Map Pins for Vertical Search
For this step, you will be overriding your `static > js > theme-map > PinImages.js` file. In the shadowed file, we'll start by updating the `generatePin` function to accomplish two things:

1. Generate a different pin for each entity type.
2. Assign a different background color to the pin for each entity type and pin state, if desired. 

To accomplish the former, replace the current `generatePin` function with the below content.

```
generatePin ({
    backgroundColor = profile.type === 'location' ? "[[REPLACE_ME_BACKGROUND_COLOR 1]]" : "[[REPLACE_ME_BACKGROUND_COLOR 2]]",
    strokeColor = 'black',
    labelColor = 'white',
    width = '24px',
    height= '34px',
    index = '',
    profile = ''
  } = {}) {

    if (profile.type === 'location'){

      return `
      <svg width="${width}" height="${height}" viewBox="0 0 24 34" version="1.1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink">
          <g id="Styles" stroke="none" stroke-width="1" fill="none" fill-rule="evenodd">
              <g id="Elements/Buttons/MapPins/Pins/Branch/Normal">
                  <circle id="Oval" stroke-opacity="1" stroke="${strokeColor}" fill="${backgroundColor}" cx="12" cy="17" r="11.5"></circle>
              </g>
          </g>
          </svg>
      `;
    } else {
      return `
      <svg width="${width}" height="${height}" viewBox="0 0 24 34" version="1.1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink">
        <g id="Styles" stroke="none" stroke-width="1" fill="none" fill-rule="evenodd">
            <g id="Elements/Buttons/MapPins/Pins/ATM/Normal">
                <rect id="Rectangle" stroke-opacity="1" stroke="${strokeColor}" fill="${backgroundColor}" x="0.5" y="5.5" width="23" height="23"></rect>
            </g>
        </g>
        </svg>
      `; 
    }
  };
 ```

To assign different background colors to the pins for each entity type and pin state, you will update three additional functions within the same `PinImages.js` file:
1. `getDefaultPin`
2. `getHoveredPin`
3. `getSelectedPin`

For each function you will update the `backgroundColor` attribute to be different for each entity type. For example, the `getDefaultPin` would be updated as follows.
```
getDefaultPin (index, profile) {
    return this.generatePin({
      backgroundColor: profile.type === 'location' ? "[[REPLACE_ME_BACKGROUND_COLOR 1]]" : "[[REPLACE_ME_BACKGROUND_COLOR 2]]",
      strokeColor: this.defaultPinConfig.strokeColor,
      labelColor: this.defaultPinConfig.labelColor,
      width: '24',
      height: '34',
      index: '',
      profile: profile
    });
  }
```
Make a similar update to the `getHoveredPin` and `getSelectedPin` functions, utilizing whichever background colors you prefer for each pin state.

**Note:** When you are not changing the background color of pins based on entity type, the pin styling is controlled within the `pin` component in your map vertical config file. If you choose to override the pin styling as shown above, we recommend adding a comment above the `pin` component in the map vertical config file to let others looking at your code know that you are overriding those values in the `PinImages.js` file.

## Adding the Custom Ordinals for Universal Search
In order to update the styling of the ordinals on the result card, we need to employ similar logic to add a class we can target with styling based off the entity type.

In the component.js file of your forked location card, we'll define a new variable `type` that will store the entity type of the card.

```
type: profile.type == "location" ? "location " : "atm",
```

In your template.hbs, replace the `ordinalAndTitle` inline partial with the below code. This will add a class depending on the card type, either `ordinal--location` or `ordinal--atm`.
```
{{#* inline "ordinalAndTitle"}}
{{#if (any displayOrdinal card.title)}}
<div class="HitchhikerLocationStandard-ordinalAndTitle">
  {{#if displayOrdinal}}
  <div class="HitchhikerLocationStandard-ordinal HitchhikerLocationCard-ordinal {{#if card.type}}ordinal--{{card.type}}{{/if}}">
    {{result.ordinal}}
  </div>
  {{/if}}
  {{> title }}
</div>
{{/if}}
{{/inline}}
```

Lastly, add styling to modify the ordinals depending on the class. For this example, we'll change the color of the ordinals to match the pins and turn the ATM ordinals into squares to match the pin we are using.

```
.ordinal {
   &--atm {
     border-radius: 0;
     background-color: #0080ff;
   }
   &--location {
     background-color: #de0b0b;
   }
}
```
## Adding the Legend
In your location page's handlebars file, add the below 4 lines of HTML directly underneath the `templates/vertical-full-page-map/markup/map` partial.
```
<div class="Answers-legend">
  <div class="Answers-legendItem Answers-legendItem--branches">Branches</div>
  <div class="Answers-legendItem Answers-legendItem--atms">ATMs</div>
</div>
```
This will add the HTML for the legend.

### Legend CSS Styling
In terms of styling the legend, there are a few things we want to do:
1. Hide the legend on smaller screens
2. Fix the legend to the top right of the map
3. Set the color and shape of the icons for each entity type 

To hide the legend on mobile, add the following css to `answers.scss`:
```css
@media only screen and (max-width: 991px) {
  .AnswersVerticalMap .Answers
  {
    &-mapWrapper {
      .Answers-legend {
          display: none;
        }
      }
    }
}

```

To place the legend in the top right and set the color and shape of the icons, add the following css to `answers.scss` under the code you just placed. It is important to include the media query so this styling is only applied on larger screens.
```css
@media only screen and (min-width: 992px) {
.AnswersVerticalMap .Answers
  {
    &-mapWrapper
    {
      display: flex;
      flex-grow: 1;
      position: relative;

      .Answers-legend {
        position: absolute;
        top: 0;
        right: 60px;
        display: flex;
        padding: 1rem;
        background-color: #fff;
        @media only screen and (max-width: 991px) {
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
          background-color: #de0b0b;
          border-radius: 50%;
        }

        &Item--atms:before {
          background-color: #0080ff;
          border-radius: 0;
        }
      }
    }
  }
}
```
Once complete, your universal and vertical maps should look like the below screenshots!

**Universal:**
![Universal Map Custom Pins](https://user-images.githubusercontent.com/77170754/117351642-8faec600-ae73-11eb-9d0c-bac360ec17e0.PNG)


**Vertical:**
![Vertical Map Custom Pins](https://user-images.githubusercontent.com/77170754/117351668-95a4a700-ae73-11eb-85f0-663d05c2a8a6.PNG)

