---
layout: api
toc: true
title: Activities
---

## Overview

The Activity object represents activities made with the contact. Use it to keep
track of what you've done. An activity can't be orphan - it needs to be linked
to a contact.

When retrieving an activity, we always also return some basic information about
the related contact.

## List all the activities in your account

<url>
  GET /activities/
</url>

### Parameters

| Name | Type | Description |
| ---- | ----------- | ----------- |
| limit | integer | Indicates the page size. |
| page | integer | Indicates the page to return. |

### Response

{% highlight json %}
{
  "data": [
    {
      "id": 1,
      "object": "activity",
      "summary": "Tennis and restaurant",
      "description": "On a mangé avec papi et mamie au restaurant indien.",
      "date_it_happened": "2016-10-04T07:59:14Z",
      "activity_type": {
        "id": 9,
        "object": "activityType",
        "type": "ate_restaurant",
        "group": "food",
        "location_type": "outside",
        "created_at": "2017-01-17T17:06:34Z",
        "updated_at": "2017-01-17T17:06:34Z"
      },
      "account": {
        "id": 1
      },
      "contact": {
        "id": 1,
        "object": "contact",
        "first_name": "Henri",
        "last_name": "Troyat",
        "gender": "female",
        "is_partial": false,
        "information": {
          "dates": [
            {
              "name": "birthdate",
              "is_birthdate_approximate": "exact",
              "birthdate": "1983-10-23T19:10:42Z"
            }
          ]
        },
        "account": {
          "id": 1
        }
      },
      "created_at": "2016-10-07T11:59:14Z",
      "updated_at": "2017-05-03T01:42:28Z"
    },
    {
      "id": 2,
      "object": "activity",
      "summary": "Lunch with Dwight",
      "description": "We play handball and it was just awesome. He told me about a new girl he likes Cathy Simms, so he has to be careful.",
      "date_it_happened": "2016-10-18T13:09:47Z",
      "activity_type": {
        "id": 4,
        "object": "activityType",
        "type": "did_sport_activities_together",
        "group": "sport",
        "location_type": "outside",
        "created_at": "2017-01-17T17:06:34Z",
        "updated_at": "2017-01-17T17:06:34Z"
      },
      "account": {
        "id": 1
      },
      "contact": {
        "id": 8,
        "object": "contact",
        "first_name": "Jim",
        "last_name": "Halpert",
        "gender": "male",
        "is_partial": false,
        "information": {
          "dates": [
            {
              "name": "birthdate",
              "is_birthdate_approximate": "exact",
              "birthdate": "1978-10-01T16:20:55Z"
            }
          ]
        },
        "account": {
          "id": 1
        }
      },
      "created_at": "2016-10-18T23:58:18Z",
      "updated_at": "2017-06-07T13:09:47Z"
    },
    {
      "id": 42,
      "object": "activity",
      "summary": "Squash",
      "description": null,
      "date_it_happened": "2017-02-18T23:59:47Z",
      "activity_type": {
        "id": 4,
        "object": "activityType",
        "type": "did_sport_activities_together",
        "group": "sport",
        "location_type": "outside",
        "created_at": "2017-01-17T17:06:34Z",
        "updated_at": "2017-01-17T17:06:34Z"
      },
      "account": {
        "id": 1
      },
      "contact": {
        "id": 1,
        "object": "contact",
        "first_name": "Henri",
        "last_name": "Troyat",
        "gender": "female",
        "is_partial": false,
        "information": {
          "dates": [
            {
              "name": "birthdate",
              "is_birthdate_approximate": "exact",
              "birthdate": "1983-10-23T19:10:42Z"
            }
          ]
        },
        "account": {
          "id": 1
        }
      },
      "created_at": "2017-02-18T23:59:47Z",
      "updated_at": "2017-02-18T23:59:47Z"
    },
    {
      "id": 4203,
      "object": "activity",
      "summary": "Recognize",
      "description": "",
      "date_it_happened": "2017-10-08T00:00:00Z",
      "activity_type": {
        "id": 1,
        "object": "activityType",
        "type": "just_hung_out",
        "group": "simple_activities",
        "location_type": "outside",
        "created_at": "2017-01-17T17:06:34Z",
        "updated_at": "2017-01-17T17:06:34Z"
      },
      "account": {
        "id": 1
      },
      "contact": {
        "id": 1,
        "object": "contact",
        "first_name": "Henri",
        "last_name": "Troyat",
        "gender": "female",
        "is_partial": false,
        "information": {
          "dates": [
            {
              "name": "birthdate",
              "is_birthdate_approximate": "exact",
              "birthdate": "1983-10-23T19:10:42Z"
            }
          ]
        },
        "account": {
          "id": 1
        }
      },
      "created_at": "2017-10-08T22:06:40Z",
      "updated_at": "2017-10-08T22:06:40Z"
    }
  ],
  "links": {
    "first": "https:\/\/app.monicahq.com\/api\/activities?page=1",
    "last": "https:\/\/app.monicahq.com\/api\/activities?page=1",
    "prev": null,
    "next": null
  },
  "meta": {
    "current_page": 1,
    "from": 1,
    "last_page": 1,
    "path": "https:\/\/app.monicahq.com\/api\/activities",
    "per_page": 10,
    "to": 4,
    "total": 4
  }
}
{% endhighlight %}

## List all the activities of a specific contact

<url>
  GET /contacts/:id/activities
</url>

### Response

{% highlight json %}
{
  "data": [
    {
      "id": 1,
      "object": "activity",
      "summary": "Tennis and restaurant",
      "description": "On a mangé avec papi et mamie au restaurant indien.",
      "date_it_happened": "2016-10-04T07:59:14Z",
      "activity_type": {
        "id": 9,
        "object": "activityType",
        "type": "ate_restaurant",
        "group": "food",
        "location_type": "outside",
        "created_at": "2017-01-17T17:06:34Z",
        "updated_at": "2017-01-17T17:06:34Z"
      },
      "account": {
        "id": 1
      },
      "contact": {
        "id": 1,
        "object": "contact",
        "first_name": "Henri",
        "last_name": "Troyat",
        "gender": "female",
        "is_partial": false,
        "information": {
          "dates": [
            {
              "name": "birthdate",
              "is_birthdate_approximate": "exact",
              "birthdate": "1983-10-23T19:10:42Z"
            }
          ]
        },
        "account": {
          "id": 1
        }
      },
      "created_at": "2016-10-07T11:59:14Z",
      "updated_at": "2017-05-03T01:42:28Z"
    },
    {
      "id": 42,
      "object": "activity",
      "summary": "Squash",
      "description": null,
      "date_it_happened": "2017-02-18T23:59:47Z",
      "activity_type": {
        "id": 4,
        "object": "activityType",
        "type": "did_sport_activities_together",
        "group": "sport",
        "location_type": "outside",
        "created_at": "2017-01-17T17:06:34Z",
        "updated_at": "2017-01-17T17:06:34Z"
      },
      "account": {
        "id": 1
      },
      "contact": {
        "id": 1,
        "object": "contact",
        "first_name": "Henri",
        "last_name": "Troyat",
        "gender": "female",
        "is_partial": false,
        "information": {
          "dates": [
            {
              "name": "birthdate",
              "is_birthdate_approximate": "exact",
              "birthdate": "1983-10-23T19:10:42Z"
            }
          ]
        },
        "account": {
          "id": 1
        }
      },
      "created_at": "2017-02-18T23:59:47Z",
      "updated_at": "2017-02-18T23:59:47Z"
    },
    {
      "id": 4203,
      "object": "activity",
      "summary": "Recognize",
      "description": "",
      "date_it_happened": "2017-10-08T00:00:00Z",
      "activity_type": {
        "id": 1,
        "object": "activityType",
        "type": "just_hung_out",
        "group": "simple_activities",
        "location_type": "outside",
        "created_at": "2017-01-17T17:06:34Z",
        "updated_at": "2017-01-17T17:06:34Z"
      },
      "account": {
        "id": 1
      },
      "contact": {
        "id": 1,
        "object": "contact",
        "first_name": "Henri",
        "last_name": "Troyat",
        "gender": "female",
        "is_partial": false,
        "information": {
          "dates": [
            {
              "name": "birthdate",
              "is_birthdate_approximate": "exact",
              "birthdate": "1983-10-23T19:10:42Z"
            }
          ]
        },
        "account": {
          "id": 1
        }
      },
      "created_at": "2017-10-08T22:06:40Z",
      "updated_at": "2017-10-08T22:06:40Z"
    }
  ],
  "links": {
    "first": "https:\/\/app.monicahq.com\/api\/activities?page=1",
    "last": "https:\/\/app.monicahq.com\/api\/activities?page=1",
    "prev": null,
    "next": null
  },
  "meta": {
    "current_page": 1,
    "from": 1,
    "last_page": 1,
    "path": "https:\/\/app.monicahq.com\/api\/activities",
    "per_page": 10,
    "to": 3,
    "total": 3
  }
}
{% endhighlight %}

## Get a specific activity

<url>
  GET /activities/:id
</url>

### Response

{% highlight json %}
{
  "data": {
    "id": 2,
    "object": "activity",
    "summary": "Lunch with Dwight",
    "description": "We play handball and it was just awesome. He told me about a new girl he likes Cathy Simms, so he has to be careful.",
    "date_it_happened": "2016-10-18T13:09:47Z",
    "activity_type": {
      "id": 4,
      "object": "activityType",
      "type": "did_sport_activities_together",
      "group": "sport",
      "location_type": "outside",
      "created_at": "2017-01-17T17:06:34Z",
      "updated_at": "2017-01-17T17:06:34Z"
    },
    "account": {
      "id": 1
    },
    "contact": {
      "id": 8,
      "object": "contact",
      "first_name": "Jim",
      "last_name": "Halpert",
      "gender": "male",
      "is_partial": false,
      "information": {
        "dates": [
          {
            "name": "birthdate",
            "is_birthdate_approximate": "exact",
            "birthdate": "1978-10-01T16:20:55Z"
          }
        ]
      },
      "account": {
        "id": 1
      }
    },
    "created_at": "2016-10-18T23:58:18Z",
    "updated_at": "2017-06-07T13:09:47Z"
  }
}
{% endhighlight %}

## Create an activity

<url>
  POST /activities/
</url>

### Input

| Name | Type | Description |
| ---- | ----------- | ----------- |
| summary | string | <strong>Required</strong>. A short description of the activity. Max 255 characters. |
| description | string | An optional comment to add more details on what happened. Max 1000000 characters. |
| date_it_happened | date | <strong>Required</strong>. The date the event happened. Can be in the past or future - the latter being dumb, but well. |
| activity_type_id | integer | The ID of the type of activity that the activity is associated with. |
| contact_id | integer | <strong>Required</strong>. The ID of the contact that the call is associated with. |

### Example

{% highlight json %}
{
  "summary": "We ate at an awesome restaurant.",
  "description": "We ate way too much, we had fun and we promised we'd see each other again in a couple of weeks.",
  "date_it_happened": "2018-02-02",
  "activity_type_id": 2,
  "contact_id": 3
}
{% endhighlight %}

### Response

The API call returns an Activity object if the call succeeds.

{% highlight json %}
{
  "data": {
    "id": 4204,
    "object": "activity",
    "summary": "We ate at an awesome restaurant.",
    "description": "We ate way too much, we had fun and we promised we'd see each other again in a couple of weeks.",
    "date_it_happened": "2018-02-02T00:00:00Z",
    "activity_type": {
      "id": 2,
      "object": "activityType",
      "type": "watched_movie_at_home",
      "group": "simple_activities",
      "location_type": "my_place",
      "created_at": "2017-01-17T17:06:34Z",
      "updated_at": "2017-01-17T17:06:34Z"
    },
    "account": {
      "id": 1
    },
    "contact": {
      "id": 3,
      "object": "contact",
      "first_name": "David",
      "last_name": "Olagnier",
      "gender": "male",
      "is_partial": false,
      "information": {
        "dates": [
          {
            "name": "birthdate",
            "is_birthdate_approximate": "unknown",
            "birthdate": null
          }
        ]
      },
      "account": {
        "id": 1
      }
    },
    "created_at": "2017-10-09T14:31:54Z",
    "updated_at": "2017-10-09T14:31:54Z"
  }
}
{% endhighlight %}

## Update an activity

<url>
  PUT /activities/:id
</url>

### Input

| Name | Type | Description |
| ---- | ----------- | ----------- |
| content | string | <strong>Required</strong>. The description of the call. Max 100000 characters. |
| contact_id | integer | <strong>Required</strong>. The ID of the contact that the call is associated with. |
| called_at | date | <strong>Required</strong>. The date the called happened. Can be in the past or future - the latter being dumb, but well. |

### Example

{% highlight json %}
{
  "content": "He called, we had fun and really awesome.",
  "contact_id": 3,
  "called_at": "2018-02-02"
}
{% endhighlight %}

### Response

{% highlight json %}
{
  "data": {
    "id": 5,
    "object": "call",
    "called_at": "2017-10-07T22:29:21Z",
    "content": "He called, we had fun and really awesome.",
    "account": {
      "id": 5
    },
    "contact": {
      "id": 3,
      "object": "contact",
      "first_name": "Leslie",
      "last_name": "Knope",
      "gender": "none",
      "is_partial": false,
      "information": {
        "dates": [
          {
            "name": "birthdate",
            "is_birthdate_approximate": "unknown",
            "birthdate": null
          }
        ]
      },
      "account": {
        "id": 5
      }
    },
    "created_at": "2017-10-07T22:29:21Z",
    "updated_at": "2017-10-07T22:29:56Z"
  }
}
{% endhighlight %}

## Delete a call

<url>
  DELETE /calls/:id
</url>

### Response

The response sends back the id that was just deleted.

{% highlight json %}
{
  "deleted": true,
  "id": 31
}
{% endhighlight %}