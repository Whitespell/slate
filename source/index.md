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
X-Authentication | ```<userId>,<key>``` | User authentication header
Authorization | ```<api_key>``` | Your developer key

##Variables

You can send data to the API in 3 different ways. Each method has a different meaning. 

Key | Example | Info
--- | ----- | ----
URL Variables | ```GET https://peakapi.whitespell.com/users/<userId>``` | This is used when the value is guaranteed to be unique and you are directly accessing an object
Query String Variables | ```GET https://peakapi.whitespell.com/users/categories/?categories=1,2,3&limit=10``` | This is mainly used to specify/narrow a result set or search for certain values. 
Request Body (Payload) | ```POST https://peakapi.whitespell.com/categories -> {"categoryName" : "new_category"}``` | This is used in the body of the request, also known as the payload. We only accept JSON payloads.

## Errors
```shell
curl "http://peakapi.whitespell.com/users/categories?" \
  -H "Authorization: YOUR_API_KEY" \
  -H "X-Authentication: YOUR_USER_ID,YOUR_AUTH_KEY"
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


# Endpoints


# Newsfeed


## Get Newsfeed


```shell
    curl "https://peakapi.whitespell.com/newsfeed/USER_ID" \
    -H "Content-Type: application/json" \     
```

> The above command returns JSON structured like this:

```json
{
newsfeed_id: 0,
newsfeed_object: "TEST"
}
```

This endpoint returns the newsfeed for a given userId.

### HTTP Request

`GET https://peakapi.whitespell.com/newsfeed/USER_ID`


## Add Newsfeed


```shell
    curl "https://peakapi.whitespell.com/newsfeed/USER_ID" \
    -H "Content-Type: application/json"
```

> The above command returns JSON structured like this:

```json
{
newsfeed_id: 0,
newsfeed_object: "TEST"
}
```

This endpoint returns the newsfeed for a given userId.

### HTTP Request

`GET https://peakapi.whitespell.com/newsfeed/USER_ID`


# Search


```shell
    curl "https://peakapi.whitespell.com/search?q=SEARCH_STRING" \
        -H "Content-Type: application/json" 
```

> The above command returns JSON structured like this:

```json
{
    "users":[  
        {  
            "userFollowing":[],
            "usersFollowed":[],
            "categoryFollowing":[],
            "categoryPublishing":[],
            "userId":1337,
            "userName":"football",
            "displayName":""
        }
    ],
    "categories":[  
        4
    ],
    "content":[  
        {  
            "contentId":165,
            "contentType":1,
            "contentTitle":"Amir Football Skills",
            "contentUrl":"https://youtu.be/5Z2Fm-2xZgc",
            "contentDescription":"Amir's football skills",
            "likes":100,
            "thumbnail":"http://telecoms.com/wp-content/blogs.dir/1/files/2012/06/euro-football-sport.jpg"
        }
    ]
}
```

This endpoint returns a JSON Object with a profiles array, a categories array (this returns the numbers of the searched categories, e.g. 1=football,2=skydiving,etc) and also a list of content (workouts). 
The categories object contains the categoryIds that match the search query. You can find the available categoryIds using the Request Categories endpoint.

### HTTP Request

`GET https://peakapi.whitespell.com/search/`

### QUERY Parameters

Parameter | Default | Description | Status
--------- | ------- | ----------- | ------
q | None | *REQUIRED* String value of search query (e.g. chri) | Tested
limit | 50 | If set, limit the amount of user objects you will get back by this amount. | Tested
offset | None | If set, start loading from user ids only larger than the offset number (e.g. for infinite scrolling)  | Tested


# Trending


```shell
    curl "https://peakapi.whitespell.com/trending"     
```

> The above command returns JSON structured like this:

```json
{
    "users":[
        {
            "userId":1337,
            "userName":"USER_NAME",
            "displayName":""
        }
    ],
    "categories":[
        4,
        3,
        2,
        1
    ],
    "content":[
        {
            "contentId":4448,
            "contentType":1,
            "contentTitle":"The HARDCORE of SQUATS",
            "contentUrl":"https://youtu.be/X--QIF0mFTg",
            "contentDescription":"Bored of doing the same old squat just Watch the video\nThe HARDCORE of SQUATS.",
            "likes":100,
            "thumbnailUrl":"https://i.ytimg.com/vi/X--QIF0mFTg/hqdefault.jpg"
        }
    ]
}
```

This endpoint returns a JSON Object with a user object array, a categoryId array and also a content array of the trending content. 
Results are truncated here.

### HTTP Request

`GET https://peakapi.whitespell.com/trending/`


# Authentication


## Authentication Request


```shell
curl -d \ '{"userName":"YOUR_USERNAME","password":"YOUR_PASSWORD","device":"DEVICE_INFO", "mac_address":"MAC_ADDRESS","geolocation":"LOCATION_INFO"}' \
-H "Content-Type: application/json" \
-X POST "https://peakapi.whitespell.com/authentication" 
```

> The above command returns JSON structured like this:

```json
[
    {
        "status"    :    "ok",
        "key"    :    "32bitstring",
        "expires"    :   137183918301
    }
]
```

This endpoint allows testing of authentication requests.

### HTTP Request

`POST https://peakapi.whitespell.com/authentication/`

### POST Parameters

Parameter | Required | Description | Status
--------- | ------- | ----------- | ------
userName | Yes | String(30) | Tested
password | Yes | String(inf) | Tested
device | No | String(45) | In Progress
mac_address | No | String(45) | In Progress
geolocation | No | String(Lat, Lon, 45) | In Progress


# Users


## Get All Users

```shell
curl "https://peakapi.whitespell.com/users/" \ 
  -H "Authorization: YOUR_API_KEY" \
  -H "X-Authentication: YOUR_USER_ID,YOUR_AUTH_KEY"
```

> The above command returns JSON structured like this:

```json
[
    {
        "userFollowing": [],
        "categoryFollowing": [],
        "categoryPublishing": [],
        "userId": 0,
        "userName": "example_name",
        "email": "hidden",
        "thumbnail": "https://image.com/photo.jpg"
    },
    {
        "userFollowing": [],
        "categoryFollowing": [],
        "categoryPublishing": [],
        "userId": 0,
        "userName": "example_name2",
        "email": "hidden",
        "thumbnail": "https://image.com/photo.jpg"
    }
]
```

This endpoint retrieves all users and allows for search queries on users.

### HTTP Request

`GET https://peakapi.whitespell.com/users/`

### Query Parameters

Parameter | Default | Description | Status
--------- | ------- | ----------- | ------
limit | 50 | If set, limit the amount of user objects you will get back by this amount. | Tested
offset | None | If set, start loading from user ids only larger than the offset number (e.g. for infinite scrolling)  | Tested
userName | None | If set, will search for users with a matching or semi-matching userName  | Not Started
bio | None | If set, will search for users with a matching or semi-matching bio  | Not Started
publisher | None | If set, will look for accounts only with certain publisher status. | Not Started


## Get a Specific User


```shell
curl "https://peakapi.whitespell.com/users/USER_ID" \
  -H "Authorization: YOUR_API_KEY" \
  -H "X-Authentication: YOUR_USER_ID,YOUR_AUTH_KEY"
```

> The above command returns JSON structured like this:

```json
{
    "userFollowing": [],
    "categoryFollowing": [],
    "categoryPublishing": [],
    "userId": 134,
    "userName": "pimdewitte",
    "email": "hidden",
    "thumbnail": "https://image.com/photo.jpg"
}
```

This endpoint retrieves all users and allows for search queries on users.

### HTTP Request

`GET https://peakapi.whitespell.com/users/USER_ID`

### Query Parameters

Parameter | Default | Description | Status
--------- | ------- | ----------- | ------
includeFollowing | 0 | If value = 1, will include a JSON Array of user objects this user is following. | Tested
includeCategories | 0 | If value = 1, will include a JSON Array of categoryIds this user is following. | Tested
includeFollowers | 0 | If value = 1, will include a JSON Array of user objects which are following this user.  | Not Started
includePublishing | 0 | If value = 1, will include a list of categories this user is publishing in  | Not Started


## Create a New User


```shell
curl -d \ '{"userName":"YOUR_USERNAME","password":"YOUR_PASSWORD","email":"YOUR_EMAIL@EMAIL.COM", "publisher":0}' \
-H "Content-Type: application/json" \
-X POST "https://peakapi.whitespell.com/users" 
```

> The above command returns JSON structured like this:

```json
[
    {
    	"userFollowing": [],
    	"usersFollowed": [],
    	"categoryFollowing": [],
    	"categoryPublishing": [],
    	"userId": 1337,
    	"userName": "YOUR_USERNAME",
    	"displayName": "",
    	"email": "YOUR_EMAIL@EMAIL.COM",
    	"thumbnail": "",
    	"coverPhoto": "",
    	"slogan": ""
    }
]
```

This endpoint allows a new user to create their User Account.

### HTTP Request

`POST https://peakapi.whitespell.com/users/`

### POST Parameters

Parameter | Required | Description | Status
--------- | ------- | ----------- | ------
userName | Yes | String(30) | Tested
password | Yes | String(inf) | Tested
email | Yes | String(45) | Tested
publisher | No | BOOL (1 or 0) | Tested


## Update your User Profile


```shell
curl -d \ '{"userName":"YOUR_NEW_USERNAME","displayName":"DISPLAY_NAME","thumbnail":"https://newThumbUrl.com","cover_photo":"https://coverPhotoUrl.com","slogan":"slogan"}' \
-H "Content-Type: application/json" \
-H "X-Authentication: YOUR_USER_ID,YOUR_AUTH_KEY" \
-X POST "https://peakapi.whitespell.com/users/YOUR_USER_ID"
```

> The above command returns JSON structured like this:
> Only updated fields are returned in the response, others are "" or [].

```json
[
    {
    "userFollowing":[],
    "categoryFollowing":[],
    "categoryPublishing":[],
    "userId":1337,
    "userName":"YOUR_NEW_USERNAME",
    "displayName":"DISPLAY_NAME",
    "email":"",
    "thumbnail":"https://newThumbUrl.com",
    "coverPhoto":"https://coverPhotoUrl.com",
    "slogan":"slogan"
    }
]
```

This endpoint allows a user to update their user profile.

### HTTP Request

`POST https://peakapi.whitespell.com/users/YOUR_USER_ID`

### POST Parameters

Parameter | Required | Description | Status
--------- | ------- | ----------- | ------
userName | No | String(30) | Tested
displayName | No | String(30) | Tested
thumbnail | No | String(255) | Tested
coverPhoto | No | String(255)  | Tested
slogan | No | String(255) | Tested


## Update your User Settings


```shell
curl -d \ '{"password":"CURRENT_PASS","email":"email@email.com","newPassword":"NEW_PASS"}' \
-H "Content-Type: application/json" \
-H "Authorization: YOUR_API_KEY" \
-H "X-Authentication: YOUR_USER_ID,YOUR_AUTH_KEY" \
-X POST "https://peakapi.whitespell.com/users/YOUR_USER_ID/settings"
```

> The above command returns JSON structured like this:
> Only updated fields are returned in the response, others are "".

```json
[
    {
    "key":"NEWLY_CREATED_KEY",
    "userId":1337,
    "expires":-1
    }
]
```

This endpoint allows a user to update their user settings, where they can change their email and/or password.

### HTTP Request

`POST https://peakapi.whitespell.com/users/USER_ID/settings`

### POST Parameters

Parameter | Required | Description | Status
--------- | ------- | ----------- | ------
password | Yes | String(inf) | Tested
email | No | String(45) | Tested
newPassword | No | String(inf) | Tested


## User Follow Action


```shell
curl -d \ '{"followingId":188,"action":"follow"}' \
-H "Content-Type: application/json" \
-H "Authorization: YOUR_API_KEY" \
-H "X-Authentication: YOUR_USER_ID,YOUR_AUTH_KEY" \
-X POST "https://peakapi.whitespell.com/users/YOUR_USER_ID/following"
```

> The above command returns JSON structured like this:
> Only updated fields are returned in the response, others are "".

```json
[
    {
        "action_taken"    :    "followed"
    }
]
```

This endpoint allows a user to follow another user.

### HTTP Request

`POST https://peakapi.whitespell.com/users/USER_ID/following`

### POST Parameters

Parameter | Required | Description | Status
--------- | ------- | ----------- | ------
followingId | Yes | int(11) | Tested
action | Yes | String, either follow/unfollow | Tested


## Request Following Categories


```shell
curl -d \ '{"userId":YOUR_USER_ID}' \
-H "Content-Type: application/json" \
-H "Authorization: YOUR_API_KEY" \
-H "X-Authentication: YOUR_USER_ID,YOUR_AUTH_KEY" \
-X POST "https://peakapi.whitespell.com/users/YOUR_USER_ID/categories"
```

> The above command returns JSON structured like this:

```json
[
    {
        "categoryId" : 1,
        "categoryName" : "fitness"
    },
    {
        "categoryId" : 2,
        "categoryName" : "lacrosse"
    }
]
```

This endpoint returns the list of categories you are following.

### HTTP Request

`POST https://peakapi.whitespell.com/users/YOUR_USER_ID/categories`

### POST Parameters

Parameter | Required | Description | Status
--------- | ------- | ----------- | ------
userId | Yes | int(11) | Not Started


## Follow Category


```shell
curl -d \ '{"categoryId":CATEGORY_ID,"action":"follow"}' \
-H "Content-Type: application/json" \
-H "Authorization: YOUR_API_KEY" \
-H "X-Authentication: YOUR_USER_ID,YOUR_AUTH_KEY" \
-X POST "https://peakapi.whitespell.com/users/YOUR_USER_ID/categories"
```

> The above command returns JSON structured like this:

```json
[
    {
        "action_taken"    :    "category_followed"
    }
]
```

This endpoint returns the list of categories you are following.

### HTTP Request

`POST https://peakapi.whitespell.com/users/YOUR_USER_ID/categories`

### POST Parameters

Parameter | Required | Description | Status
--------- | ------- | ----------- | ------
categoryId | Yes | int(11) | Tested
action | Yes | String (either follow/unfollow) | Tested


## Get Users by Category


```shell
curl "https://peakapi.whitespell.com/users/categories?categories=1" 
```

> The above command returns JSON structured like this:

```json
[
    {  
        "userId":134,
        "username":"pimdewitte",
        "thumbnail":"https://lh3.googleusercontent.com/-Sa9kdnhuE5E/AAAAAAAAAAI/AAAAAAAAABs/H8dhweNPuFI/photo.jpg",
        "categoryId":1
    },
    {  
        "userId":129,
        "username":"cyberstrike1",
        "thumbnail":"https://lh3.googleusercontent.com/-Sa9kdnhuE5E/AAAAAAAAAAI/AAAAAAAAABs/H8dhweNPuFI/photo.jpg",
        "categoryId":1
    }
]
```

This endpoint returns a list of users sorted by the categories you specify.

### HTTP Request

`GET https://peakapi.whitespell.com/users/categories`

### QUERY Parameters

Parameter | Default | Description | Status
--------- | ------- | ----------- | ------
categories | None | *REQUIRED* integer array of categories  | Tested
limit | 50 | If set, limit the amount of user objects you will get back by this amount. | Tested
offset | None | If set, start loading from user ids only larger than the offset number (e.g. for infinite scrolling)  | Not Completed


# Content


## Request Content


```shell
curl "https://peakapi.whitespell.com/content?userId=11" \
       -H "Authorization: YOUR_API_KEY" \
       -H "X-Authentication: YOUR_USER_ID,YOUR_AUTH_KEY" 
```

> The above command returns JSON structured like this:

```json
[
    {
            "contentId"    :    1313,
            "userId" : 11,
            "contentType"    :    2,
            "contentTitle"    :    "Knee to overhead press",
            "contentDescription"    :    "video descr here",
            "timestamp"    :    1433083968,
            "thumbnailUrl" :  "http://cdn.amazoncontent.com/test.jpg"
        },
        {
            "contentId"    :    1212,
            "userId" : 11,
            "contentType"    :    1,
            "contentTitle"    :    "Knee to overhead press",
            "contentDescription"    :    "see me do it",
            "timestamp"    :    1433083968,
            "thumbnailUrl" :   "http://cdn.amazoncontent.com/test.jpg"
        }
]
```

This endpoint requests the content for the newsfeed, can be user specific (?userId=USER_ID).

### HTTP Request

`GET https://peakapi.whitespell.com/content`

### QUERY Parameters

Parameter | Default | Description | Status
--------- | ------- | ----------- | ------
userId | None | int(11), use this to search for content posted by a specific userId. | Tested
limit | 50 | int(11) of the size of the content you'd like to see. E.g. 25 for 25 videos. | Tested
offset | None | int(11) of the minimum video ID to request (e.g. when you already have content, the last content id you have is the offset) | Tested


## Add Content


```shell
curl -d \ '{"contentTypeId":CONTENT_TYPE,"contentTitle":"CONTENT_TITLE","contentUrl":"CONTENT_URL","contentDescription":"DESCRIPTION","thumbnailUrl":"thumburl.com"}' \
-H "Content-Type: application/json" \
-H "Authorization: YOUR_API_KEY" \
-H "X-Authentication: YOUR_USER_ID,YOUR_AUTH_KEY" \
-X POST "https://peakapi.whitespell.com/content"
```

> The above command returns JSON structured like this:

```json
[
    {
            "content_type_added"    :    true
    }
]
```

This endpoint allows a user to add content to the database.

### HTTP Request

`POST https://peakapi.whitespell.com/users/content`

### POST Parameters

Parameter | Required | Description | Status
--------- | ------- | ----------- | ------
contentTypeId | Yes | int, Numeric value of the content type (find all content types on GET /content/types)  | Tested
contentTitle | Yes | String(45) | Tested
contentUrl | Yes | String(255) | Tested
contentDescription | Yes | String(100) | Tested
thumbnailUrl | Yes | String(255) | Tested


## Request Content Types


```shell
curl "https://peakapi.whitespell.com/content/types" \
       -H "Authorization: YOUR_API_KEY" \
       -H "X-Authentication: YOUR_USER_ID,YOUR_AUTH_KEY"
```

> The above command returns JSON structured like this:

```json
[
     {
        "contentTypeId" : 1,
        "contenTypeName" : "youtube"
     }
]
```

This endpoint requests all the content types.

### HTTP Request

`GET https://peakapi.whitespell.com/content/types`


## Add ContentType


```shell
curl -d \ '{"contentTypeName":"CONTENT_TYPE_NAME"}' \
-H "Content-Type: application/json" \
-H "Authorization: YOUR_API_KEY" \
-H "X-Authentication: YOUR_USER_ID,YOUR_AUTH_KEY" \
-X POST "https://peakapi.whitespell.com/content/types"
```

> The above command returns JSON structured like this:

```json
[
    {
            "content_type_added"    :    true
    }
]
```

This endpoint adds a content type such as youtubeVideo to the database. Avoid spaces.

### HTTP Request

`POST https://peakapi.whitespell.com/content/types`

### POST Parameters

Parameter | Required | Description | Status
--------- | ------- | ----------- | ------
contentTypeName | Yes | String(45) Name of the added contentType. Avoid spaces. | Tested


# Categories


## Request Categories


```shell
curl "https://peakapi.whitespell.com/content/categories" \
       -H "Authorization: YOUR_API_KEY" \
       -H "X-Authentication: YOUR_USER_ID,YOUR_AUTH_KEY"
```

> The above command returns JSON structured like this:

```json
[
     {
         "categoryId" : 1,
         "categoryName" : "soccer"
     },
     {
         "categoryId" : 2,
         "categoryName" : "basketball"
     }
]
```

This endpoint requests all current categories in the database.

### HTTP Request

`GET https://peakapi.whitespell.com/content/categories`


## Add a Category


```shell
curl -d \ '{"categoryName":"CATEGORY_NAME","categoryThumbnail":"CATEGORY_THUMB_URL"}' \
-H "Content-Type: application/json" \
-H "Authorization: YOUR_API_KEY" \
-H "X-Authentication: YOUR_USER_ID,YOUR_AUTH_KEY" \
-X POST "https://peakapi.whitespell.com/content/categories"
```

> The above command returns JSON structured like this:

```json
[
    {
    "category_added":true
    }
]
```

This endpoint adds a category to the list of categories.

### HTTP Request

`POST https://peakapi.whitespell.com/content/categories`

### POST Parameters

Parameter | Required | Description | Status
--------- | ------- | ----------- | ------
categoryName | Yes | String(25) Maximum 10 categories. | Tested
categoryThumbnail | Yes | String(255) | Tested



