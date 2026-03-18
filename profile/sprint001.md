# Sprint 001

## Goal
    
    For this first version, the EXTRACT layer is only responsible for making available the file it has received itself. There is no filtering and no calls to any external API. It is provided with a single public link.
    
    The TRANSFORM layer is responsible for converting the ICS format into JSON. Each ICS event becomes one JSON object. There is no data cleaning, no specific field formatting, and no date filtering.
    
    The LOAD layer receives a list of events in JSON format and converts them into SQL.

## Constraints

    As the previous sprint for the essential.

    Update : Internal ELT communication via message broker.


## Sprint duration

    2 weeks — Review and retro scheduled for Thursday, March 19, 2026.

## EXTRACT Layer

```ics
BEGIN:VEVENT
UID:john-20250303@mycompany.com
DTSTAMP:20250201T080000Z
DTSTART;TZID=Europe/Bern:20250303T090000
DTEND;TZID=Europe/Bern:20250303T150000
SUMMARY:Work session
DESCRIPTION:[acme.ch] Development session
CATEGORIES:BUSINESS
ORGANIZER:MAILTO:contact@acme.ch
ATTENDEE:MAILTO:john.doe@mycompany.com
LOCATION:https://maps.google.com/?q=46.2044,6.1432
END:VEVENT
```

## 

```json
{
"uid": "john-20250303@mycompany.com",
"dtstamp": "20250201T080000Z",
"dtstart": "20250303T090000",
"dtend": "20250303T150000",
"summary": "Work session",
"description": "[acme.ch] Development session",
"categories": "BUSINESS",
"organizer": "contact@acme.ch",
"attendee": "john.doe@mycompany.com",
"location": "https://maps.google.com/?q=46.2044,6.1432",
"timezone": "Europe/Bern"
}
```

* SQL - DDL

```sql
CREATE TABLE events (
uid TEXT PRIMARY KEY,
dtstamp TEXT,
dtstart TEXT,
dtend TEXT,
summary TEXT,
description TEXT,
categories TEXT,
organizer TEXT,
attendee TEXT,
location TEXT,
timezone TEXT
);
```

* SQL - DML

```sql
INSERT INTO events (
uid,
dtstamp,
dtstart,
dtend,
summary,
description,
categories,
organizer,
attendee,
location,
timezone
)
VALUES (
'john-20250303@mycompany.com',
'20250201T080000Z',
'20250303T090000',
'20250303T150000',
'Work session',
'[acme.ch] Development session',
'BUSINESS',
'contact@acme.ch',
'john.doe@mycompany.com',
'https://maps.google.com/?q=46.2044,6.1432',
'Europe/Bern'
);
```
