---
name: Add Hours Open Status to Card
description: Formatter to display a custom field of type hours to a card with open status.
keywords: Hours, Open, Open Status, Custom Formatters
communityLink: https://hitchhikers.yext.com/community/t/add-drive-thru-hours-open-status-to-card/1667
dateUpdated: 09/15/2020

---
1. Override the Theme (formatter.js File)
We need to override the theme here so we can pass a “field” parameter to the hours formatter. This will allow us to pass Drive thru hours in addition to main hours.

Copy the existing openStatus formatter and create a openStatusV2 formatter that accepts a field.

  static openStatusV2(profile, field, locale = 'en-US') {
    if (!field) {
      return '';
    }

    const days = this._formatHoursForAnswers(field, profile.timeZoneUtcOffset);
    if (days.length === 0) {
      return '';
    }


    const { time, day } = this._calculateYextDayTime(new Date(), profile.timeZoneUtcOffset);

    /**
     * @type {{days: Object[], time: number, day: string, dayIndex: number }}
     */
    let hours = {
        days: days,
        time: time,
        day: day,
        dayIndex: this._dayToInt(day),
      };

    hours.yextDays = this._prepareIntervals(hours);
    let { status, nextTime, nextDay } = this._getStatus(hours);
    hours.nextTime =  nextTime;
    hours.nextDay = nextDay;
    hours.status = status;

    return this._getTodaysMessage({ hoursToday: hours, isTwentyFourHourClock: false, locale: locale });
  }
  
Since you’re now shadowing this file, just be careful in future theme upgrades to not overwrite this.

2. Update the component.js File
Use the new formatter for the existing hours field, and then add a new field driveThru to store the drive thru hours data.

hours: Formatter.openStatusV2(profile, profile.hours),
driveThru: Formatter.openStatusV2(profile, profile.c_driveThruHours),

3. Update the template.hbs file
3a - Add the card.driveThru to the if statement.
3b -Add the div for the driveThru hours only if card.driveThru is populated.
3c - Add headings (Lobby & Drive Thru).

 {{#if (any card.hours card.driveThru card.services)}}
  <div class="HitchhikerLocationStandard-infoCol">
    {{#if card.hours}}
    <div class="HitchhikerLocationStandard-hoursText">
      <strong>Lobby: </strong>{{{card.hours}}}
    </div>
    {{/if}}
    {{#if card.driveThru}}
    <div class="HitchhikerLocationStandard-hoursText driveThru">
      <strong>Drive-Thru: </strong>{{{card.driveThru}}}
    </div>
    {{/if}}
    {{#if card.services}}
    <div class="HitchhikerLocationStandard-services">
      <span class="HitchhikerLocationStandard-servicesLabel">
        Services:
      </span>
      <span>
        {{#each card.services~}}{{this}}{{#unless @last}}, {{/unless}}{{~/each}}
      </span>
    </div>
    {{/if}}
  </div>
  {{/if}}
  
4. Updates to the Answers.scss file
Add this for quick styling for the labels, but you can take this further if you want to add more.

 .HitchhikerLocationStandard-hoursText {
    strong {
      font-weight: bold;
    }
  }
