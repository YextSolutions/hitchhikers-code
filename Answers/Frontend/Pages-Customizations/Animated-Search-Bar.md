---
name: Adding an Animated Search Bar to the Results Page
description: Adding typed animated text to the Answers results page
keywords: search bar, results, animated, js, javascript
dateUpdated: 12/14/2020
product: Answers
categories: Frontend, Page Customizations
---
The default Answers search bar has a static text label, but you can modify the experience to make the search bar have a typing text animation that pulls from the [hardcoded prompts](https://hitchhikers.yext.com/modules/ans110-core-config-query-suggestions/02-hardcoded-prompts/) you have already set. Below are the steps you need to follow:

1. Go to layouts > headerincludes.hbs and add the following:
```html
<script src="https://cdn.jsdelivr.net/npm/typed.js@2.0.11"></script>
<script src="https://cdn.jsdelivr.net/npm/axios/dist/axios.min.js"></script>
```
2.  Next, you will click into tools and then override theme. You will need to override the on-ready.js file within script. Once you have that file open, you will add the following code (make sure to include the correct variables for your experience):

```js
const apiKey= "INSERT_API_KEY";
const experienceKey= "INSERT_EXPERIENCE_KEY";
const experienceVersion = "PRODUCTION";
const businessId= "INSERT_BUSINESS_ID";
const locale = "en";

  // Make API Call to Options
  var url = 'https://liveapi-cached.yext.com/v2/accounts/me/answers/autocomplete';
  url += '?v=20190101';
  url += '&api_key=' + apiKey;
  url += '&sessionTrackingEnabled=false';
  url += '&experienceKey=' + experienceKey;
  url += '&input=';
  url += '&version=' + experienceVersion;
  url += '&locale=' + locale;
  axios.get(url).then(function(response) {
    // Get strings from response
    const strings = response.data.response.results.map(function(r) {
      return r.value;
    });
    // Set up Typed
    var options = {
      strings: strings,
      showCursor: true,
      cursorChar: "|",
      typeSpeed: 45,
      backSpeed: 20,
      smartBackspace: true,
      loop: true,
      startDelay: 500,
      backDelay: 2000,
      attr: "placeholder",
    };
    var typed = new Typed(".js-yext-query", options);
  });
```

### **The Result:**

![image](https://aws1.discourse-cdn.com/turtlehead/original/2X/4/4bcbd52a475fd7dcef319864790759f5af47f855.gif) 