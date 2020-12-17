---
name: Embedding a Video Into a Card
keywords: video, embed
dateUpdated: 12/17/2020
product: Answers
categories: Frontend, Card Customizations
communityLinks: https://hitchhikers.yext.com/community/t/embedding-a-video-into-a-card/2114
imageURL:
---

## Requirements
* You should have a video publicly uploaded to a content website. We’ll use YouTube and Vimeo as examples, but this solution is generic to content websites.
* The URL should be the embeddable URL. You can find this URL by going to share and clicking the embed option on the respective website. See Gotchas for more information.
* The URL should be HTTPS. An HTTP link will not work if you try to view the video in an HTTPS link.
* This is assuming you already have an Answers Experience and a Jambo site that is viewable in Live Preview.
* Let’s assume that the YouTube video URL is in a video list field videos and the Vimeo video URL is in a vimeo URL custom field c_vimeo.

## Step-by-step

1. Add a new card. For this, I will be referring to a new card called multilang-product-prominentvideo, a card that is branched from the multilang-product-prominentimage card. You can branch whatever card you want and name it whatever you want. See more at https://hitchhikers.yext.com/modules/ans160-core-frontend-adding-pages-and-cards/06-adding-updating-cards/

2. Direct our desired vertical to use this new card. In my case, I changed config/locations.json to have "cardType": "multilang-product-prominentvideo",.

3. Update cards/multilang-product-prominentvideo/component.js

Within our dataForRender(profile) function, we will want to get our video URL with null-checking. Note that depending on the field structure, you may have a different field to check for.

**Example 1**
```
const youtubeUrl = (profile.videos && profile.videos[0] && profile.videos[0].video && profile.videos[0].video.url) ? profile.videos[0].video.url : 'https://www.youtube.com/embed/Ww4EqJ1YUmw';
```

**Example 2**

```
const vimeoUrl = profile.c_vimeo ? profile.c_vimeo : 'https://player.vimeo.com/video/436602215';
```

In the return statement of the same file, we will add the video URL. Your function may look something like this:

```
...
  dataForRender(profile) {
  	...

    const vimeoUrl = profile.c_vimeo ? profile.c_vimeo : 'https://player.vimeo.com/video/436602215';

    return {
      title: profile.name, // The header text of the card
      url: profile.landingPageUrl, // If the card title is a clickable link, set URL here
      ...
      videoUrl: vimeoUrl, // The embeddable URL of the video to display on the card
      ...
    };
...
```
4. Update cards/multilang-product-prominentvideo/template.hbs

Now we want to use the URL in an iframe to show the embedded video player. Put this HTML wherever you would expect the video to show on the card. In my example, I am replacing the image in the prominentimage card with the video.

```hbs
  {{#if card.videoUrl}}
  <div class="HitchhikerProductProminentVideo-videoWrapper">
    <iframe class="HitchhikerProductProminentVideo-video"
      width="100%"
      height="100%"
      src="{{card.videoUrl}}"
      allowfullscreen>
    </iframe>
  </div>
  {{/if}}
```

So your template might look like this:

```hbs
<div class="HitchhikerProductProminentVideo {{cardName}}">
  {{#if card.videoUrl}}
  <div class="HitchhikerProductProminentVideo-videoWrapper">
    <iframe class="HitchhikerProductProminentVideo-video"
      width="100%"
      height="100%"
      src="{{card.videoUrl}}"
      allowfullscreen>
    </iframe>
  </div>
  {{/if}}
  <div class="HitchhikerProductProminentVideo-body">
    {{> title }}
    {{> subtitle }}
    <div class="HitchhikerProductProminentVideo-contentWrapper">
      {{> details }}
      {{> ctas }}
    </div>
  </div>
</div>
```
5. Update theme.scss

Now we will want to style the height/width of the video player. In general, you may want the height/width to take up as much of the wrapper as it can. So, you can add the CSS below. The class is specific to your card class.

```css
  .HitchhikerProductProminentVideo-video {
    width: 100%;
    height: 100%;
  }
```

## Considerations

* If you get the error (below), then you are trying to load an HTTP video on an HTTPS site. You should change your video URL to an HTTPS URL.

```
Mixed Content: The page at '<URL>' was loaded over HTTPS, but requested an insecure frame '<URL>'. This request has been blocked; the content must be served over HTTPS.
```
* If you get the error (below), then you are trying to use a video URL that is not embeddable via iFrame (determined by the website hosting the video). You should find the link that is embeddable.
  * For YouTube this is of the form https://www.youtube.com/embed/Ww4EqJ1YUmw
  * For Vimeo this is of the form https://player.vimeo.com/video/436602215
```
Refused to display '<URL>' in a frame because it set 'X-Frame-Options' to 'sameorigin'.
```