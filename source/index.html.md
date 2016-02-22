---
title: API Reference

language_tabs:
  - shell
  - ruby

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to the ShipSticks API! You can use our API to access ShipSticks API endpoints, which can get information on users, shipments, etc., in our database.

We have language bindings in Shell and Ruby. You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.


# Authentication

> To authorize, use this code:

<!--```ruby-->
<!--require 'shipsticks'-->

<!--api = ShipSticks::APIClient.authorize!('API-KEY')-->
<!--```-->

```shell
# With shell, you can just pass the correct header with each request
curl "api_endpoint_here"
  -H "Authorization: API-KEY"
```

> Make sure to replace `API-KEY` with your API key.

ShipSticks uses API keys to allow access to the API. You can register a new ShipSticks API key at our [developer portal](http://example.com/developers).

ShipSticks expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: API-KEY`

<aside class="notice">
You must replace <code>API-KEY</code> with your personal API key.
</aside>

# Users

The API allows you to create, retrieve, and update your users. You can retrieve individual users as well as a list of all your users.

## Get All Users

<!--```ruby-->
<!--require 'shipsticks'-->

<!--api = ShipSticks::APIClient.authorize!('API-KEY')-->
<!--api.users.get-->
<!--```-->

```shell
curl "https://shipsticks.com/api/beta/users"
  -H "Authorization: API-KEY"
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": "56c201211200c1a03000000c",
    "first_name": "John",
    "last_name": "Doe",
    "email": "john@shipsticks.com",
    "phone_number": "5613336666"
  },
  {
    "id": "56c201289200c2b03000000f",
    "first_name": "Jane",
    "last_name": "Doe",
    "email": "jane@shipsticks.com",
    "phone_number": "9542227777"
  }
]
```

This endpoint retrieves all users.

### HTTP Request

`GET https://shipsticks.com/api/beta/users`


## Get a Specific User by ID

<!--```ruby-->
<!--require 'shipsticks'-->

<!--api = ShipSticks::APIClient.authorize!('API-KEY')-->
<!--api.users.get("56c201289200c2b03000000f")-->
<!--```-->

```shell
curl "https://shipsticks.com/api/beta/users/56c201289200c2b03000000f"
  -H "Authorization: API-KEY"
```

> The above command returns JSON structured like this:

```json
{
  "id": "56c201289200c2b03000000f",
  "first_name": "Jane",
  "last_name": "Doe",
  "email": "jane@shipsticks.com",
  "phone_number": "9542227777"
}
```

This endpoint retrieves a specific user.

### HTTP Request

`GET https://shipsticks.com/api/beta/users/<ID>`

### URL Parameters

Parameter | Required | Description
--------- | -------- | -----------
`id` | `true` | The `id` of the user to retrieve


## Get a Specific User by Email

<!--```ruby-->
<!--require 'shipsticks'-->

<!--api = ShipSticks::APIClient.authorize!('API-KEY')-->
<!--api.users.search("jane@shipsticks.com")-->
<!--```-->

```shell
curl "https://shipsticks.com/api/beta/search/users/?email=jane@shipsticks.com"
  -H "Authorization: API-KEY"
```

> The above command returns JSON structured like this:

```json
{
  "id": "56c201289200c2b03000000f",
  "first_name": "Jane",
  "last_name": "Doe",
  "email": "jane@shipsticks.com",
  "phone_number": "9542227777"
}
```

This endpoint retrieves a specific user.


### HTTP Request

`GET https://shipsticks.com/api/beta/search/users/?email=<EMAIL>`

### URL Parameters

Parameter | Required | Description
--------- | -------- | -----------
`email` | `true` | The `email` of the user to retrieve


## Create a User

<!--```ruby-->
<!--require 'shipsticks'-->

<!--api = ShipSticks::APIClient.authorize!('API-KEY')-->
<!--api.users.create(-->
  <!--user: {-->
    <!--first_name: "Geoff",-->
    <!--last_name: "Skoch",-->
    <!--email: "geoff@shipsticks.com",-->
    <!--phone_number: "5614440000"-->
  <!--}-->
<!--)-->
<!--```-->

```shell
curl -X POST -H "Authorization: API-KEY"
  -d '{
    "user": {
      "first_name": "Geoff",
      "last_name": "Skoch",
      "email": "geoff@shipsticks.com",
      "phone_number": "5614440000"
    }
  }' "http://shipsticks.com/api/beta/users/"
}'
```

> The above command returns JSON structured like this:

```json
{
  "id": "56c201289200c2b03000000k",
  "first_name": "Geoff",
  "last_name": "Skoch",
  "email": "geoff@shipsticks.com",
  "phone_number": "5614440000"
}
```

This endpoint creates a user.


### HTTP Request

`POST https://shipsticks.com/api/beta/users/`

### URL Parameters

Parameter | Required | Description
--------- | -------- | -----------
`first_name` | `true` | The `first name` of the user
`last_name` | `true` | The `last name` of the user
`email` | `true` | The `email` of the user
`phone_number` | `false` | The `phone number` of the user


## Update a User

<!--```ruby-->
<!--require 'shipsticks'-->

<!--api = ShipSticks::APIClient.authorize!('API-KEY')-->
<!--api.users.update(-->
  <!--{-->
    <!--id: "56c201289200c2b03000000k",-->
    <!--user: {-->
      <!--first_name: "Nick"-->
    <!--}-->
  <!--}-->
<!--)-->
<!--```-->

```shell
curl -X PUT -H "Authorization: API-KEY"
  -d '{
    "user": {
      "first_name": "Nick"
    }
  }' "http://shipsticks.com/api/beta/users/56c201289200c2b03000000k"
}'
```

> The above command returns JSON structured like this:

```json
{
  "id": "56c201289200c2b03000000k",
  "first_name": "Nick",
  "last_name": "Skoch",
  "email": "geoff@shipsticks.com",
  "phone_number": "5614440000"
}
```

This endpoint updates a specific user.


### HTTP Request

`PUT https://shipsticks.com/api/beta/users/<ID>`

### URL Parameters

Parameter | Required | Description
--------- | -------- | -----------
`id` | `true` | The `id` of the user to update
`first_name` | `false` | The `first name` of the user to update
`last_name` | `false` | The `last name` of the user to update
`email` | `false` | The `email` of the user to update
`phone_number` | `false` | The `phone number` of the user to update

# Facilities

The API allows you to create, retrieve, and update your facilities. You can retrieve individual facilities as well as a list of all your facilities.

## Get All Facilities

<!--```ruby-->
<!--require 'shipsticks'-->

<!--api = ShipSticks::APIClient.authorize!('API-KEY')-->
<!--api.facilities.get-->
<!--```-->

```shell
curl "https://shipsticks.com/api/beta/facilities"
  -H "Authorization: API-KEY"
```

> The above command returns JSON structured like this:

```json
[
  {
    "_id": "56aa6daa1200c1d231000001",
    "_type": "Club",
    "club_id": "1026705",
    "name": "Birch Ridge Golf Course, Inc.",
    "ship_to_address": {
      "_id": "56aa6daa1200c1d231000003",
      "address_1": "42223 Sterling Hwy",
      "address_2": "",
      "city": "Soldotna",
      "country": "United States",
      "country_code": "US",
      "lat": null,
      "lng": null,
      "state": "AK",
      "zip": "99669",
      "zip4": null
    },
    "carrier_selection": "UPS",
    "club_close_time": "16:30",
    "allowed_same_day_pickup": true,
    "geo_zip_enabled": true,
    "facility_type": "Club",
    "has_daily_pickup": false,
    "has_fedex_ground_pickup": false,
    "has_fedex_express_pickup": false,
    "allow_in_autocomplete": false,
    "has_carrier_selection": true,
    "closed_monday": false,
    "closed_tuesday": false,
    "closed_wednesday": false,
    "closed_thursday": false,
    "closed_friday": false,
    "saturday_pickup": null,
    "saturday_delivery": null,
    "phone": "(907) 262-5270",
    "formatted_address": "Birch Ridge Golf Course, Inc., AK, United States",
    "icon_url": "//s3.amazonaws.com/shipsticks/cdn/golf-facility-icon.png"
  },
  {
    "_id": "56aa6df71200c161ba00000a",
    "_type": "Club",
    "club_id": "1034485",
    "name": "Poxabogue Golf Center",
    "ship_to_address": {
      "_id": "56aa6df71200c161ba00000c",
      "address_1": "3556 Montauk Highway",
      "address_2": "",
      "city": "Wainscott",
      "country": "United States",
      "country_code": "US",
      "lat": 8.123156999999999,
      "lng": 80.1422381,
      "state": "NY",
      "zip": "11975",
      "zip4": null
    },
    "carrier_selection": "FEDEX",
    "club_close_time": "16:30",
    "allowed_same_day_pickup": true,
    "geo_zip_enabled": false,
    "facility_type": "Club",
    "has_daily_pickup": false,
    "has_fedex_ground_pickup": false,
    "has_fedex_express_pickup": false,
    "allow_in_autocomplete": false,
    "has_carrier_selection": true,
    "closed_monday": true,
    "closed_tuesday": false,
    "closed_wednesday": false,
    "closed_thursday": false,
    "closed_friday": false,
    "saturday_pickup": false,
    "saturday_delivery": false,
    "phone": "(631) 537-0025",
    "formatted_address": "Poxabogue Golf Center, NY, United States",
    "icon_url": "//s3.amazonaws.com/shipsticks/cdn/golf-facility-icon.png"
  }
]
```

This endpoint retrieves all facilities.

### HTTP Request

`GET https://shipsticks.com/api/beta/facilities`


## Get a Specific Facility by ID

<!--```ruby-->
<!--require 'shipsticks'-->

<!--api = ShipSticks::APIClient.authorize!('API-KEY')-->
<!--api.facilities.get("56aa6df71200c161ba00000a")-->
<!--```-->

```shell
curl "https://shipsticks.com/api/beta/facilities/56aa6df71200c161ba00000a"
  -H "Authorization: API-KEY"
```

> The above command returns JSON structured like this:

```json
{
  "_id": "56aa6df71200c161ba00000a",
  "_type": "Club",
  "club_id": "1034485",
  "name": "Poxabogue Golf Center",
  "ship_to_address": {
    "_id": "56aa6df71200c161ba00000c",
    "address_1": "3556 Montauk Highway",
    "address_2": "",
    "city": "Wainscott",
    "country": "United States",
    "country_code": "US",
    "lat": 8.123156999999999,
    "lng": 80.1422381,
    "state": "NY",
    "zip": "11975",
    "zip4": null
  },
  "carrier_selection": "FEDEX",
  "club_close_time": "16:30",
  "allowed_same_day_pickup": true,
  "geo_zip_enabled": false,
  "facility_type": "Club",
  "has_daily_pickup": false,
  "has_fedex_ground_pickup": false,
  "has_fedex_express_pickup": false,
  "allow_in_autocomplete": false,
  "has_carrier_selection": true,
  "closed_monday": true,
  "closed_tuesday": false,
  "closed_wednesday": false,
  "closed_thursday": false,
  "closed_friday": false,
  "saturday_pickup": false,
  "saturday_delivery": false,
  "phone": "(631) 537-0025",
  "formatted_address": "Poxabogue Golf Center, NY, United States",
  "icon_url": "//s3.amazonaws.com/shipsticks/cdn/golf-facility-icon.png"
}
```

This endpoint retrieves a specific facility.

### HTTP Request

`GET https://shipsticks.com/api/beta/facilities/<ID>`

### URL Parameters

Parameter | Required | Description
--------- | -------- | -----------
`id` | `true` | The `id` of the facility to retrieve


## Get Facilities by Name

<!--```ruby-->
<!--require 'shipsticks'-->

<!--api = ShipSticks::APIClient.authorize!('API-KEY')-->
<!--api.facilities.search("Poxabogue Golf Center")-->
<!--```-->

```shell
curl "https://shipsticks.com/api/beta/search/facilities/?name=Poxabogue Golf Center"
  -H "Authorization: API-KEY"
```

> The above command returns JSON structured like this:

```json
[
  {
    "_id": "56aa6df71200c161ba00000a",
    "_type": "Club",
    "club_id": "1034485",
    "name": "Poxabogue Golf Center",
    "ship_to_address": {
      "_id": "56aa6df71200c161ba00000c",
      "address_1": "3556 Montauk Highway",
      "address_2": "",
      "city": "Wainscott",
      "country": "United States",
      "country_code": "US",
      "lat": 8.123156999999999,
      "lng": 80.1422381,
      "state": "NY",
      "zip": "11975",
      "zip4": null
    },
    "carrier_selection": "FEDEX",
    "club_close_time": "16:30",
    "allowed_same_day_pickup": true,
    "geo_zip_enabled": false,
    "facility_type": "Club",
    "has_daily_pickup": false,
    "has_fedex_ground_pickup": false,
    "has_fedex_express_pickup": false,
    "allow_in_autocomplete": false,
    "has_carrier_selection": true,
    "closed_monday": true,
    "closed_tuesday": false,
    "closed_wednesday": false,
    "closed_thursday": false,
    "closed_friday": false,
    "saturday_pickup": false,
    "saturday_delivery": false,
    "phone": "(631) 537-0025",
    "formatted_address": "Poxabogue Golf Center, NY, United States",
    "icon_url": "//s3.amazonaws.com/shipsticks/cdn/golf-facility-icon.png"
  }
]
```

This endpoint retrieves 1 or more facilities.


### HTTP Request

`GET https://shipsticks.com/api/beta/search/facilities/?name=<NAME>`

### URL Parameters

Parameter | Required | Description
--------- | -------- | -----------
`name` | `true` | The `name` of the Facility/ies to retrieve


## Create a Facility

<!--```ruby-->
<!--require 'shipsticks'-->

<!--api = ShipSticks::APIClient.authorize!('API-KEY')-->
<!--api.facilities.create(-->
  <!--facility: {-->
    <!--name: "Poxabogue Golf Center",-->
    <!--type: "Club"-->
    <!--phone: "6315370025",-->
    <!--club_id: "1034485",-->
    <!--carrier_selection: "UPS"-->
  <!--},-->
  <!--ship_to_address: {-->
    <!--destination: {-->
      <!--address_1: "3556 Montauk Highway",-->
      <!--address_2: "Suite #300",-->
      <!--city: "Wainscott",-->
      <!--country: "United States",-->
      <!--country_code: "US",-->
      <!--state: "NY",-->
      <!--zip: 11975,-->
      <!--lat: 8.123156999999999,-->
      <!--lng: 80.1422381,-->
      <!--zip4: "4224"-->
    <!--}-->
  <!--}-->
<!--)-->
<!--```-->

```shell
curl -X POST -H "Authorization: API-KEY"
  -d '{
    "facility": {
      "name": "Poxabogue Golf Center",
      "type": "Club",
      "phone": "6315370025",
      "club_id": "1034485",
      "carrier_selection": "UPS"
    },
    "addresses": {
      "destination": {
        "address_1": "3556 Montauk Highway",
        "address_2": "Suite #300",
        "city": "Wainscott",
        "state": "NY",
        "country": "United States",
        "country_code": "US",
        "zip5": "11975",
        "lat": 8.123156999999999,
        "lng": 80.1422381,
        "zip4": "4224"
      }
    }
  }' "http://shipsticks.com/api/beta/facilities/"
}'
```

> The above command returns JSON structured like this:

```json
{
  "_id": "56aa6df71200c161ba00000a",
  "_type": "Club",
  "club_id": "1034485",
  "name": "Poxabogue Golf Center",
  "ship_to_address": {
    "_id": "56aa6df71200c161ba00000c",
    "address_1": "3556 Montauk Highway",
    "address_2": "",
    "city": "Wainscott",
    "country": "United States",
    "country_code": "US",
    "lat": 8.123156999999999,
    "lng": 80.1422381,
    "state": "NY",
    "zip": "11975",
    "zip4": "4224"
  },
  "carrier_selection": "UPS",
  "club_close_time": "16:30",
  "allowed_same_day_pickup": true,
  "geo_zip_enabled": false,
  "facility_type": "Club",
  "has_daily_pickup": false,
  "has_fedex_ground_pickup": false,
  "has_fedex_express_pickup": false,
  "allow_in_autocomplete": false,
  "has_carrier_selection": true,
  "closed_monday": true,
  "closed_tuesday": false,
  "closed_wednesday": false,
  "closed_thursday": false,
  "closed_friday": false,
  "saturday_pickup": false,
  "saturday_delivery": false,
  "phone": "6315370025",
  "formatted_address": "Poxabogue Golf Center, NY, United States",
  "icon_url": "//s3.amazonaws.com/shipsticks/cdn/golf-facility-icon.png"
}
```

This endpoint creates a facility.

### HTTP Request

`POST https://shipsticks.com/api/beta/facilities/`

### URL Parameters

Parameter | Required | Description
--------- | -------- | -----------
`name` | `true` | The `name` of the facility
`type` | `true` | The `type` of the facility
`ship_to_address` | `true` | The `ship_to_address` of the facitilty
`club_id` | `true` | The friendly identifier of the facility
`phone` | `false` | The phone number of the facility
`carrier_selection` | `false` | The default carrier of the facility
`club_close_time` | `false` | The closing time of the facility
`allowed_same_day_pickup`  | `false` | The `allowed_same_day_pickup` flag for the facility
`geo_zip_enabled` | `false` | The `geo_zip_enabled` flag for the facility
`has_daily_pickup` | `false` | The `has_daily_pickup` flag for the facility
`has_fedex_ground_pickup` | `false` | The `has_fedex_ground_pickup` flag for the facility
`has_fedex_express_pickup` | `false` | The `has_fedex_express_pickup` flag for the facility
`allow_in_autocomplete` | `false` | The `allow_in_autocomplete` flag for the facility
`has_carrier_selection` | `false` | The `has_carrier_selection` flag for the facility
`closed_monday` | `false` | The `closed_monday` flag for the facility
`closed_tuesday` | `false` | The `closed_tuesday` flag for the facility
`closed_wednesday` | `false` | The `closed_wednesday` flag for the facility
`closed_thursday` | `false` | The `closed_thursday` flag for the facility
`closed_friday` | `false` | The `closed_friday` flag for the facility
`saturday_pickup` | `false` | The `saturday_pickup` flag for the facility
`saturday_delivery` | `false` | The `saturday_delivery` flag for the facility

### Child Parameters for `ship_to_address` (addresses object with two keys: `destination` which is required, and `origin` optional)

Parameter | Required | Description
--------- | -------- | -----------
`address_1` | `true` | The street address of the facility
`address_2` | `false` | The secondary street of the facility
`city` | `true` | The `city` of the facitilty
`state` | `true` | The `state` of the facility
`zip` | `true` | The `zip` code of the facility
`zip4` | `false` | The last 4 number zip code of the facility
`country` | `true` | The `country` of the facility
`country_code` | `false` | The `country_code` of the facility
`lat` | `false` | The latitude of the facility
`lng` | `false` | The longitude of the facility


## Update a Facility

<!--```ruby-->
<!--require 'shipsticks'-->

<!--api = ShipSticks::APIClient.authorize!('API-KEY')-->
<!--api.users.update(-->
  <!--{-->
    <!--id: "56c201289200c2b03000000k",-->
    <!--facility: {-->
      <!--name: "Poxabogue Golf Club"-->
    <!--}-->
  <!--}-->
<!--)-->
<!--```-->

```shell
curl -X PUT -H "Authorization: API-KEY"
  -d '{
    "facility": {
      "name": "Poxabogue Golf Club"
    }
  }' "http://shipsticks.com/api/beta/users/56c201289200c2b03000000k"
}'
```

> The above command returns JSON structured like this:

```json
{
  "_id": "56aa6df71200c161ba00000a",
  "_type": "Club",
  "club_id": "1034485",
  "name": "Poxabogue Golf Club",
  "ship_to_address": {
    "_id": "56aa6df71200c161ba00000c",
    "address_1": "3556 Montauk Highway",
    "address_2": "",
    "city": "Wainscott",
    "country": "United States",
    "country_code": "US",
    "lat": 8.123156999999999,
    "lng": 80.1422381,
    "state": "NY",
    "zip": "11975",
    "zip4": "4224"
  },
  "carrier_selection": "UPS",
  "club_close_time": "16:30",
  "allowed_same_day_pickup": true,
  "geo_zip_enabled": false,
  "facility_type": "Club",
  "has_daily_pickup": false,
  "has_fedex_ground_pickup": false,
  "has_fedex_express_pickup": false,
  "allow_in_autocomplete": false,
  "has_carrier_selection": true,
  "closed_monday": true,
  "closed_tuesday": false,
  "closed_wednesday": false,
  "closed_thursday": false,
  "closed_friday": false,
  "saturday_pickup": false,
  "saturday_delivery": false,
  "phone": "6315370025",
  "formatted_address": "Poxabogue Golf Center, NY, United States",
  "icon_url": "//s3.amazonaws.com/shipsticks/cdn/golf-facility-icon.png"
}
```

This endpoint updates a specific facility.


### HTTP Request

`PUT https://shipsticks.com/api/beta/facilities/<ID>`

### URL Parameters

Parameter | Required | Description
--------- | -------- | -----------
`id` | `true` | The `id` of the facility
`name` | `false` | The `name` of the facility
`type` | `false` | The `type` of the facility
`club_id` | `false` | The friendly identifier of the facility
`phone` | `false` | The phone number of the facility
`carrier_selection` | `false` | The default carrier of the facility
`club_close_time` | `false` | The closing time of the facility
`allowed_same_day_pickup`  | `false` | The `allowed_same_day_pickup` flag for the facility
`geo_zip_enabled` | `false` | The `geo_zip_enabled` flag for the facility
`has_daily_pickup` | `false` | The `has_daily_pickup` flag for the facility
`has_fedex_ground_pickup` | `false` | The `has_fedex_ground_pickup` flag for the facility
`has_fedex_express_pickup` | `false` | The `has_fedex_express_pickup` flag for the facility
`allow_in_autocomplete` | `false` | The `allow_in_autocomplete` flag for the facility
`has_carrier_selection` | `false` | The `has_carrier_selection` flag for the facility
`closed_monday` | `false` | The `closed_monday` flag for the facility
`closed_tuesday` | `false` | The `closed_tuesday` flag for the facility
`closed_wednesday` | `false` | The `closed_wednesday` flag for the facility
`closed_thursday` | `false` | The `closed_thursday` flag for the facility
`closed_friday` | `false` | The `closed_friday` flag for the facility
`saturday_pickup` | `false` | The `saturday_pickup` flag for the facility
`saturday_delivery` | `false` | The `saturday_delivery` flag for the facility

