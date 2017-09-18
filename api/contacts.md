---
layout: api
---

# Overview

The Contact object is the core of what Monica is all about. The API allows you
to create, delete and update your contacts. You can retrieve individual contacts
as well as a list of all your contacts.

It's important to understand that all the people in Monica are Contact objects -
that includes a kid or a significant other (also called partner). However, there
are two types of contacts:
* `real` contacts
* `partial` contacts.

A `real` contact is a contact that you have a lot of information about - therefore you can attach activities, reminders, notes, etc... to the object. Real contacts have their own contact sheet.

A `partial` contact, however, is a person you don't have a lot of information about. This is typically the spouse of one of your friend, or their child for whom you only need to remember the names and the date of birth. A `partial` contact is always linked to a `real` contact. Partial contacts don't have their own contact sheet and shouldn't have one.

## List all your contacts
## Get a specific contact
## Edit a contact
## Delete a contact
