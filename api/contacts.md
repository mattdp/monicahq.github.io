---
layout: api
toc: true
title: Contacts
---

## Overview

The Contact object is the core of what Monica is all about. The API allows you
to create, delete and update your contacts. You can retrieve individual contacts
as well as a list of all your contacts.

It's important to understand that all the people in Monica are Contact objects -
that includes a kid or a significant other (also called partner). However, there
are two types of contacts:
* `real` contacts
* `partial` contacts.

A `real` contact is a contact that you have a lot of information about -
therefore you can attach activities, reminders, notes, etc... to the object.
Real contacts have their own contact sheet.

A `partial` contact, however, is a person you don't have a lot of information
about. This is typically the spouse of one of your friend, or their child for
whom you only need to remember the names and the date of birth. A `partial`
contact is always linked to a `real` contact. Partial contacts don't have their
own contact sheet and shouldn't have one.

A `partial` contact has the flag `is_partial` set to `true`.

When creating `real` contacts, the only rule is the uniqueness of the email
address in the user's account. If you try to use the same email address when
creating another contact in the account, the API will return an error.

## List all your contacts

<url>
  GET /contacts/
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
      "object": "contact",
      "first_name": "John",
      "last_name": "Doe",
      "gender": "female",
      "is_partial": false,
      "last_called": null,
      "last_talked_to": null,
      "information": {
        "family": {
          "kids": {
            "total": 1,
            "kids": [
              {
                "id": 79172,
                "object": "contact",
                "first_name": "Héloïse",
                "last_name": null,
                "gender": "female",
                "is_partial": true,
                "information": {
                  "dates": [
                    {
                      "name": "birthdate",
                      "is_birthdate_approximate": "exact",
                      "birthdate": "2011-11-22T02:21:49Z"
                    }
                  ]
                },
                "account": {
                  "id": 1
                }
              }
            ]
          },
          "partners": {
            "total": 1,
            "partners": [
              {
                "id": 76934,
                "object": "contact",
                "first_name": "Roger",
                "last_name": null,
                "gender": "male",
                "is_partial": true,
                "information": {
                  "dates": [
                    {
                      "name": "birthdate",
                      "is_birthdate_approximate": "approximate",
                      "birthdate": "1976-01-01T02:43:04Z"
                    }
                  ]
                },
                "account": {
                  "id": 1
                }
              }
            ]
          },
          "progenitors": {
            "total": 0,
            "progenitors": [
              {
                "id": 76934,
                "object": "contact",
                "first_name": "Henri",
                "last_name": null,
                "gender": "male",
                "is_partial": true,
                "information": {
                  "dates": [
                    {
                      "name": "birthdate",
                      "is_birthdate_approximate": "approximate",
                      "birthdate": "1976-01-01T02:43:04Z"
                    }
                  ]
                },
                "account": {
                  "id": 1
                }
              }
            ]
          }
        },
        "dates": [
          {
            "name": "birthdate",
            "is_birthdate_approximate": "exact",
            "birthdate": "1983-10-23T19:10:42Z"
          }
        ],
        "career": {
          "job": null,
          "company": null
        },
        "avatar": {
          "gravatar_url": false
        },
        "food_preferencies": "Love oranges and pepper."
      },
      "contact": {
        "emails": [
          {
            "name": "personal",
            "email": "john.doe@gmail.com"
          }
        ],
        "phone_numbers": [
          {
            "name": "home",
            "phone_number": "314 443 1231"
          }
        ],
        "social_network": {
          "facebook_profile_url": "https://facebook.com/johndoe",
          "twitter_profile_url": "https://twitter.com/johndoe",
          "linkedin_profile_url": "https://linkedin.com/johndoe"
        },
        "addresses": [
          {
            "name": "home",
            "street": "1234 Street",
            "city": "Montreal",
            "province": "QC",
            "postal_code": "21LK23",
            "country_id": 2,
            "country_name": "Canada"
          }
        ]
      },
      "tags": [
        {
          "id": 856,
          "object": "tag",
          "name": "friend",
          "name_slug": "friend",
          "account": {
            "id": 1
          },
          "created_at": "2017-09-26 20:51:59",
          "updated_at": "2017-09-26T20:51:59Z"
        },
        {
          "id": 857,
          "object": "tag",
          "name": "college",
          "name_slug": "college",
          "account": {
            "id": 1
          },
          "created_at": "2017-09-26 20:51:59",
          "updated_at": "2017-09-26T20:51:59Z"
        }
      ],
      "data": {
        "number_of_calls": 0,
        "number_of_notes": 1,
        "number_of_activities": 2,
        "number_of_reminders": 1,
        "number_of_tasks": 0,
        "number_of_gifts": 1,
        "number_of_debts": 0
      },
      "account": {
        "id": 1
      },
      "created_at": "2016-09-04T02:42:51Z",
      "updated_at": "2017-06-13T14:57:53Z"
    }
  ],
  "links": {
    "first": "https://app.monica.com/api/contacts?page=1",
    "last": "https://app.monica.com/api/contacts?page=15",
    "prev": null,
    "next": "https://app.monica.com/api/contacts?page=2"
  },
  "meta": {
    "current_page": 1,
    "from": 1,
    "last_page": 15,
    "path": "https://app.monica.com/api/contacts",
    "per_page": "2",
    "to": 2,
    "total": 30
  }
}
{% endhighlight %}

## Get a specific contact

<url>
  GET /contacts/:id
</url>

{% highlight json %}
{
  "id": 1,
  "object": "contact",
  "first_name": "John",
  "last_name": "Doe",
  "gender": "female",
  "is_partial": false,
  "last_called": null,
  "last_talked_to": null,
  "information": {
    "family": {
      "kids": {
        "total": 1,
        "kids": [
          {
            "id": 79172,
            "object": "contact",
            "first_name": "Héloïse",
            "last_name": null,
            "gender": "female",
            "is_partial": true,
            "information": {
              "dates": [
                {
                  "name": "birthdate",
                  "is_birthdate_approximate": "exact",
                  "birthdate": "2011-11-22T02:21:49Z"
                }
              ]
            },
            "account": {
              "id": 1
            }
          }
        ]
      },
      "partners": {
        "total": 1,
        "partners": [
          {
            "id": 76934,
            "object": "contact",
            "first_name": "Roger",
            "last_name": null,
            "gender": "male",
            "is_partial": true,
            "information": {
              "dates": [
                {
                  "name": "birthdate",
                  "is_birthdate_approximate": "approximate",
                  "birthdate": "1976-01-01T02:43:04Z"
                }
              ]
            },
            "account": {
              "id": 1
            }
          }
        ]
      },
      "progenitors": {
        "total": 0,
        "progenitors": [
          {
            "id": 76934,
            "object": "contact",
            "first_name": "Roger",
            "last_name": null,
            "gender": "male",
            "is_partial": true,
            "information": {
              "dates": [
                {
                  "name": "birthdate",
                  "is_birthdate_approximate": "approximate",
                  "birthdate": "1976-01-01T02:43:04Z"
                }
              ]
            },
            "account": {
              "id": 1
            }
          }
        ]
      }
    },
    "dates": [
      {
        "name": "birthdate",
        "is_birthdate_approximate": "exact",
        "birthdate": "1983-10-23T19:10:42Z"
      }
    ],
    "career": {
      "job": null,
      "company": null
    },
    "avatar": {
      "gravatar_url": false
    },
    "food_preferencies": null
  },
  "contact": {
    "emails": [
      {
        "name": "personal",
        "email": null
      }
    ],
    "phone_numbers": [
      {
        "name": "home",
        "phone_number": null
      }
    ],
    "social_network": {
      "facebook_profile_url": "https://facebook.com/johndoe",
          "twitter_profile_url": "https://twitter.com/johndoe",
          "linkedin_profile_url": "https://linkedin.com/johndoe"
    },
    "addresses": [
      {
        "name": "home",
        "street": "1234 Plessis",
        "city": "Montreal",
        "province": null,
        "postal_code": null,
        "country_id": 2,
        "country_name": "Canada"
      }
    ]
  },
  "tags": [],
  "data": {
    "number_of_calls": 0,
    "number_of_notes": 1,
    "number_of_activities": 2,
    "number_of_reminders": 1,
    "number_of_tasks": 0,
    "number_of_gifts": 1,
    "number_of_debts": 0
  },
  "account": {
    "id": 1
  },
  "created_at": "2016-09-04T02:42:51Z",
  "updated_at": "2017-06-13T14:57:53Z"
}
{% endhighlight %}

## Create a contact

<url>
  POST /contacts/
</url>

### Input

If a field is not required, you can send the `null` value as the content of the field.

| Name | Type | Description |
| ---- | ----------- | ----------- |
| first_name | string | <strong>Required</strong>. The first name of the contact. Max 50 characters. |
| last_name | string | Last name of the contact. Max 100 characters. |
| gender | string | <strong>Required</strong>. The gender of the contact. Can be `male`, `female` or `unknown`. |
| birthdate | string | Format: 'YYYY-MM-DD HH:MM:SS'. The birthdate of the contact. |
| is_birthdate_approximate | string | Can be `exact`, `approximate` or `unknown`. |
| age | integer | The age of the contact. |
| email | string | The email address of the contact. Max 255 characters. |
| phone_number | string | The phone number of the contact. Max 255 characters. |
| job | string | The job title of the contact. Max 255 characters. |
| company | string | The company which employs the contact. Max 255 characters. |
| street | string | The street where the contact lives. Max 255 characters. |
| city | string | The city where the contact lives. Max 255 characters. |
| province | string | The province where the contact lives. Max 255 characters. |
| postal_code | string | The postal code where the contact lives. Max 255 characters. |
| country_id | integer | The country id of the country. You need to retrieve the list of countries that we support and send the right country id from this list. |
| food_preferencies | string | The food preferencies of the contact. Max 100000 characters. |
| facebook_profile_url | string | The Facebook URL of the contact. Max 255 characters. |
| twitter_profile_url | string | The Twitter URL of the contact. Max 255 characters. |
| linkedin_profile_url | string | The LinkedIn URL of the contact. Max 255 characters. |

### Example

{% highlight json %}
{
  "first_name":"henri",
  "last_name":"troyat",
  "gender":"male",
  "birthdate":"1981-02-02 00:00:00",
  "is_birthdate_approximate":"approximate",
  "age":30,
  "email":"henri.troyat@gmail.com",
  "phone_number":"455 321 2123",
  "job":"Animator",
  "company":"Star Wars",
  "street":"21 Jump Street",
  "city":"Montreal",
  "province":"QC",
  "postal_code":"H2K1N1",
  "country_id":3,
  "food_preferencies":"Fish and fresh potatoes.",
  "facebook_profile_url":"https://facebook.com/johndoe",
  "twitter_profile_url":"https://twitter.com/johndoe",
  "linkedin_profile_url":"https://linkedin.com/johndoe"
}
{% endhighlight %}

### Response

The API call returns a contact object if the call succeeds.

{% highlight json %}
{
  "id": 93145,
  "object": "contact",
  "first_name": "henri",
  "last_name": "troyat",
  "gender": "male",
  "is_partial": null,
  "last_called": null,
  "last_talked_to": null,
  "information": {
    "family": {
      "kids": {
        "total": 0,
        "kids": []
      },
      "partners": {
        "total": 0,
        "partners": []
      },
      "progenitors": {
        "total": 0,
        "progenitors": []
      }
    },
    "dates": [
      {
        "name": "birthdate",
        "is_birthdate_approximate": "approximate",
        "birthdate": "1987-01-01T19:19:36Z"
      }
    ],
    "career": {
      "job": "Animator",
      "company": "Star Wars"
    },
    "avatar": {
      "gravatar_url": false
    },
    "food_preferencies": "Fish and fresh potatoes."
  },
  "contact": {
    "emails": [
      {
        "name": "personal",
        "email": "henri.troyat@gmail.com"
      }
    ],
    "phone_numbers": [
      {
        "name": "home",
        "phone_number": "455 321 2123"
      }
    ],
    "social_network": {
      "facebook_profile_url": "https://facebook.com/johndoe",
      "twitter_profile_url": "https://twitter.com/johndoe",
      "linkedin_profile_url": "https://linkedin.com/johndoe"
    },
    "addresses": [
      {
        "name": "home",
        "street": "21 Jump Street",
        "city": "Montreal",
        "province": "QC",
        "postal_code": "H2K1N1",
        "country_id": 3,
        "country_name": "France"
      }
    ]
  },
  "tags": [
    {
      "id": 856,
      "object": "tag",
      "name": "friend",
      "name_slug": "friend",
      "account": {
        "id": 1
      },
      "created_at": "2017-09-26 20:51:59",
      "updated_at": "2017-09-26T20:51:59Z"
    },
    {
      "id": 857,
      "object": "tag",
      "name": "college",
      "name_slug": "college",
      "account": {
        "id": 1
      },
      "created_at": "2017-09-26 20:51:59",
      "updated_at": "2017-09-26T20:51:59Z"
    }
  ],
  "data": {
    "number_of_calls": 0,
    "number_of_notes": 0,
    "number_of_activities": 0,
    "number_of_reminders": 0,
    "number_of_tasks": 0,
    "number_of_gifts": 0,
    "number_of_debts": 0
  },
  "account": {
    "id": 1
  },
  "created_at": "2017-09-18T19:19:36Z",
  "updated_at": "2017-09-18T19:19:36Z"
}
{% endhighlight %}

## Update a contact

<url>
  PUT /contacts/:id
</url>

### Input

| Name | Type | Description |
| ---- | ----------- | ----------- |
| first_name | string | <strong>Required</strong>. The first name of the contact. Max 50 characters. |
| last_name | string | Last name of the contact. Max 100 characters. |
| gender | string | <strong>Required</strong>. The gender of the contact. Can be `male`, `female` or `unknown`. |
| birthdate | string | Format: 'YYYY-MM-DD HH:MM:SS'. The birthdate of the contact. |
| is_birthdate_approximate | string | Can be `exact`, `approximate` or `unknown`. |
| age | integer | The age of the contact. |
| email | string | The email address of the contact. Max 255 characters. |
| phone_number | string | The phone number of the contact. Max 255 characters. |
| job | string | The job title of the contact. Max 255 characters. |
| company | string | The company which employs the contact. Max 255 characters. |
| street | string | The street where the contact lives. Max 255 characters. |
| city | string | The city where the contact lives. Max 255 characters. |
| province | string | The province where the contact lives. Max 255 characters. |
| postal_code | string | The postal code where the contact lives. Max 255 characters. |
| country_id | integer | The country id of the country. You need to retrieve the list of countries that we support and send the right country id from this list. |
| food_preferencies | string | The food preferencies of the contact. Max 100000 characters. |
| facebook_profile_url | string | The Facebook URL of the contact. Max 255 characters. |
| twitter_profile_url | string | The Twitter URL of the contact. Max 255 characters. |
| linkedin_profile_url | string | The LinkedIn URL of the contact. Max 255 characters. |

### Example

{% highlight json %}
{
  "first_name":"henri",
  "last_name":"troyat",
  "gender":"male",
  "birthdate":"1981-02-02 00:00:00",
  "is_birthdate_approximate":"approximate",
  "age":30,
  "email":"henri.troyat@gmail.com",
  "phone_number":"455 321 2123",
  "job":"Animator",
  "company":"Star Wars",
  "street":"21 Jump Street",
  "city":"Montreal",
  "province":"QC",
  "postal_code":"H2K1N1",
  "country_id":3,
  "food_preferencies":"Fish and fresh potatoes.",
  "facebook_profile_url":"https://facebook.com/johndoe",
  "twitter_profile_url":"https://twitter.com/johndoe",
  "linkedin_profile_url":"https://linkedin.com/johndoe"
}
{% endhighlight %}

### Response

{% highlight json %}
{
  "id": 93145,
  "object": "contact",
  "first_name": "henri",
  "last_name": "troyat",
  "gender": "male",
  "is_partial": null,
  "last_called": null,
  "last_talked_to": null,
  "information": {
    "family": {
      "kids": {
        "total": 0,
        "kids": []
      },
      "partners": {
        "total": 0,
        "partners": []
      },
      "progenitors": {
        "total": 0,
        "progenitors": []
      }
    },
    "dates": [
      {
        "name": "birthdate",
        "is_birthdate_approximate": "approximate",
        "birthdate": "1987-01-01T19:19:36Z"
      }
    ],
    "career": {
      "job": "Animator",
      "company": "Star Wars"
    },
    "avatar": {
      "gravatar_url": false
    },
    "food_preferencies": "Fish and fresh potatoes."
  },
  "contact": {
    "emails": [
      {
        "name": "personal",
        "email": "henri.troyat@gmail.com"
      }
    ],
    "phone_numbers": [
      {
        "name": "home",
        "phone_number": "455 321 2123"
      }
    ],
    "social_network": {
      "facebook_profile_url": "https://facebook.com/johndoe",
      "twitter_profile_url": "https://twitter.com/johndoe",
      "linkedin_profile_url": "https://linkedin.com/johndoe"
    },
    "addresses": [
      {
        "name": "home",
        "street": "21 Jump Street",
        "city": "Montreal",
        "province": "QC",
        "postal_code": "H2K1N1",
        "country_id": 3,
        "country_name": "France"
      }
    ]
  },
  "tags": [],
  "data": {
    "number_of_calls": 0,
    "number_of_notes": 0,
    "number_of_activities": 0,
    "number_of_reminders": 0,
    "number_of_tasks": 0,
    "number_of_gifts": 0,
    "number_of_debts": 0
  },
  "account": {
    "id": 1
  },
  "created_at": "2017-09-18T19:19:36Z",
  "updated_at": "2017-09-18T19:19:36Z"
}
{% endhighlight %}

## Delete a contact

<url>
  DELETE /contacts/:id
</url>

### Response

The response sends back the id that was just deleted.

{% highlight json %}
{
  "deleted": true,
  "id": 93135
}
{% endhighlight %}
