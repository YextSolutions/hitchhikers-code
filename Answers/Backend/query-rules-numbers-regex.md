---
name: Query rules - string of numbers
description: Surfacing a specific FAQ when a string of numbers is searched.
keywords: Query rules, string, regex
imageURL: 
dateUpdated: 10/6/2020
communityLinks:
product: Answers
categories: Backend, Query Rules
---

When implementing query ruels there may be scenarios where you would like to taregt a **type* of query. You can find the full list of Query Rules criteria here (https://hitchhikers.yext.com/tracks/answers-advanced/ans302-query-rules/02-criteria/). You can target a 5-7 number string via RegEx (Regular expressions). Regular expressions allow you to search for a pattern of characters, and allows more flexibility when you’re looking for query matches.

Without getting into the weeds, the below query rule will work to boost any specified FAQs when a 5 to 7 digit number is searched.

```json
"rules": [
{
  "criteria": {
    "searchTermMatchesRegex": "\\b\\d{5,7}\\b"
  },
  "actions": [
    {
      "actionType": "BOOST_ENTITIES",
      "entityIds": [
        "FAQ-0"
      ],
      "verticalKey": "faqs"
    }
  ]
}
```

For anyone looking to learn more about RegEx or validate their expressions I highly recommend visiting https://regexone.com/and https://regex101.com/ respectively.