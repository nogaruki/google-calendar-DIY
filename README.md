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
 - [Readme generator](https://readme.so/editor) 
 

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
## Screenshots

Not avaible now

