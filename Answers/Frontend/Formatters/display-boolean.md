---
name: Format Boolean Value to Display on Card
description: Display text based off the value of the boolean.
keywords: Boolean, JS, Accepting New Patients, Custom Formatters
---
Hey @Sarah_Dougherty! Really cool use-case here that you're setting up for your brand's experience. In order to "transform" the boolean field, I recommend using custom (yet simple) JS formatter in your **formatters.js** file. In order to add this formatter, you'll want to go to **Jambo Commands** -> **Override Theme** -> **static > js > formatters.js**.

Here, you can add the following code within the file:

    static acceptingStatus(profile) {
      if (profile.acceptingNewPatients) {
        return 'Accepting New Patients';
      } 
      return '';
    }

This formatter is essentially translating the **"True"** boolean value to **"Accepting New Patients"**. From here, you'll want to update the **details** mapping within your card's **compnent.js** file. Please update it such that it transforms the data using your JS formatter:

**details: Formatter.acceptingStatus(profile),**




See below for final result:

![image|690x225](https://aws1.discourse-cdn.com/turtlehead/optimized/1X/cbeb9bae4d34329455a2e64f7ebcd9255c224fa4_2_1380x450.png) 

You can also target the details to make the Accepting New Patients stand out a bit more. Let me know if you have any follow up questions when implementing this!