# iCal #

An AppleScript to quickly add events to iCal for [Alfred App](http://www.alfredapp.com)
Based on the iCal extension by [Gianni Rondini](http://twitter.com/giannivt)

## Installation ##

Download and double click the `ical.alfredextension`

## How to Use ##

`cal [description] [at time] [on date] [today] [tomorrow] [in location] [using calendar] [alarm [type] minutes] [attendee email]`

`description` must come first, all of the others can be specified in any order you want.

If  you include multiple `at`, `in`, `using` or any combination of `on`, `today`, or `tomorrow`, the last one will always be used.

Multiple `alarm` and `email` statements are allowed.

`description` - name of the iCal Event.  It can be left out to create a blank event.
`at` - specify the hour and minutes an event is to happen.  Either use am/pm indicator (space optional) or 24 hour time notation.  Leading zeros are allowed.  Minutes can be supplied.  All of the following are valid:

 * `1am` or `1` would be interpreted as 01:00 or 1:00 AM
 * `1pm` or '13' would be interpreted as 13:00 or 1:00 PM
 * `1:30am` or `01:30` would be interpreted as 01:30 or 1:30 AM
 * `1:30pm` or `13:30` would be interpreted as 13:30 or 1:30 PM
 * 
`on`, `today`, `tomorrow` - specify the date for an event.  Date formats accepted are based on the Formats pane of your International settings in System Preferences.

`in` - free text `location` to specify where your event is happening

`using` - `calendar` should be the name of the calendar you want to put the event on.  Defaults to the first available calendar in iCal

`alarm` - can be specified multiple times. `minutes` is a positive number to alarm after the event has started, negative number for before the event.  `type` defaults to `sound`, can also be `email`.
 
 `attendee` - add attendee invitation to the event.  Multiple attendees can have their own individual `attendee` line or be specified by separating email addresses with a space.  So both `attendee fred@example.com wilma@example.com` and `attendee fred@example.com [other statements] attendee wilma@example.com` are equally valid.
 
## Configuration ##

There is no need to configure anything unless you want to modify some of the default behaviors or separators.

### Calendar ###

If you you do not specify `using` we'll use the first calendar in iCal to schedule your event under.  If you would like a different default calendar edit Line 6 (`DefaultCalendar`) to be the name of whatever calendar you would like to schedule your events under.

### Alarms ###

By default there are no alarms set.  If you would like to set default alarms modify lines 12 (`AlarmTimes`) and/or 19 (`EmailTimes`) of the script.

```applescript
	set AlarmTimes to {}
```

```applescript
	set EmailTimes to {}
```

If you wanted an a Message w/ Sound alarm 15 and 30 minutes prior as well as an email 1 hour prior, you would do the following:

```applescript
	set AlarmTimes to {-15, -30}
```

```applescript
	set EmailTimes to {-60}
```

### Meeting Length ###

The default meeting length is currently 1 hour and there is no ability to set this (yet) when you are creating events.  Line 26 of the script (`MeetingLength`) can be change to any real number to indicate how many hours you want a meeting to be set as.

### Localization ###

If you wish to localize the keywords, edit lines 31-40.  Please notice that 2 of these keywords (`until` and `for`) are not currently in use but may be used in the future.

