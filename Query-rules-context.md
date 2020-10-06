---
name: Query rules context
description: Usng Query Rules to Filter Results that only pertain to specific locations.
keywords: Query rules, locations, filter
---

**Overview:** To filter results to only those that pertain to the online location (ie. website) a user originates from, Query Rules detects the URL a user searched from, maps it to a value of the custom field “Query Rules Location”, and filters the result set to only the entities that have that value populated in the custom field.

For example, take someone searching from a page on https://location1.com/. We will see that a user searched from a page matching this subdomain, map that to the custom field value of “Location 1”, and filter the results such that only results with the field “Query Rules Location” containing “Location 1” appear in the results.

**Instructions**

*For this example*, the 3 entity types are Locations, FAQs, and Services.

**Mapping URLs to the “Query Rules Locations” custom field**

1. Created a custom field called “Query Rules Location” that has a multi-option selections for each location URL.
2. Within each entity type, select which Query Rule location the type falls under within the “Query Rules Location” field.
3. Once all of your locations are labeled correctly, also update the Query Rules Location custom field for all FAQs and Services and click on all the location options within the field. Note: This is so that all FAQs and Services will surface in the Answers experience for all location pages.

Example:
![image|1008x740](https://aws1.discourse-cdn.com/turtlehead/optimized/1X/535ecd2e389b0ed7de4997ae0a69e2944abf268c_2_892x594.png)

**Create Saved Search Filters**

1. In order to filter results in Query Rules based on the location page the user is searching from, we need to create saved search filters for each location page.
2. Within the knowledge graph, create an advanced filter with the following search criteria:
*Fields with Data includes any of Query Rules Location*
*Query Rules Location includes Choose the Location you want to filter for*
3. Apply filter and save the Filter.

Example:
![image|1262×286](https://aws1.discourse-cdn.com/turtlehead/optimized/1X/76c5df71565da0fbf491749963b1ce9163597f2c_2_624x141.png)

**Creating Query Rule in Search Configuration**

1. Navigate to Answers → Experiences → Search Configuration.
2. Scroll to the bottom where you will find the “Rules” section.
3. Criteria will be the “referrerPageURLRegex” with the following syntax for the specific URL: "^.location1.com”
4. Action will be “ADD_FILTER”.
5. Filter using “savedFilterID”. Depending on the location you are filtering for, copy the Saved Filter ID for that location and copy it for the “$eq” portion.
6. Within “verticalKeys”, include the verticals you would like to filter for.

Example:
![image|1318×800] (https://aws1.discourse-cdn.com/turtlehead/optimized/1X/c0025426379594c9bbbc64832790ca562fb5f97a_2_936x568.png)


