---
layout: api
toc: true
title: General concept
---

## Overview

This document describes how to use Monica's API. This document is heavily
inspired by [GitHub's](https://developer.github.com/v3) and
[Stripe's](https://stripe.com/docs/api) API. Please use the API in a nice way
and don't be a jerk.

## Current version

By default, all requests to <url>https://app.monicahq.com/api</url> receive the
v1 version of the API.

## Schema

All API access is over HTTPS, and accessed from the
<url>https://app.monicahq.com/api</url> URL. All data is sent and received as
JSON.

{% highlight bash %}
Server: nginx/1.11.9
Content-Type: application/json
Transfer-Encoding: chunked
Connection: keep-alive
Cache-Control: no-cache, private
Date: Thu, 14 Sep 2017 02:24:19 GMT
X-RateLimit-Limit: 60
X-RateLimit-Remaining: 58
{% endhighlight %}

All timestamps return in ISO 8601 format:

<url>
YYYY-MM-DDTHH:MM:SSZ
</url>

## HTTP verbs

Monica tries to use the appropriate HTTP verbs wherever it can. Note that the
`PATCH` HTTP verb is not used right now.

| Verb | Description |
| ---- | ----------- |
| GET | Used for retrieving resources. |
| POST | Used for creating resources. |
| PUT | Used for replacing resources or collections. |
| DELETE | Used for deleting resources. |

## Authentication

## Pagination

Requests that return multiple items will be paginated to 10 items by default.
You can specify further pages with the `?page` parameter. For some resources,
you can also set a custom page size up to 100 with the `?limit` parameter.
Omitting the `?page` parameter will return the first page.

<url>
curl 'https://app.monicahq.com/api/contacts?page=2&limit=100'
</url>

## Rate limiting

The returned HTTP headers of any API request show your current rate limit status:

{% highlight bash %}
Date: Thu, 14 Sep 2017 02:24:19 GMT
X-RateLimit-Limit: 60
X-RateLimit-Remaining: 58
{% endhighlight %}

| Header name | Description |
| ----------- | ----------- |
| X-RateLimit-Limit | The maximum number of requests you're permitted to make per hour. |
| X-RateLimit-Remaining | The number of requests remaining in the current rate limit window. |

If you exceed the rate limit, an `429` error response returns with a JSON:

{% highlight bash %}
X-RateLimit-Limit   60
X-RateLimit-Remaining   0
Retry-After 55
{% endhighlight %}

{% highlight json %}
{
    "error": {
        "message": "Too many attempts, please slow down the request.",
        "error_code": 34
    }
}
{% endhighlight %}
