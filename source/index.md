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
    -H "Content-Type: application/json"   
```

> The above command returns JSON structured like this:

```json
[
    {
        "newsfeedId":14020,
        "user":{
            "userId":11835,
            "publisher":1,
            "emailVerified":0,
            "userName":"peakbasketball",
            "displayName":"",
            "email":"basketball@peakapp.me",
            "thumbnail":"http://peakapp.me/img/app_assets/avatar.png",
            "coverPhoto":"http://peakapp.me/img/app_assets/cover.png",
            "slogan":""
        },
        "content":{
            "userId":11835,
            "contentId":14020,
            "contentType":1,
            "categoryId":1,
            "contentTitle":"Kobe Bryant Shooting Drills",
            "contentUrl":"https://www.youtube.com/watch?v\u003dHOf7UsHyFFQ",
            "contentDescription":"Basketball Shooting Drills That Kobe Bryant Uses In His Training",
            "likes":0,
            "thumbnailUrl":"http://i3.ytimg.com/vi/HOf7UsHyFFQ/0.jpg",
            "userLiked":0,
            "contentPrice":0.99,
            "children":[]
        }
    },
    {
        "newsfeedId":14019,
        "user":{
            "userId":11835,
            "publisher":1,
            "emailVerified":0,
            "userName":"peakbasketball",
            "displayName":"",
            "email":"basketball@peakapp.me",
            "thumbnail":"http://peakapp.me/img/app_assets/avatar.png",
            "coverPhoto":"http://peakapp.me/img/app_assets/cover.png",
            "slogan":""
        },
        "content":{
            "userId":11835,
            "contentId":14019,
            "contentType":1,
            "categoryId":1,
            "contentTitle":"Outdoor Basketball Training",
            "contentUrl":"https://www.youtube.com/watch?v\u003dbGy-pCzJG0I",
            "contentDescription":"Check out these outdoor exercises that will build your fitness and mental toughness.",
            "likes":0,
            "thumbnailUrl":"http://i3.ytimg.com/vi/bGy-pCzJG0I/0.jpg",
            "userLiked":0,
            "contentPrice":0.99,
            "children":[]
        }
    },
    {
        "newsfeedId":14017,
        "user":{
            "userId":11835,
            "publisher":1,
            "emailVerified":0,
            "userName":"peakbasketball",
            "displayName":"",
            "email":"basketball@peakapp.me",
            "thumbnail":"http://peakapp.me/img/app_assets/avatar.png",
            "coverPhoto":"http://peakapp.me/img/app_assets/cover.png",
            "slogan":""
        },
        "content":{
            "userId":11835,
            "contentId":14017,
            "contentType":6,
            "categoryId":1,
            "contentTitle":"Basketball Skills Training - Anthony Bathalon",
            "contentUrl":"https://www.youtube.com/watch?v\u003d-it8-e7dOEo",
            "contentDescription":"Anthony Bathalon showing and motivating you to believe in working on your game.",
            "likes":0,
            "thumbnailUrl":"http://i3.ytimg.com/vi/-it8-e7dOEo/0.jpg",
            "userLiked":0,
            "contentPrice":0.99,
            "children":[
                {
                    "userId":11835,
                    "contentId":14016,
                    "contentType":1,
                    "categoryId":1,
                    "contentTitle":"Fun Drills For Youth Players",
                    "contentUrl":"https://www.youtube.com/watch?v\u003dcQkYcgO7pXw",
                    "contentDescription":"Here are some great drills for youth players!",
                    "likes":0,
                    "thumbnailUrl":"http://i3.ytimg.com/vi/cQkYcgO7pXw/0.jpg",
                    "userLiked":0,
                    "contentPrice":0.99,
                    "children":[]
                },
                {
                    "userId":11835,
                    "contentId":14018,
                    "contentType":1,
                    "categoryId":1,
                    "contentTitle":"Full Shooting Workout for Basketball Players\n",
                    "contentUrl":"https://www.youtube.com/watch?v\u003dJ71iEaXSLCs",
                    "contentDescription":"Dennis Stanton shares a full shooting workout for basketball players. ",
                    "likes":0,
                    "thumbnailUrl":"http://i3.ytimg.com/vi/J71iEaXSLCs/0.jpg",
                    "userLiked":0,
                    "contentPrice":0.99,
                    "children":[]
                }
            ]
        }
    }
]
```

This endpoint returns the newsfeed for a given userId.

### HTTP Request

`GET https://peakapi.whitespell.com/newsfeed/USER_ID`

### QUERY Parameters

Parameter | Default | Description | Status
--------- | ------- | ----------- | ------
limit | 50 | int(11) of the size of the newsfeed you'd like to see. E.g. 25 for 25 videos. | Tested


# Search


```shell
    curl "https://peakapi.whitespell.com/search?q=SEARCH_STRING" \
        -H "Content-Type: application/json" 
```

> The above command returns JSON structured like this:

```json
[
    {
        "newsfeedId":14122,
        "user":{
            "userId":11832,
            "publisher":1,
            "emailVerified":0,
            "emailNotifications":0,
            "userName":"PeakFitness",
            "displayName":" peakfitness",
            "email":"info@whitespell.com",
            "thumbnail":"http://peakapp.me/img/app_assets/avatar.png",
            "coverPhoto":"http://peakapp.me/img/app_assets/cover.png",
            "slogan":""
        },
        "content":{
            "userId":11832,
            "contentId":14122,
            "contentType":6,
            "categoryId":2,
            "contentTitle":"Cross-Training Workout",
            "contentUrl":"https://www.youtube.com/watch?v\u003dxUvuywQy8Ik",
            "contentDescription":"Here are two great exercises from my 31 Days Of Fitness Series: Thrusters and Renegade Rows",
            "likes":0,
            "userLiked":0,
            "contentPrice":0.0,
            "hasAccess":1,
            "recommended":0,
            "poster":{
                "userId":11832,
                "publisher":0,
                "emailVerified":0,
                "emailNotifications":0,
                "userName":"PeakFitness",
                "thumbnail":"http://peakapp.me/img/app_assets/avatar.png"
            },
            "children":[]
        }
    },
    {
        "newsfeedId":14121,
        "user":{
            "userId":11832,
            "publisher":1,
            "emailVerified":0,
            "emailNotifications":0,
            "userName":"PeakFitness",
            "displayName":" peakfitness",
            "email":"info@whitespell.com",
            "thumbnail":"http://peakapp.me/img/app_assets/avatar.png",
            "coverPhoto":"http://peakapp.me/img/app_assets/cover.png",
            "slogan":""
        },
        "content":{
            "userId":11832,
            "contentId":14121,
            "contentType":6,
            "categoryId":2,
            "contentTitle":"Cross-Training Workout",
            "contentDescription":"Here are two great exercises from my 31 Days Of Fitness Series: Thrusters and Renegade Rows",
            "likes":0,
            "userLiked":0,
            "contentPrice":0.0,
            "hasAccess":0,
            "recommended":0,
            "poster":{
                "userId":11832,
                "publisher":0,
                "emailVerified":0,
                "emailNotifications":0,
                "userName":"PeakFitness",
                "thumbnail":"http://peakapp.me/img/app_assets/avatar.png"
            },
            "children":[]
        }
    }
]
```

This endpoint returns a JSON Object with a profiles array, a categories array (this returns the numbers of the searched categories, e.g. 1=football,2=skydiving,etc) and also a list of content. 
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
            "userId":1,
            "contentId":4448,
            "contentType":1,
            "contentTitle":"The HARDCORE of SQUATS",
            "contentUrl":"https://youtu.be/X--QIF0mFTg",
            "contentDescription":"Bored of doing the same old squat just Watch the video\nThe HARDCORE of SQUATS.",
            "likes":100,
            "contentPrice":0.99,
            "thumbnailUrl":"https://i.ytimg.com/vi/X--QIF0mFTg/hqdefault.jpg"
        }
    ]
}
```

This endpoint returns a JSON Object with a user object array, a categoryId array and also a content array of the trending content. 
Now trending users are sorted by amount of published content. 

### HTTP Request

`GET https://peakapi.whitespell.com/trending/`

### Query Parameters

Parameter | Default | Description | Status
--------- | ------- | ----------- | ------
limit | 50 | If set, limit or increase the amount of each object type (user, category, content) you will get back. | Tested


# Authentication


## Authentication Request


```shell
curl -d \ '{"userName":"YOUR_USERNAME","password":"YOUR_PASSWORD","deviceName":"DEVICE_NAME","deviceType":1,"deviceUUID":"DEVICE_TOKEN","mac_address":"MAC_ADDRESS","geolocation":"LOCATION_INFO"}' \
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

This endpoint allows testing of authentication requests. If on a mobile client please include deviceName, deviceType and deviceUUID. 

### HTTP Request

`POST https://peakapi.whitespell.com/authentication/`

### POST Parameters

Parameter | Required | Description | Status
--------- | ------- | ----------- | ------
userName | Yes | String(30) | Tested
password | Yes | String(inf) | Tested
deviceName | No | String(255), Name of device in settings, e.g. "Users Phone" | Tested
deviceType | No | BOOL, 0 or 1, 0 for iOS devices, 1 for Android | Tested
deviceUUID | No | String(255), the identifying device token for the device | Tested
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
        "publisher" : 1,
        "userName": "example_name",
        "email": "hidden",
        "thumbnail": "https://image.com/photo.jpg",
        "slogan":"slogan"
    },
    {
        "userFollowing": [],
        "categoryFollowing": [],
        "categoryPublishing": [],
        "userId": 0,
        "publisher" : 1,
        "userName": "example_name2",
        "email": "hidden",
        "thumbnail": "https://image.com/photo.jpg",
        "slogan":"slogan"
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
userName | None | If set, will for users with a matching or semi-matching userName  | Not Started
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
    "userFollowers": [],
    "userFollowing": [],
    "categoryFollowing": [],
    "categoryPublishing": [],
    "userId": 134,
    "publisher": 1,
    "userName": "pimdewitte",
    "email": "hidden",
    "thumbnail": "https://image.com/photo.jpg",
    "slogan":"slogan",
    "emailNotification":0
}
```

This endpoint retrieves information related to a unique user and allows for search queries on a unique user.

### HTTP Request

`GET https://peakapi.whitespell.com/users/USER_ID`

### Query Parameters

Parameter | Default | Description | Status
--------- | ------- | ----------- | ------
includeFollowers | 0 | If value = 1, will include a JSON Array of userIds who are followers of this user.  | Tested
includeFollowing | 0 | If value = 1, will include a JSON Array of userIds this user is following. | Tested
includeCategories | 0 | If value = 1, will include a JSON Array of categoryIds this user is following. | Tested
includePublishing | 0 | If value = 1, will include a list of categoryIds this user is publishing in  | Tested


## Create a New User


```shell
curl -d \ '{"userName":"YOUR_USERNAME","password":"YOUR_PASSWORD","email":"YOUR_EMAIL@EMAIL.COM", "publisher":1}' \
-H "Content-Type: application/json" \
-X POST "https://peakapi.whitespell.com/users" 
```

> The above command returns JSON structured like this:

```json
{
    "userId":11741,
    "publisher":1,
    "userName":"newPubUser2",
    "displayName":"",
    "email":"q2q@qq.com",
    "thumbnail":"",
    "coverPhoto":"",
    "slogan":""
}
```

This endpoint allows a new user to create their User Account, with or without publisher status.

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
curl -d \ '{"password":"CURRENT_PASS","email":"email@email.com","newPassword":"NEW_PASS","publisher":PUBLISHER_NEW_VALUE}' \
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
    "userId": 1,
    "publisher": 0,
    "email": "updated@email.com"
    }
]
```

This endpoint allows a user to update their user settings, where they can change their email, password and/or publisher status.

### HTTP Request

`POST https://peakapi.whitespell.com/users/USER_ID/settings`

### POST Parameters

Parameter | Required | Description | Status
--------- | ------- | ----------- | ------
password | Yes | String(inf) | Tested
email | No | String(45) | Tested
newPassword | No | String(inf) | Tested
publisher | No | BOOL (1 or 0) | Tested


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
userId | Yes | int(11) | Tested


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
categories | None | Integer array of categories | Tested
limit | 50 | If set, limit the amount of user objects you will get back by this amount. | Tested
offset | None | If set, start loading from user ids only larger than the offset number (e.g. for infinite scrolling)  | Not Completed


## Add to Saved Content


```shell
curl -d \ '{"contentId":CONTENT_ID}' \
-H "Content-Type: application/json" \
-H "Authorization: YOUR_API_KEY" \
-H "X-Authentication: YOUR_USER_ID,YOUR_AUTH_KEY" \
-X POST "https://peakapi.whitespell.com/users/YOUR_USER_ID/saved"
```

> The above command returns JSON structured like this:

```json
[
    {
      "addedContentId" : 0 
    }
]
```

*Requires authentication as the user.* This endpoint adds the content with the given contentId to the user's SavedContent.

### HTTP Request

`POST https://peakapi.whitespell.com/users/YOUR_USER_ID/saved`

### POST Parameters

Parameter | Required | Description | Status
--------- | ------- | ----------- | ------
contentId | Yes | int(11) | Tested


## Get User Saved Content


```shell
curl "https://peakapi.whitespell.com/users/USER_ID/saved" \
-H "Content-Type: application/json" \
-H "Authorization: YOUR_API_KEY" \
-H "X-Authentication: YOUR_USER_ID,YOUR_AUTH_KEY" 
```

> The above command returns JSON structured like this:

```json
{
    "savedContent":[
        {
            "userId":11832,
            "contentId":14122,
            "contentType":6,
            "categoryId":2,
            "contentTitle":"Cross-Training Workout",
            "contentUrl":"https://www.youtube.com/watch?v\u003dxUvuywQy8Ik",
            "contentDescription":"Here are two great exercises from my 31 Days Of Fitness Series: Thrusters and Renegade Rows",
            "likes":0,
            "userLiked":0,
            "contentPrice":0.0,
            "hasAccess":1,
            "recommended":0,
            "poster":{
                "userId":11832,
                "publisher":0,
                "emailVerified":0,
                "emailNotifications":0,
                "userName":"PeakFitness",
                "thumbnail":"http://peakapp.me/img/app_assets/avatar.png"
            },
            "children":[]
        }
    ]
}
```

*Requires authentication as the user.* This endpoint returns the savedContent list for the given userId. 

### HTTP Request

`GET https://peakapi.whitespell.com/users/USER_ID/saved`


## Update Email Verification Status


```shell
curl -d \ '{"userName":"username","emailToken":"EMAIL_TOKEN"}' \
-H "Content-Type: application/json" \
-X POST "https://peakapi.whitespell.com/users/email"
```

> The above command returns JSON structured like this:

```json
{
    "userId":-1,
    "publisher":0,
    "emailVerified":1,
    "userName":"USERNAME",
    "displayName":"",
    "email":"EMAIL",
    "thumbnail":"",
    "coverPhoto":"",
    "slogan":""
}
```

This endpoint is used to validate a user account with a valid email token on the web frontend.

### HTTP Request

`POST https://peakapi.whitespell.com/users/email`

### POST Parameters

Parameter | Required | Description | Status
--------- | ------- | ----------- | ------
userName | Yes | String(45) | Tested
emailToken | Yes | String(32) | Tested


## Resend Welcome Email (Email Verification)


```shell
curl -d \ {"email":"USER_EMAIL"}' \
-H "Content-Type: application/json" \
-X POST "https://peakapi.whitespell.com/users/resendemail"
```

> The above command returns JSON structured like this:

```json
{
    "success":true,
    "email":"USER_EMAIL"
}
```

This endpoint is used to resend a user's welcome email. It resets their email verification status until they verify it
through the web link provided in their email.

### HTTP Request

`POST https://peakapi.whitespell.com/users/resendemail`

### POST Parameters

Parameter | Required | Description | Status
--------- | ------- | ----------- | ------
email | Yes | String(255) | Tested


## Get Email Verification Status


```shell
curl "https://peakapi.whitespell.com/users/USER_ID/email" \
-H "Content-Type: application/json" 
```

> The above command returns JSON structured like this:

```json
{
    "userId":11751,
    "emailVerified":0,
    "emailExpiration":"EXPIRATION_DATE"
}
```

This endpoint returns a user's email verification status. 

### HTTP Request

`GET https://peakapi.whitespell.com/users/USER_ID/email`


## Reset User Password


```shell
curl -d \ '{"userName":"username","newPassword":"newPass","resetToken":"EMAIL_TOKEN"}' \
-H "Content-Type: application/json" \
-X POST "https://peakapi.whitespell.com/users/reset"
```

> The above command returns JSON structured like this:

```json
{
    "success": true,
    "email":"USER_EMAIL"
}
```

This endpoint is used to reset a user's password with a valid reset token on the web frontend.

### HTTP Request

`POST https://peakapi.whitespell.com/users/reset`

### POST Parameters

Parameter | Required | Description | Status
--------- | ------- | ----------- | ------
userName | Yes | String(45) | Tested
newPassword | Yes | String(inf) | Tested
resetToken | Yes | String(32) | Tested


## Send Forgot Password Email


```shell
curl -d \ '{"userName":"username"}' \
-H "Content-Type: application/json" \
-X POST "https://peakapi.whitespell.com/users/forgot"
```

> The above command returns JSON structured like this:

```json
{
    "success": true,
    "email":"USER_EMAIL"
}
```

This endpoint sends a Forgot Password? email to the user's email. 

### HTTP Request

`POST https://peakapi.whitespell.com/users/forgot`

### POST Parameters

Parameter | Required | Description | Status
--------- | ------- | ----------- | ------
userName | Yes | String(45) | Tested


## Check if Peak Password Required for Facebook Login


```shell
curl -d \ '{"accessToken":"FB_ACCESS_TOKEN"}' \
-H "Content-Type: application/json" \
-X POST "https://peakapi.whitespell.com/users/checkfacebook"
```

> The above command returns JSON structured like this:

```json
[
    {
      "requiredPassword" : true
    }
]
```

This endpoint is used to check whether the users/facebook endpoint will require the user's Peak password.

### HTTP Request

`POST https://peakapi.whitespell.com/users/checkfacebook`

### POST Parameters

Parameter | Required | Description | Status
--------- | ------- | ----------- | ------
accessToken | Yes | String(varchar), retrieved from client side facebook login | Tested


## Facebook User Creation and Authentication  


```shell
curl -d \ '{"accessToken":"FB_ACCESS_TOKEN","password":"PEAK_PASSWORD","deviceName":"DEVICE_NAME","deviceType":1,"deviceUUID":"DEVICE_TOKEN"}' \
-H "Content-Type: application/json" \
-X POST "https://peakapi.whitespell.com/users/facebook"
```

> The above command returns JSON structured like this:

```json
[
    {
        "key":"AUTH_KEY",
        "userId":117,
        "expires":-1
    }
]
```

Always use the users/checkfacebook endpoint first to determine if the user's Peak password is required to log in.

This endpoint is used to create a new user or authenticate a current one with the Facebook login accessToken. 
Intended for use on client side after retrieving the Facebook access token from Facebook login in the client. 
If on a mobile client please include deviceName, deviceType and deviceUUID.

### HTTP Request

`POST https://peakapi.whitespell.com/users/facebook`

### POST Parameters

Parameter | Required | Description | Status
--------- | ------- | ----------- | ------
accessToken | Yes | String(varchar), retrieved from client side facebook login | Tested
password | No | String(inf), the user's peak password | Tested
deviceName | No | String(255), Name of device in settings, e.g. "Users Phone" | Tested
deviceType | No | BOOL, 0 or 1, 0 for iOS devices, 1 for Android | Tested
deviceUUID | No | String(255), the identifying device token for the device | Tested


## Add User Feedback for Peak


```shell
curl -d \ '{"email":"USER_EMAIL","message":"FEEDBACK_MESSAGE"}' \
-H "Content-Type: application/json" \
-H "Authorization: YOUR_API_KEY" \
-H "X-Authentication: YOUR_USER_ID,YOUR_AUTH_KEY" \
-X POST "https://peakapi.whitespell.com/users/USER_ID/feedback"
```

> The above command returns JSON structured like this:

```json
[
    {
        "success":true
    }
]
```

*Authentication as the User is Required* 

This endpoint is used to allow a user to add feedback for the app. 

### HTTP Request

`POST https://peakapi.whitespell.com/users/USER_ID/feedback`

### POST Parameters

Parameter | Required | Description | Status
--------- | ------- | ----------- | ------
email | Yes | String(255), the user's email | Tested
message | Yes | String(255), the user's feedback message | Tested


## Add Reporting Type


```shell
curl -d \ '{"reportingTypeName":"REPORTING_TYPE_NAME"}' \
-H "Content-Type: application/json" \
-H "Authorization: YOUR_API_KEY" \
-H "X-Authentication: YOUR_USER_ID,YOUR_AUTH_KEY" \
-X POST "https://peakapi.whitespell.com/users/reporting/types"
```

> The above command returns JSON structured like this:

```json
[
    {
        "reportingTypeAdded":true
    }
]
```

*Authentication is Required* 

This endpoint adds a new reporting type (e.g. Vulgar comments or Fake profile picture) to the database.

### HTTP Request

`POST https://peakapi.whitespell.com/users/reporting/types`

### POST Parameters

Parameter | Required | Description | Status
--------- | ------- | ----------- | ------
reportingTypeName | Yes | String(255), short description of why the user is being reported, to be shown in dropdown menu | Tested


## Request Reporting Types


```shell
curl "https://peakapi.whitespell.com/users/reporting/types" \
       -H "Authorization: YOUR_API_KEY" \
       -H "X-Authentication: YOUR_USER_ID,YOUR_AUTH_KEY" 
```

> The above command returns JSON structured like this:

```json
[  
    {  
        "reportingTypeId":4,
        "reportingTypeName":"Fake profile"
    },
    {  
        "reportingTypeId":1,
        "reportingTypeName":"Hate Speech or Attacking An Individual"
    }
]
```

*Authentication is Required* 

This endpoint requests the reporting types that will be available for reporting a user endpoint (users/USER_ID/reporting).

### HTTP Request

`GET https://peakapi.whitespell.com/users/reporting/types`


## Report a User 


```shell
curl -d \ '{"reportedUserId":"REPORTED_USER_ID","typeId":1,"message":"REPORTING_MESSAGE"}' \
-H "Content-Type: application/json" \
-H "Authorization: YOUR_API_KEY" \
-H "X-Authentication: YOUR_USER_ID,YOUR_AUTH_KEY" \
-X POST "https://peakapi.whitespell.com/users/USER_ID/reporting"
```

> The above command returns JSON structured like this:

```json
[
    {
        "success":true
    }
]
```

*Authentication is Required* 

This endpoint adds a new report on a user to the database.

### HTTP Request

`POST https://peakapi.whitespell.com/users/USER_ID/reporting/`

### POST Parameters

Parameter | Required | Description | Status
--------- | ------- | ----------- | ------
reportedUserId | Yes | Int(11), the reported user's userId | Tested
typeId | Yes | Int(11), the id of the reporting type, get all reporting types with GET users/reporting/types | Tested
message | Yes | String(255), user inputted message describing the reason for the report | Tested


## Get User Notifications


```shell
curl "https://peakapi.whitespell.com/users/USER_ID/notifications" \
       -H "Authorization: YOUR_API_KEY" \
       -H "X-Authentication: YOUR_USER_ID,YOUR_AUTH_KEY" 
```

> The above command returns JSON structured like this:

```json
{  
    "userNotifications":[  
        {  
            "userId":11896,
            "notificationText":"cory uploaded a new video!",
            "notificationAction":"open-content:14068",
            "notificationBadge":0,
            "notificationSound":0,
            "notificationStatus":1,
            "notificationImage":"THUMBNAIL_URL"
        },
        {  
            "userId":11896,
            "notificationText":"pim uploaded a new video!",
            "notificationAction":"open-content:14069",
            "notificationBadge":0,
            "notificationSound":0,
            "notificationStatus":1,
            "notificationImage":"THUMBNAIL_URL"
        }
    ]
}
```

*Authentication as the user is Required* 

This endpoint requests all of the notifications that a user should have received. NotificationStatus is 0 when initialized, 1 on successful send, 
and should be set to 2 when read. (update notificationRead endpoint)

### HTTP Request

`GET https://peakapi.whitespell.com/users/USER_ID/notifications`

### QUERY Parameters

Parameter | Default | Description | Status
--------- | ------- | ----------- | ------
limit | 50 | int(11) of the size of the notifications list. | Tested
offset | None | int(11) of the minimum notificationId to request | Tested


## Update User Email Notification Status


```shell
curl -d \ '{"emailNotifications":0}' \
     -H "Content-Type: application/json" \
     -H "Authorization: YOUR_API_KEY" \
     -H "X-Authentication: YOUR_USER_ID,YOUR_AUTH_KEY" \
     -X POST "https://peakapi.whitespell.com/users/USER_ID/notifications"
```

> The above command returns JSON structured like this:
> Only updated fields are returned in the response, others are "" or -1.

```json  
{
    "userId":1337,
    "publisher":-1,
    "emailVerified":-1,
    "emailNotifications":0,
    "userName":"USERNAME"
}   
```

*Authentication as the user is Required* 

This endpoint modifies the user's email notification status. Unchanged values are -1.

### HTTP Request

`POST https://peakapi.whitespell.com/users/USER_ID/notifications`

### QUERY Parameters

Parameter | Default | Description | Status
--------- | ------- | ----------- | ------
emailNotifications | None | BOOL(1 or 0). 0 for no email notifications, 1 to allow them. | Tested


## Update User's Access to Content


```shell
curl -d \ '{"contentId":0}' \
     -H "Content-Type: application/json" \
     -H "Authorization: YOUR_API_KEY" \
     -H "X-Authentication: YOUR_USER_ID,YOUR_AUTH_KEY" \
     -X POST "https://peakapi.whitespell.com/users/USER_ID/access"
```

> The above command returns JSON structured like this:

```json  
{
    "success":true
}   
```

*Authentication as the user is Required* 

This endpoint grants the user access to a content.

### HTTP Request

`POST https://peakapi.whitespell.com/users/USER_ID/access`

### QUERY Parameters

Parameter | Default | Description | Status
--------- | ------- | ----------- | ------
contentId | None | Int(11). contentId the user will gain access to. | Tested


# Content

## Request Individual Content Object


```shell
curl "https://peakapi.whitespell.com/content" \
       -H "Authorization: YOUR_API_KEY" \
       -H "X-Authentication: YOUR_USER_ID,YOUR_AUTH_KEY" 
```

> The above command returns JSON structured like this:

```json
    {
        "userId":11863,
        "contentId":14007,
        "contentType":6,
        "categoryId":3,
        "contentTitle":"Beginners Home Yoga Workout!",
        "contentUrl":"https://www.youtube.com/watch?v\u003dv7AYKMP6rOE",
        "contentDescription":"Yoga for Complete Beginners!",
        "likes":0,
        "userLiked":0,
        "contentPrice":0.0,
        "hasAccess":1,
        "recommended":0,
        "parent":null,
        "processed":1,
        "poster":{
            "userId":11863,
            "publisher":0,
            "emailVerified":0,
            "emailNotifications":0,
            "userName":"peakyoga",
            "thumbnail":"http://peakapp.me/img/app_assets/avatar.png"
        },
        "children":[
            {
                "userId":11863,
                "contentId":14008,
                "contentType":1,
                "categoryId":3,
                "contentTitle":"Day 1 - Ease Into It - 30 Days of Yoga\n",
                "contentUrl":"https://www.youtube.com/watch?v\u003doBu-pQG6sTY",
                "contentDescription":"Join Adriene on Day 1 of The 30 Days of Yoga journey!",
                "likes":0,
                "userLiked":0,
                "contentPrice":0.0,
                "hasAccess":1,
                "parent":14007,
                "processed":1,
                "recommended":0,
                "poster":{
                    "userId":11863,
                    "publisher":0,
                    "emailVerified":0,
                    "emailNotifications":0,
                    "userName":"peakyoga",
                    "thumbnail":"http://peakapp.me/img/app_assets/avatar.png"
                },
                "children":[]
            }
        ]
    }
```

This endpoint returns a specific content object as specified in the URL

### HTTP Request

`GET https://peakapi.whitespell.com/content/CONTENT_ID`


## Request Content


```shell
curl "https://peakapi.whitespell.com/content" \
       -H "Authorization: YOUR_API_KEY" \
       -H "X-Authentication: YOUR_USER_ID,YOUR_AUTH_KEY" 
```

> The above command returns JSON structured like this:

```json
[
    {
        "userId":11863,
        "contentId":14007,
        "contentType":6,
        "categoryId":3,
        "contentTitle":"Beginners Home Yoga Workout!",
        "contentUrl":"https://www.youtube.com/watch?v\u003dv7AYKMP6rOE",
        "contentDescription":"Yoga for Complete Beginners!",
        "likes":0,
        "userLiked":0,
        "contentPrice":0.0,
        "hasAccess":1,
        "recommended":0,
        "parent":null,
        "processed":1,
        "poster":{
            "userId":11863,
            "publisher":0,
            "emailVerified":0,
            "emailNotifications":0,
            "userName":"peakyoga",
            "thumbnail":"http://peakapp.me/img/app_assets/avatar.png"
        },
        "children":[
            {
                "userId":11863,
                "contentId":14008,
                "contentType":1,
                "categoryId":3,
                "contentTitle":"Day 1 - Ease Into It - 30 Days of Yoga\n",
                "contentUrl":"https://www.youtube.com/watch?v\u003doBu-pQG6sTY",
                "contentDescription":"Join Adriene on Day 1 of The 30 Days of Yoga journey!",
                "likes":0,
                "userLiked":0,
                "contentPrice":0.0,
                "hasAccess":1,
                "parent":14007,
                "processed":1,
                "recommended":0,
                "poster":{
                    "userId":11863,
                    "publisher":0,
                    "emailVerified":0,
                    "emailNotifications":0,
                    "userName":"peakyoga",
                    "thumbnail":"http://peakapp.me/img/app_assets/avatar.png"
                },
                "children":[]
            }
        ]
    }
]
```

This endpoint requests the content in the database, can be user specific (?userId=USER_ID), contentId specific (?contentId=CONTENT_ID),
contentType specific (?contentType=CONTENT_TYPE) or category specific (?categoryId=CATEGORY_ID).

userLiked refers to whether the authenticated user liked the given content. (1 authenticated user has liked it, 0 authenticated user has not liked it),
recommended only applies to the newsfeed. hasAccess is 0 when the user needs to purchase to content to view it, 1 when the content is free or purchased.

### HTTP Request

`GET https://peakapi.whitespell.com/content`

### QUERY Parameters

Parameter | Default | Description | Status
--------- | ------- | ----------- | ------
userId | None | int(11), use this to search for content posted by a specific userId. | Tested
contentId | None | int(11), use this to search for content with a specific contentId. | Tested
contentType | None | int(11), use this to search for content of a certain contentType. e.g. contentType=6 for bundles | Tested
categoryId | None | int(2), use this to search for content posted within a certain category. | Tested
parent | None | int(11), finds all content objects which match a parent object id | Not Tested
processed | None | int(1), 0 or 1, find processed or unprocessed videos | Tested
limit | 50 | int(11) of the size of the content you'd like to see. E.g. 25 for 25 videos. | Tested
offset | None | int(11) of the minimum video ID to request (e.g. when you already have content, the last content id you have is the offset). | Tested


## Add Content


```shell
curl -d \ '{"categoryId":1,"contentType":CONTENT_TYPE,"contentTitle":"CONTENT_TITLE","contentUrl":"CONTENT_URL","contentDescription":"DESCRIPTION","thumbnailUrl":"thumburl.com","contentPrice":0.99}' \
-H "Content-Type: application/json" \
-H "Authorization: YOUR_API_KEY" \
-H "X-Authentication: YOUR_USER_ID,YOUR_AUTH_KEY" \
-X POST "https://peakapi.whitespell.com/content"
```

> The above command returns JSON structured like this:

```json
[
    {
    "contentAdded":true,
    "contentId":"CONTENT_ADDED_ID"
    }
]
```

This endpoint allows a user to add content to the database. If a content has not 

### HTTP Request

`POST https://peakapi.whitespell.com/users/USER_ID/content`

### POST Parameters

Parameter | Required | Description | Status
--------- | ------- | ----------- | ------
categoryId | Yes | int, Numeric value of the category (find all categories on GET /categories)  | Tested
contentType | Yes | int, Numeric value of the content type (find all content types on GET /content/types)  | Tested
contentTitle | Yes | String(45) | Tested
contentUrl | Yes | String(255) | Tested
contentDescription | Yes | String(100) | Tested
contentPrice | Yes | Double(10,2) | Tested
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
        "contentTypeName" : "youtube"
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


## Get Comments on Content


```shell
curl "https://peakapi.whitespell.com/content/CONTENT_ID/comments" \
       -H "Authorization: YOUR_API_KEY" \
       -H "X-Authentication: YOUR_USER_ID,YOUR_AUTH_KEY"
```

> The above command returns JSON structured like this:

```json
[
    {
        "contentId":8420,
        "likes":0,
        "comment":"first comment",
        "timestamp":"Aug 6, 2015 5:08:16 PM",
        "poster":{
            "userId":272,
            "publisher":0,
            "emailVerified":0,
            "userName":"1337",
            "thumbnail":"http://wpidiots.com/html/writic/red-writic-template/css/img/demo-images/avatar1.jpg"
        }
    },
    {
        "contentId":8420,
        "likes":0,
        "comment":"second comment",
        "timestamp":"Aug 6, 2015 5:08:23 PM",
        "poster":{
            "userId":272,
            "publisher":0,
            "emailVerified":0,
            "userName":"1337",
            "thumbnail":"http://wpidiots.com/html/writic/red-writic-template/css/img/demo-images/avatar1.jpg"
        }
    },
    {
        "contentId":8420,
        "likes":0,
        "comment":"third comment",
        "timestamp":"Aug 6, 2015 5:08:28 PM",
        "poster":{
            "userId":272,
            "publisher":0,
            "emailVerified":0,
            "userName":"1337",
            "thumbnail":"http://wpidiots.com/html/writic/red-writic-template/css/img/demo-images/avatar1.jpg"
        }
    },
    {
        "contentId":8420,
        "likes":0,
        "comment":"fourth comment",
        "timestamp":"Aug 6, 2015 5:08:33 PM",
        "poster":{
            "userId":272,
            "publisher":0,
            "emailVerified":0,
            "userName":"1337",
            "thumbnail":"http://wpidiots.com/html/writic/red-writic-template/css/img/demo-images/avatar1.jpg"
        }
    },
    {
        "contentId":8420,
        "likes":0,
        "comment":"wow this video is awesome, love it!",
        "timestamp":"Aug 6, 2015 9:54:30 PM",
        "poster":{
            "userId":272,
            "publisher":0,
            "emailVerified":0,
            "userName":"1337",
            "thumbnail":"http://wpidiots.com/html/writic/red-writic-template/css/img/demo-images/avatar1.jpg"
        }
    }
]
```

*Requires authentication as any user.* This endpoint returns all the comments for the given contentId, sorted by date and time.

### HTTP Request

`GET https://peakapi.whitespell.com/content/CONTENT_ID/comments`


## Add Comment to Content


```shell
curl -d \ '{"userId":USER_ID,"comment":"COMMENT_VALUE"}' \
-H "Content-Type: application/json" \
-H "Authorization: YOUR_API_KEY" \
-H "X-Authentication: YOUR_USER_ID,YOUR_AUTH_KEY" \
-X POST "https://peakapi.whitespell.com/content/CONTENT_ID/comments"
```

> The above command returns JSON structured like this:

```json
[
    {
            "commentAdded"    :    true
    }
]
```

*Requires authentication as the user posting the comment.* This endpoint adds a comment to the given contentId as the given userId. 

### HTTP Request

`POST https://peakapi.whitespell.com/content/CONTENT_ID/comments`

### POST Parameters

Parameter | Required | Description | Status
--------- | ------- | ----------- | ------
userId | Yes | int(11) | Tested
comment | Yes | String(255) | Tested


## Content Like Action


```shell
curl -d \ '{"userId":188,"action":"like"}' \
-H "Content-Type: application/json" \
-H "Authorization: YOUR_API_KEY" \
-H "X-Authentication: YOUR_USER_ID,YOUR_AUTH_KEY" \
-X POST "https://peakapi.whitespell.com/content/CONTENT_ID/likes"
```

> The above command returns JSON structured like this:

```json
[
    {
        "action_taken"    :    "like"
    }
]
```

This endpoint allows a user like/unlike content.

### HTTP Request

`POST https://peakapi.whitespell.com/content/CONTENT_ID/likes`

### POST Parameters

Parameter | Required | Description | Status
--------- | ------- | ----------- | ------
userId | Yes | int(11), userId of user that is liking/unliking content | Tested
action | Yes | String, either like/unlike | Tested


## Add Content to A Bundle


```shell
curl -d \ '{"childId":CHILD_ID}' \
-H "Content-Type: application/json" \
-H "Authorization: YOUR_API_KEY" \
-H "X-Authentication: YOUR_USER_ID,YOUR_AUTH_KEY" \
-X POST "https://peakapi.whitespell.com/content/PARENT_CONTENT_ID/add_child"
```

> The above command returns JSON structured like this:

```json
[
    {
        "added_to_bundle":true
    }
]
```

This endpoint adds a child to a parent (bundle) 

### HTTP Request

`POST https://peakapi.whitespell.com/content/PARENT_CONTENT_ID/add_child`

### POST Parameters

Parameter | Required | Description | Status
--------- | ------- | ----------- | ------
childId | Yes | int(11), contentId of the parent content (bundle) | Tested


## Update Content


```shell
curl -d \ '{"userId":"UPLOADER_USER_ID","contentTitle":"CONTENT_TITLE","contentDescription":"CONTENT_DESCRIPTION","contentPrice":CONTENT_PRICE}' \
-H "Content-Type: application/json" \
-H "X-Authentication: YOUR_USER_ID,YOUR_AUTH_KEY" \
-X POST "https://peakapi.whitespell.com/content/CONTENT_ID"
```

> The above command returns JSON structured like this:
> Only updated fields are returned in the response, others are "", 0 or [].

```json
{
    "updateStatus" : "success"
}
```

*Requires authentication as the uploader*
 
This endpoint allows a user to update their content.

### HTTP Request

`POST https://peakapi.whitespell.com/content/CONTENT_ID`

### POST Parameters

Parameter | Required | Description | Status
--------- | ------- | ----------- | ------
userId | Yes | int(11) | Tested
contentTitle | No | String(45) | Tested
contentDescription | No | String(100) | Tested
contentPrice | No | Double(10,2)  | Tested
categoryId | No | int(1) | Tested
contentUrl | No | String(255)  | Tested
content1080p | No | String(255)  | Tested
content720p | No | String(255)  | Tested
content480p | No | String(255)  | Tested
contentPreview720p | No | String(255)  | Tested
processed | No | int(1) | Tested

# Categories


## Request Categories


```shell
curl "https://peakapi.whitespell.com/categories"
```

> The above command returns JSON structured like this:

```json
[
    {
        "categoryId":1,
        "categoryName":"basketball",
        "categoryThumbnail":"http://www.dhresource.com/albu_355597555_00/1.0x0.jpg",
        "categoryFollowers":12,
        "categoryPublishers":3
    },
    {
        "categoryId":2,
        "categoryName":"fitness",
        "categoryThumbnail":"https://encrypted-tbn2.gstatic.com/images?q\u003dtbn:ANd9GcSARlNn_7bqIDtOekrGQyloJOLaoHaBNvOOUMdeXoSTFXviLXHT",
        "categoryFollowers":61,
        "categoryPublishers":0
    }
]
```

This endpoint requests all current categories in the database.

### HTTP Request

`GET https://peakapi.whitespell.com/categories`


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

`POST https://peakapi.whitespell.com/categories`

### POST Parameters

Parameter | Required | Description | Status
--------- | ------- | ----------- | ------
categoryName | Yes | String(25) Maximum 10 categories. | Tested
categoryThumbnail | Yes | String(255) | Tested



