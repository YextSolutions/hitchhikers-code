---
name: Formatting the Footer Module
description: Example of footer CSS
keywords: Page Builder, Flex
dateUpdated: 10/5/2020
---

Hi Ella!

Great question. There seems to be two components that you want to change here - 1) adjust position properties for the Footer links to move them to right hand side and 2) adjust the social icons to also be on the left and stacked above the links.

For both of these, we can leverage the power of FlexBox. You can read more about FlexBox here (https://css-tricks.com/snippets/css/a-guide-to-flexbox/), but we'll review the basics you'll need to accomplish this layout.

First, let's take a look at the HTML layout of this footer section.

```html
<div class="row align-items-center">
    <div class="col-md-8 footer-links d-flex flex-wrap">
        <a class="footer-link lp-param lp-param-link1Text lp-param-link1Url" href="https://www.federalrealty.com/privacy-policy/" data-pages-analytics="clicktowebsite">Privacy Policy</a>
        <a class="footer-link lp-param lp-param-link2Text lp-param-link2Url" href="http://www.theavenueatwhitemarsh.com/contact-us/" data-pages-analytics="clicktowebsite">Contact Us</a>
    </div>
    <div class="social-icons col-md-4 d-flex flex-wrap justify-content-md-end justify-content-center pt-sm-2 pt-2">
        <a href="https://www.facebook.com/TheAvenueAtWhiteMarsh" class="social-icon lp-param lp-param-facebook" data-pages-analytics="clicktowebsite"><img class="icon-img" src="https://assets.sitescdn.net/landingpages/modules/footer/images/facebook.svg" alt="facebook icon"></a>
        <a href="https://www.pinterest.com/theavenueatwm/" class="social-icon lp-param lp-param-pinterest" data-pages-analytics="clicktowebsite"><img class="icon-img" src="https://assets.sitescdn.net/landingpages/modules/footer/images/pinterest.svg" alt="pinterest icon"></a>
        <a href="//twitter.com/https://twitter.com/THEAVENUEatWM" class="social-icon lp-param lp-param-twitter" data-pages-analytics="clicktowebsite"><img class="icon-img" src="https://assets.sitescdn.net/landingpages/modules/footer/images/twitter.svg" alt="twitter icon"> </a>
        <a href="//instagram.com/https://www.instagram.com/theavenueatwhitemarsh/" class="social-icon lp-param lp-param-instagram" data-pages-analytics="clicktowebsite"><img class="icon-img" src="https://assets.sitescdn.net/landingpages/modules/footer/images/instagram.svg" alt="instagram icon"></a>
    </div>
</div>

```
In Flexbox, we use the parent elements (the containers) to control the position of child elements (the elements within the parent). Here, we have a few layers:
* The container with classes `row align-items-center` that contains two divs - one containing the footer links, and one containing the social icons
* Parent containers for the `footer-links` and `social-icons`, each containing several `a` tags within

The first step we'll take is define how the two divs within the overarching parent container are positioned. The CSS to do this is below:

```css
.align-items-center {
    display: flex;
    flex-direction: column-reverse;
    align-items: flex-end !important;
}
```
By adding the rule `display: flex;`, we're noting that we'll use the flexbox layout for this container & its immediate children. 

`flex-direction` allows us to determine the order of the elements - we can choose between:
* `row` (side-by-side, elements in the order they appear in the HTML)
* `column` (stacked, elements in the order they appear in the HTML)
* `row-reverse` (side-by-side, elements in the reverse order that they appear in the HTML)
* `column-reverse` (stacked, elements in the reverse order that they appear in the HTML)

Here, because we want the links *underneath* the social icons, we'll opt for `column-reverse`.

Lastly, we want the child items to align to the end of the container, so we'll add `align-items: flex-end;`. The `!important` is needed in this case to override the Page Builder built-in CSS, but use this sparingly.

We'll take a similar approach to stack the footer links on top of one another, using the below CSS.
```
.footer-links {
    display: flex;
    flex-direction: column;
    align-items: flex-end;
}
```
![image|690x108](https://aws1.discourse-cdn.com/turtlehead/original/2X/1/1f446b4f825c14ce7551aad3e99e3f411ed75b20.png) 

We'd also recommend ensuring you test across browsers for changes like these - you may want to tweak the mobile behavior further as well.