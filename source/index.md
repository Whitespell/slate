---
title: API Reference

language_tabs:
  - shell
  - Javascript
  - Java
  - Objective-C

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='http://github.com/tripit/slate'>Documentation Powered by Slate</a>

search: true
---

#Basics

##API

The API is located at ```https://peakapi.whitespell.com```


Data | Format | Info
--- | ----- | ----
Payload | JSON only | This is to make it a lot easier to parse and post
Requests | Query String Parameters | Make sure to also use SSL
Encryption | 256-bit SSL | Make sure to also use SSL in your requests for the sake of our users
Max string length | 255 | Don't post strings longer than 255 characters :-)


##Design Schema

In order to better understand the API, here you can find a design schema of the endpoints. Please email [pim@whitespell.com](mailto:pim@whitespell.com) to request access.

Method | Schema URL | Info
--- | ---- | ------
Post data | [POST](https://docs.google.com/drawings/d/1UIDXzXAISMnD30ZVTRfRWIPrzDZQuWtkyJEMr0BOXF8/edit) | Used to add or update data
Request data | [GET](https://docs.google.com/drawings/d/13vZSrLS6FnD81OHgMIYzTpy-j4cC0fsQbbLdgwEp_Lo/edit) | Used to add or update data


##Headers

Key | Value | Info
--- | ----- | ----
X-Authentication | ```<user_id>,<key>``` | User authentication header
Authorization | ```<api_key>``` | Your developer key

##Variables

You can send data to the API in 3 different ways. Each method has a different meaning. 


Key | Example | Info
--- | ----- | ----
URL Variables | ```GET https://peakapi.whitespell.com/users/<user_id>``` | This is used when the value is guaranteed to be unique and you are directly accessing an object
Query String Variables | ```GET https://peakapi.whitespell.com/users/categories/?categories=1,2,3&limit=10``` | This is mainly used to specify/narrow a result set or search for certain values. 
Request Body (Payload) | ```POST https://peakapi.whitespell.com/categories -> {"category_name" : "new_category"}``` | This is used in the body of the request, also known as the payload. We only accept JSON payloads.

## Errors
```shell
curl "http://peakapi.whitespell.com/users/categories?"
  -H "Authorization: YOUR_API_KEY" 
  -H "X-Authentication: 134,c5m7tb6equb0isdbbv1pla98hu"
```

> Because the 'categories' parameter is missing in the query string, and it is a required parameter, the following JSON error will be thrown

```json
{
    "className" :   "GetUsersByCategory",
    "httpStatusCode"    :   400,
    "errorId"   :   113,
    "errorMessage"  :   "Required key 'categories' was not found in the query string. See the documentation for all the requirements."
}
```

The API has a really good error informative reporting system, making it super simple for developers to use the API and learn from there errors.

Parameter | Meaning
---------- | -------
className | The class the error was thrown in
httpStatusCode | The status code that was returned by the API
errorId | The error ID that was reported. Developers can use this to look up your error.
errorMessage | More information about the error


Error Code | Meaning
---------- | -------
400 | Bad Request -- Your request contains information that is not acceptable, for example your JSON is not actually JSON
401 | Unauthorized -- Your API key is wrong or your X-Authentication is wrong.
403 | Forbidden -- You are not permitted to do this action
404 | Not Found -- The specified kitten could not be found
500 | Internal Server Error -- We had a problem with our server. Try again later.
503 | Service Unavailable -- We're temp. offline for maintanance. Please try again later.


# Users

## Get All Users

```shell
curl "https://peakapi.whitespell.com/users/"
  -H "Authorization: YOUR_API_KEY" 
  -H "X-Authentication: 134,c5m7tb6equb0isdbbv1pla98hu"
```

> The above command returns JSON structured like this:

```json
[
    {
        "user_following": [],
        "category_following": [],
        "category_publishing": [],
        "user_id": 0,
        "username": "example_name",
        "email": "hidden",
        "thumbnail": "https://image.com/photo.jpg"
    },
    {
        "user_following": [],
        "category_following": [],
        "category_publishing": [],
        "user_id": 0,
        "username": "example_name2",
        "email": "hidden",
        "thumbnail": "https://image.com/photo.jpg"
    }
]
```

This endpoint retrieves all users and allows for search queries on users

### HTTP Request

`GET https://peakapi.whitespell.com/users/`

### Query Parameters

Parameter | Default | Description | Status
--------- | ------- | ----------- | ------
limit | 50 | If set, limit the amount of user objects you will get back by this amount. | Not Started
offset | None | If set, start loading from user ids only larger than the offset number (e.g. for infinite scrolling)  | Not Started
username | None | If set, will search for users with a matching or semi-matching username  | Not Started
bio | None | If set, will search for users with a matching or semi-matching bio  | Not Started
publisher | None | If set, will look for accounts only with certain publisher status. | Not Started


## Get a Specific User


```shell
curl "https://peakapi.whitespell.com/users/"
  -H "Authorization: YOUR_API_KEY" 
  -H "X-Authentication: 134,c5m7tb6equb0isdbbv1pla98hu"
```

> The above command returns JSON structured like this:

```json
{
    "user_following": [],
    "category_following": [],
    "category_publishing": [],
    "user_id": 134,
    "username": "pimdewitte",
    "email": "hidden",
    "thumbnail": "https://image.com/photo.jpg"
}
```

This endpoint retrieves all users and allows for search queries on users

### HTTP Request

`GET https://peakapi.whitespell.com/users/`

### Query Parameters

Parameter | Default | Description | Status
--------- | ------- | ----------- | ------
include_following | false | If set, will include a JSON Array of user objects this user is following. | Not Started
include_followers | false | If set, will include a JSON Array of user objects which are following this user.  | Not Started
include_publishing | false | If set, will include a list of categories this user is publishing in  | Not Started



