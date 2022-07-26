# Google calendar DIY
 Hi today I will try to learn the google calendar API by myself, you will follow my evolution through my push, my comments and the readme

NB : The indentation of the readme is going to change
## Author

- [@Nogaruki](https://www.github.com/nogaruki)


## 🚀 About Me
First of all, thank you for taking the time to read this file, which I will try to complete as time goes by and as I learn this technology.

To introduce myself quickly, Johann fullStack developer with a preference for the web and bigData. 
I am in MASTER MIAGE option MBDS


## Acknowledgements

 - [Google Calendar for Developers](hhttps://developers.google.com/calendar/api)
 - [Stack overflow ](https://stackoverflow.com/questions/tagged/google-calendar-api)
 - [How to write a Good readme](https://bulldogjob.com/news/449-how-to-write-a-good-readme-for-your-github-project)
 - [Readme.so]//readme.so/editor) 
 - [Ascii tree generator](https://ascii-tree-generator.com/)

## ⚠️ WARNING ⚠️
I am not at all a professional of this platfrom, or even of the API itself.
in case of mistake or misunderstanding of my part do not hesitate to correct me ! 
## Lessons Learned
Here begins all the lessons I could learn with this project.

I'll try to be as clear and constructed as possible.

### 1 Create an Google Cloud Platform Projet

#### 1.1 Set the name

My projet will be call : _API Calendar test_

#### 1.2 Set libraries

In our case we will use one library => [Google Calendar API](https://console.cloud.google.com/apis/library/calendar-json.googleapis.com?project=api-calendar-test-346413&supportedpurview=project)

### 2 Learn about Google Calendar

#### 2.1 [Overview](https://developers.google.com/calendar/api/guides/overview) 

I will try to explain with my word all contents of the overview page : 

- [Event](https://developers.google.com/calendar/api/v3/reference/events): An event created by the user or us. e.g: a birthday with a date, time, place, etc;
- [Calendar](https://developers.google.com/calendar/v3/reference/calendars) : A list of events (For me it mean a month);
- [Calendar List](https://developers.google.com/calendar/api/v3/reference/calendarList) : A list of calendars (For me it mean a year);
- [Setting](https://developers.google.com/calendar/api/v3/reference/settings) : A user preference from the Calendar UI;
- [ACL](https://developers.google.com/calendar/v3/reference/acl) : To make rule like granting access (I'm not sure it usefull for me).

#### 2.2 [Event](https://developers.google.com/calendar/api/v3/reference/events)

On this part we will see the whol of an event settings.

Here we can see an event object : 

```json
{
  "kind": "calendar#event",
  "etag": etag,
  "id": string,
  "status": string,
  "htmlLink": string,
  "created": datetime,
  "updated": datetime,
  "summary": string,
  "description": string,
  "location": string,
  "colorId": string,
  "creator": {
    "id": string,
    "email": string,
    "displayName": string,
    "self": boolean
  },
  "organizer": {
    "id": string,
    "email": string,
    "displayName": string,
    "self": boolean
  },
  "start": {
    "date": date,
    "dateTime": datetime,
    "timeZone": string
  },
  "end": {
    "date": date,
    "dateTime": datetime,
    "timeZone": string
  },
  "endTimeUnspecified": boolean,
  "recurrence": [
    string
  ],
  "recurringEventId": string,
  "originalStartTime": {
    "date": date,
    "dateTime": datetime,
    "timeZone": string
  },
  "transparency": string,
  "visibility": string,
  "iCalUID": string,
  "sequence": integer,
  "attendees": [
    {
      "id": string,
      "email": string,
      "displayName": string,
      "organizer": boolean,
      "self": boolean,
      "resource": boolean,
      "optional": boolean,
      "responseStatus": string,
      "comment": string,
      "additionalGuests": integer
    }
  ],
  "attendeesOmitted": boolean,
  "extendedProperties": {
    "private": {
      (key): string
    },
    "shared": {
      (key): string
    }
  },
  "hangoutLink": string,
  "conferenceData": {
    "createRequest": {
      "requestId": string,
      "conferenceSolutionKey": {
        "type": string
      },
      "status": {
        "statusCode": string
      }
    },
    "entryPoints": [
      {
        "entryPointType": string,
        "uri": string,
        "label": string,
        "pin": string,
        "accessCode": string,
        "meetingCode": string,
        "passcode": string,
        "password": string
      }
    ],
    "conferenceSolution": {
      "key": {
        "type": string
      },
      "name": string,
      "iconUri": string
    },
    "conferenceId": string,
    "signature": string,
    "notes": string,
  },
  "gadget": {
    "type": string,
    "title": string,
    "link": string,
    "iconLink": string,
    "width": integer,
    "height": integer,
    "display": string,
    "preferences": {
      (key): string
    }
  },
  "anyoneCanAddSelf": boolean,
  "guestsCanInviteOthers": boolean,
  "guestsCanModify": boolean,
  "guestsCanSeeOtherGuests": boolean,
  "privateCopy": boolean,
  "locked": boolean,
  "reminders": {
    "useDefault": boolean,
    "overrides": [
      {
        "method": string,
        "minutes": integer
      }
    ]
  },
  "source": {
    "url": string,
    "title": string
  },
  "attachments": [
    {
      "fileUrl": string,
      "title": string,
      "mimeType": string,
      "iconLink": string,
      "fileId": string
    }
  ],
  "eventType": string
}
```

It's a little bit longer...
Here is a list of all the detailed options: 
- _kind_ : is the nature of the JSON object in our case an event
- _etag_ : Is modified by google after each modification made by the user ( I guess it's like a kind of version ... ) 
- _id_ : I don't think I need to explain what an id is...
- _satuts_ : The status is the state that the event can take : confirmed", "attempt" or "cancelled
- _htmlLink_ : the link to the event
- _created_ : The date on which the event was created
- _updated_ : The date on which the event was updated if it was or null
- _summary_ : 	Title of the event
- _description_ : Description of the event. Can contain HTML. Optional param
- _location_ : Geographic location of the event as free-form text. Optional param
- _colorId_ : Color of the event. Optional param
- _creator_  : Contain information about the creator of that event
    - _id_ : The creator's Profile ID, if available
    - _email_ : The creator's email address, if available
    - _displayName_ : The creator's name, if available
    - _self_ : I'm not sure but it mean if the creator are the same than the calendar creator return true else return false
- _organizer_ : Contain information about the organizer of that event
    - _id_ :
    - _email_ : The organizer's email address, if available. It must be a valid email address
    - _displayName_ : The organizer's name, if available
    - _self_ : weird but, the same option than 
- _start_ : Contains the date information for the start of the event
    - _date_ : Start date of the event
    - _dateTime_ : Start date and time of the event
    - _timeZone_ : TimeZone of the location of the event. (Formatted as an IANA Time Zone Database name, e.g. "Europe/Zurich").
- _end_ : Contains the date information for the end of the event
    - _date_ : End date of the event
    - _dateTime_ : End date and time of the event
    - _timeZone_ : TimeZone of the location of the event. (Formatted as an IANA Time Zone Database name, e.g. "Europe/Zurich").
- _endTimeUnspecified_: Whether the end time is actually unspecified. An end time is still provided for compatibility reasons, even if this attribute is set to True. The default is False.
    - _recurrence[]_ : No't very know what it mean
- _recurringEventId_:For an instance of a recurring event, this is the id of the recurring event to which this instance belongs 
- _originalStartTime_: This is the time at which this event would start according to the recurrence data of the recurring event identified by recurringEventId
    - _date_:  Date of the event when it should start
    - _dateTime_: Date and time of the event when it should start
    - _timeZone_: TimeZone of the location of the event. (Formatted as an IANA Time Zone Database name, e.g. "Europe/Zurich").
- _transparency_: 2 Values: Opaque (default) means busy during the event and transparent means available during the event
- _visibility_: Visibility of the event. "default" - Uses the default visibility of calendar events; "public" - The event is public and the event details are visible to all calendar readers; "private" - The event is private and only event attendees may view event details; "private" - The event is private and only event attendees may view event details; "confidential" - The event is private.
- _iCalUID_: Event unique identifier as defined in [RFC5545](https://datatracker.ietf.org/doc/html/rfc5545#section-3.8.4.7). It is used to uniquely identify events accross calendaring systems and must be supplied when importing events via the import method.
- _sequence_: Sequence number as per iCalendar.
- _attendees[]_: The attendees of the event.
    -  _id_: The attendee's Profile ID, if available.
    - _email_: The attendee's email address, if available.
    - _displayName_: The attendee's name, if available. Optional.
    - _organizer_: Whether the attendee is the organizer of the event. Read-only. The default is False.
    - _self_: Whether this entry represents the calendar on which this copy of the event appears. Read-only. The default is False.
    - _resource_: Whether the attendee is a resource
    - _optional_: 	Whether this is an optional attendee. Optional. The default is False.
    - _responseStatus_: The attendee's response status. Possible values are: "needsAction" - The attendee has not responded to the invitation (recommended for new events); "declined" - The attendee has declined the invitation; "tentative" - The attendee has tentatively accepted the invitation; "accepted" - The attendee has accepted the invitation.
    - _comment_: The attendee's response comment. Optional.
    - _additionalGuests_: Number of additional guests. Optional. The default is 0.
- _attendeesOmitted_: Whether attendees may have been omitted from the event's representation. When retrieving an event, this may be due to a restriction specified by the maxAttendee query parameter. When updating an event, this can be used to only update the participant's response. Optional. The default is False.
- _extendedProperties_: extendedProperties
    - _private_: 	Properties that are private to the copy of the event that appears on this calendar.
      - (key): 	The name of the private property and the corresponding value.
    - _shared_: No info
      - (key): No info
- _hangoutLink_: An absolute link to the Google Hangout associated with this event. Read-only.
- _conferenceData_: The conference-related information, such as details of a Google Meet conference. We can create new conference details with the createRequest field.
    - _createRequest_:  A request to generate a new conference and attach it to the event. The data is generated asynchronously.
        - _requestId_: Id of the request field after the request respond
        - _conferenceSolutionKey_: The conference solution, such as Hangouts or Google Meet.
            - _type_: The conference solution type 4 value:"eventHangout" for Hangouts for consumers (deprecated; existing events may show this conference solution type but new conferences cannot be created); "eventNamedHangout" for classic Hangouts for Google Workspace users (deprecated; existing events may show this conference solution type but new conferences cannot be created); "hangoutsMeet" for Google Meet (http://meet.google.com); "addOn" for 3P conference providers
        - _status_: The status of the conference create request.
        - _statusCode_: The current status of the conference create request. Read-only. 3 value : "pending": the conference create request is still being processed; "success": the conference create request succeeded, the entry points are populated; "failure": the conference create request failed, there are no entry points.
    - _entryPoints_: Information about individual conference entry points, such as URLs or phone numbers.
        - _entryPointType_: The type of the conference entry point. 4 values:"video" - joining a conference over HTTP. A conference can have zero or one video entry point; "phone" - joining a conference by dialing a phone number. A conference can have zero or more phone entry points; "sip" - joining a conference over SIP. A conference can have zero or one sip entry point; "more" - further conference joining instructions, for example additional phone numbers. A conference can have zero or one more entry point. A conference with only a more entry point is not a valid conference.
        - _uri_: The URI of the entry point. The maximum length is 1300 characters. for video, http: or https: schema is required; for phone, tel: schema is required. The URI should include the entire dial sequence (e.g., tel:+12345678900,,,123456789;1234); for sip, sip: schema is required, e.g., sip:12345678@myprovider.com; for more, http: or https: schema is required.
        - _label_: The label for the URI. Visible to end users. Not localized. The maximum length is 512 characters.
        - _pin_: The PIN to access the conference. The maximum length is 128 characters.
        - _accessCode_: The access code to access the conference. The maximum length is 128 characters.
        - _meetingCode_: The meeting code to access the conference. The maximum length is 128 characters.
        - _passcode_: The passcode to access the conference. The maximum length is 128 characters.
        - _password_: The password to access the conference. The maximum length is 128 characters.
    - _conferenceSolution_: The conference solution, such as Google Meet.
      - _key_: The key which can uniquely identify the conference solution for this event.
        - _type_: The conference solution type.
      - _name_: The user-visible name of this solution. Not localized.
      - _iconUri_: The user-visible icon for this solution.
    - _conferenceId_: The Id of the conference.
    - _signature_: The signature of the conference data.
    - _notes_: Additional notes (such as instructions from the domain administrator, legal notices)
- _gadget_: A gadget that extends this event.
    - _type_: The gadget's type. Deprecated.
    - _title_: The gadget's title. Deprecated.
    - _link_: The gadget's URL. The URL scheme must be HTTPS. Deprecated.
    - _iconLink_: The gadget's icon URL. The URL scheme must be HTTPS. Deprecated.
    - _width_: The gadget's width in pixels. The width must be an integer greater than 0. Optional. Deprecated.
    - _height_: The gadget's height in pixels. The height must be an integer greater than 0. Optional. Deprecated.
    - _display_: The gadget's display mode. Deprecated. Possible values are: "icon" - The gadget displays next to the event's title in the calendar view; "chip" - The gadget displays when the event is clicke
    - _preferences_:  Preferences.
      - (key): The preference name and corresponding value.
- _anyoneCanAddSelf_:Whether anyone can invite themselves to the event (deprecated). Optional. The default is False.
- _guestsCanInviteOthers_:Whether attendees other than the organizer can invite others to the event. Optional. The default is True.
- _guestsCanModify_: Whether attendees other than the organizer can modify the event. Optional. The default is False.
- _guestsCanSeeOtherGuests_: Whether attendees other than the organizer can see who the event's attendees are. Optional. The default is True.
- _privateCopy_: If set to True, Event propagation is disabled. Note that it is not the same thing as Private event properties. Optional. Immutable. The default is False.
- _locked_:	Whether this is a locked event copy where no changes can be made to the main event fields "summary", "description", "location", "start", "end" or "recurrence". The default is False. Read-Only.
- _reminders_: Information about the event's reminders for the authenticated user.	
    - _useDefault_: Whether the default reminders of the calendar apply to the event.
    - _overrides_:If the event doesn't use the default reminders, this lists the reminders specific to the event, or, if not set, indicates that no reminders are set for this event.
        - _method_: The method used by this reminder. Possible values are: "email" - Reminders are sent via email; "popup" - Reminders are sent via a UI popup.
        - _minutes_: Number of minutes before the start of the event when the reminder should trigger.
  - _source_: 	Source from which the event was created. For example, a web page, an email message or any document identifiable by an URL with HTTP or HTTPS scheme.
    - _url_: URL of the source pointing to a resource. The URL scheme must be HTTP or HTTPS.
    - _title_: Title of the source; for example a title of a web page or an email subject
  - _attachments_: File attachments for the event.
      - _fileUrl_: URL link to the attachment.
      - _title_: Attachment title.
      - _mimeType_: Internet media type (MIME type) of the attachment.
      - _iconLink_: URL link to the attachment's icon.
      - _fileId_: ID of the attached file. Read-only.
  - _eventType_: Specific type of the event. Read-only. Possible values are: "default" - A regular event or not further specified; "outOfOffice" - An out-of-office event; "focusTime" - A focus-time event.

#### 2.3 [Calendar](https://developers.google.com/calendar/api/v3/reference/calendars)
A collection of all existing calendars.
``` json
{
  "kind": "calendar#calendar",
  "etag": etag,
  "id": string,
  "summary": string,
  "description": string,
  "location": string,
  "timeZone": string,
  "conferenceProperties": {
    "allowedConferenceSolutionTypes": [
      string
    ]
  }
}
```
Here is a list of all the detailed options

- _kind_: Is the nature of the JSON object in our case an event
- _etag_: Is modified by google after each modification made by the user ( I guess it's like a kind of version ... )
- _id_: Identifier of the calendar.
- _summary_: Title of the calendar.
- _description_: Description of the calendar. Optional.
- _location_: Geographic location of the calendar as free-form text. Optional.
- _timeZone_: The time zone of the calendar.
- _conferenceProperties_: Conferencing properties for this calendar, for example what types of conferences are allowed.
    - _allowedConferenceSolutionTypes_: The types of conference solutions that are supported for this calendar. The possible values are: "eventHangout"; "eventNamedHangout"; "hangoutsMeet"
#### 2.4 [Calendar](https://developers.google.com/calendar/api/v3/reference/calendars)
The collection of calendars in the user's calendar list. 

```json
{
  "kind": "calendar#calendarListEntry",
  "etag": etag,
  "id": string,
  "summary": string,
  "description": string,
  "location": string,
  "timeZone": string,
  "summaryOverride": string,
  "colorId": string,
  "backgroundColor": string,
  "foregroundColor": string,
  "hidden": boolean,
  "selected": boolean,
  "accessRole": string,
  "defaultReminders": [
    {
      "method": string,
      "minutes": integer
    }
  ],
  "notificationSettings": {
    "notifications": [
      {
        "type": string,
        "method": string
      }
    ]
  },
  "primary": boolean,
  "deleted": boolean,
  "conferenceProperties": {
    "allowedConferenceSolutionTypes": [
      string
    ]
  }
}
```

## Starting development 👨‍💻
After everything we learn, we can start some test.
We will proceed step by step.
Already in stages:

1. Setting up the workspace 
2. Creation of the test file in [php v8.1.0](https://www.php.net/releases/8.1/en.php)
3. Creation of a calendar
4. Creation of an event
5. Adding the event to the calendar

#### 1. Setting up the workspace
Before everything we have to setting up our workspace:

__Create a credencial for our project__: To creato one go to your google API project > Credntial > Configure consent Screen > Select 'External' > Create > fill the form > Next > Next > Add test users (You) > Next > Go back to credntial > Create credencials > Select OAUth client ID > type : Web app. > Modify the name if you want > create. And now you have everything you need

- We have to create a longin google form because to link our event or calendar to a google account we have to have their autorisation.
- The Credential are here to communicate with the API.

__Create the file tree__:
```bash
Create-event/
├─ config.php
├─ index.php
├─ addEvent.php
├─ eventSync.php
├─ GoogleCalendarApi.class.php
├─ css/
│  ├─ style.css
Create-Calendar/
```
It will be completed after
#### 2. Creation of the test file
Now we will start to dev ! 
You cna follow my progress in the folder [Create-event](https://github.com/nogaruki/google-calendar-DIY/tree/Create-event)

#### 3. Creation of a calendar
Now that we know how the calendar class is constituted, we will see how to instantiate it:

#### 4. Creation of an event

#### 5. Adding the event to the calendar

## Screenshots
