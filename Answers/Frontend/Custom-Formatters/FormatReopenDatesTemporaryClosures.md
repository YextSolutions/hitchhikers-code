---
name: Formatter For Adding Reopen Dates & Temporary Closures
description: If you’re working on helping a brand with temporary closures, and the brand is leveraging the reopen date field, you can showcase this information within Answers by using a custom formatter. You may find this strategy particularly useful or location entity types and healthcare facility entity types amidst COVID19.
keywords: COVID, Reopen Date, Temporary Closure, Custom Formatters, Hours
dateUpdated: 10/5/2020
product: Answers
categories: Frontend, Custom Formatters
---
In order to set this up, follow these steps:

1. Add the below to your static/js/formatter.js file

  static reopenStatus(profile) {
          if (profile.hours && profile.hours.reopenDate) {
            return 'This location is temporarily closed';
          } else {
            return 'This location is operating under normal business hours';
          }
        }
        
2. Add the below to you card mappings JS file

subtitle: Formatter.reopenStatus(profile),

This will produce the following result:

image
image
1390×938 93.5 KB
