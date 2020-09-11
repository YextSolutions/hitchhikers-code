Hi Jessie,

Great question! In order to do this the right way, we'll need to do three things:
1. Update the custom card's `component.js` to pass through the Email field, as well as the details needed to successfully fire an Analytics event.
2. Update the custom card's `template.hbs` to add a section for Email that correctly formats the link.
3. *Optional* - add CSS to update the link styling

For **Step 1**, add these two attributes to your card's data mappings in your **component.js** file.
```js
      email: profile.emails ? profile.emails[0] : null,
      emailEventOptions: this.addDefaultEventOptions(),
```
The `email` attribute passes in the first email address of the Emails field (if populated), otherwise returns null. Modify this to align with the field that stores your email addresses.

The `emailEventOptions` attribute just passes the standard data (entityId, universal vs. vertical search, etc) that allows us to fire an Analytics event.

Now comes **Step 2**, updating our template. Once this data is accessible to our card, we'll make a series of updates to our **template.hbs** file.

Assuming you're using the professional-standard or location-standard card as a starting point, this process will be pretty similar to how the address and phone are added to the card.

First, we'll create an ``{{>email}}`` partial. Add the below within your template.hbs file, preferably below the `{{#*inline 'phone'}}` partial.
```
{{#*inline 'email'}}
{{#if card.email}}
<div class="HitchhikerLocationStandard-email">
  <a href="mailto:{{card.email}}"
    data-eventtype="EMAIL"
    data-eventoptions='{{json card.emailEventOptions}}'
    target="_blank">
    {{card.email}}
  </a>
</div>
{{/if}}
{{/inline}}
```
Here, we've added a new class `HitchhikerLocationStandard-email` which allows us to style this email in the future. We're then adding a link - to create an email link, simply add `mailto:` in front of the email address. We're also passing `data-eventtype` and `data-eventoptions` so that an EMAIL event fires when a user clicks on the link. Lastly, the text of the link will be the email itself, enclosed within the `<a>` tag.

Now that we've defined the partial, we need to reference it so it's placed on the card. If you're forking from a location-standard or professional-standard card, you can navigate to the `contactInfo` partial in your file and add the email partial underneath the address & phone.

```hbs
{{#* inline "contactInfo"}}
<div class="HitchhikerLocationStandard-contactInfo">
  {{#if (any card.phone card.address card.email)}}
  <div class="HitchhikerLocationStandard-core">
    {{> address }}
    {{> phone }}
    {{> email }}
  </div>
  {{/if}}
```
You'll see that we both added the `card.email` in the #if statement, as well as added the partial below the address and phone partials.


Lastly, for **Step 3**, I'll add a bit of CSS to make the email address appear as a link.

```css
   .HitchhikerLocationStandard-email {
      color: var(--yxt-color-brand-primary);
      margin-top: .5rem;

      a {
        text-decoration: underline;

        &:hover {
          text-decoration: none;
        }
      }       
    }
```
The end result will look like the below:
![image|690x176](upload://aUgGw8k9Nf8HKvajteZRYswrOnl.png)  

Let me know if this helps!
