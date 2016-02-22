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

## Get User Shipments

```shell
curl "https://shipsticks.com/api/beta/users/569cfdc71200c1e267000001/shipments"
  -H "Authorization: API-KEY"
```

> The above command returns JSON structured like this:

```json
[
  {
    "_id": "569d01831200c1dc69000023",
    "_type": "GolfBag",
    "affiliate_id": null,
    "assigned_employee_id": null,
    "bag_count": 1,
    "carrier": "FEDEX",
    "carrier_code": "FDXG",
    "carrier_tracking_id": "782384621461",
    "carrier_transit_estimate_id": null,
    "cost_cents": 3499,
    "coupled_tracking_id": null,
    "coupon_id": null,
    "created_at": "2016-01-18T15:15:16Z",
    "custom_form_base64": null,
    "custom_form_data": null,
    "delivered_date": null,
    "desired_arrival_date": "2016-02-12",
    "destination_club_id": "",
    "destination_ship_point": {
      "_id": "569d01831200c1dc6900001c",
      "_time_zone": null,
      "address_type": "standard",
      "attention_name": "",
      "city": "Wainscott",
      "company_name": "Poxabogue Golf Center",
      "country_code": "US",
      "delivery_address_line": "3556 Montauk Highway",
      "delivery_address_line_1": null,
      "extension": null,
      "facility_id": null,
      "lat": null,
      "lng": null,
      "phone_number": "(631) 537-0025",
      "service_area_code": null,
      "state": "NY",
      "zip4": null,
      "zip5": "11975"
    },
    "discount_cents": 0,
    "drop_off_at_ups": true,
    "drop_off_ready": 0,
    "enqueued": false,
    "form_id": null,
    "golfer_email": "jose@shipsticks.com",
    "golfer_id": "1453129944767",
    "golfer_name": "jose",
    "golfer_phone": "(561) 222-2222",
    "grouped_pickup_request_id": null,
    "has_dummy_label": false,
    "height_inches": 10,
    "insurance_cents": 100000,
    "international_complete": true,
    "international_complete_date": "2016-02-17",
    "international_shipment": false,
    "landed_cost": null,
    "leg_index": "1",
    "length_inches": 48,
    "license_plate": null,
    "luggage_count": 0,
    "luggage_insurance_cents": 0,
    "mark_for_cancellation": false,
    "micro_site_id": null,
    "misc_info": "",
    "multi_leg": false,
    "new_tracking_id": null,
    "old_grouped_pickup_request_id": null,
    "original_arrival_date": null,
    "original_order_id": "569d01841200c1dc69000024",
    "original_pickup_date": null,
    "origination_club_id": "",
    "origination_ship_point": {
      "_id": "569d01831200c1dc6900001e",
      "_time_zone": null,
      "address_type": "standard",
      "attention_name": "Jose",
      "city": "West Palm Beach",
      "company_name": "Ship Sticks",
      "country_code": "US",
      "delivery_address_line": "221 Clematis St",
      "delivery_address_line_1": "Suite 300",
      "extension": null,
      "facility_id": null,
      "lat": null,
      "lng": null,
      "phone_number": "(561) 222-2222",
      "service_area_code": null,
      "state": "FL",
      "zip4": null,
      "zip5": "33401"
    },
    "paid_insurance_cents": 0,
    "paid_luggage_insurance_cents": 0,
    "payment_mode": null,
    "pickup_close_time": "1800",
    "pickup_date": "2016-02-09",
    "pickup_ready": 0,
    "pickup_ready_time": "0900",
    "pickup_request_id": null,
    "pickup_request_ids": [],
    "potential_issue": "false",
    "previous_tracking_id": null,
    "price_cents": 5499,
    "pro_id": "569cfdc71200c1e267000001",
    "product_id": "56991bbc1200c17403000004",
    "product_line_id": "56991bba1200c17403000001",
    "related_order_id": "569d01841200c1dc69000024",
    "retail_ship_rate": 5499,
    "return_arrival_date": null,
    "return_pickup_date": null,
    "revised_arrival_by_id": null,
    "revised_arrival_date": null,
    "revised_pickup_by_id": null,
    "roundtrip_shipment": null,
    "salesman_id": null,
    "service_type": "FEDEX_GROUND",
    "ship_rate_id": "56991bbf1200c17403000032",
    "shipment_changed": null,
    "size": "SMALL",
    "source": null,
    "state": "accepted",
    "tracking_id": "SS0212OCBH8RJ68",
    "tracking_result": {
      "_id": "56c4ddff1200c18bbf000003",
      "last_tracking_method": "manual",
      "progress": [
        {
          "_id": "56c4ddff1200c18bbf000004",
          "activity": "Request was successfully processed.",
          "activity_code": null,
          "date": "2016-01-16T00:00:00",
          "location": {
            "_id": "56c4ddff1200c18bbf000005",
            "city": null,
            "country": null,
            "state": null,
            "zip": null
          },
          "md5_hash": "ff5137883562247f69c39bc7de2f806c",
          "time": "2016-01-16T00:00:00"
        }
      ],
      "scheduled_deliver_date": "02/12/2016",
      "shipped_on_date": "02/09/2016",
      "signed_for": null,
      "status": "Request was successfully processed.",
      "status_code": null,
      "tracked_date": "2016-02-17T20:54:23Z",
      "tracking_id": "SS0212OCBH8RJ68"
    },
    "updated_at": "2016-02-17T20:55:34Z",
    "user_id": "569cfdc71200c1e267000001",
    "verified_cost_cents": 3187,
    "void_comment": null,
    "void_date": null,
    "void_user": null,
    "weight_oz": 560,
    "width_inches": 14,
    "zero_cents_penalty": 0,
    "zone": 6
  }
]
```

This endpoint retrieves shipments for a specific user.


### HTTP Request

`GET https://shipsticks.com/api/beta/users/<ID>/shipments`

### URL Parameters

Parameter | Required | Description
--------- | -------- | -----------
`id` | `true` | The `id` of the user to update

# Facilities

The API allows you to create, retrieve, and update your facilities. You can retrieve individual facilities as well as a list of all your facilities.

## Get All Facilities

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

# Shipments

The API allows you to retrieve shipments. You can retrieve individual facilities as well as a list of all your facilities.

## Track Shipments

This API allows you to get information on shipments based on their tracking ids and the type of the tracking ids being passed.

There are 3 types of ids:

1. `carrier` - when tracking by a carrier tracking ID (Fedex or UPS tracking ID)
2. `system` - when tracking by a system tracking ID (ShipSticks, Shipskis tracking ID)
3. `shipment` - when tracking by a shipment ID (The resource ID from the database)

```shell
curl -X GET -H "Content-Type: application/json"
  -d '{
    "tracking_ids": ["1Z12345E0291980793"],
    "tracking_id_type": "carrier"
  }' "http://localhost:3000/api/beta/shipments/track/"
```

> The above command returns JSON structured like this:

```json
[
  {
    "56c774e01200c14126000006": {
      "last_tracking_method": "manual",
      "status": "DELIVERED",
      "tracked_date": "2016-01-30T20:02:40Z",
      "tracking_id": "123GEBK7C842",
      "progress": [
        {
          "_id": "56c774e01200c14126000007",
          "activity": "DELIVERED",
          "activity_code": null,
          "date": "20151101",
          "location": {
            "_id": "56c774e01200c14126000008",
            "city": "West Victoria",
            "country": "US",
            "state": "FL",
            "zip": "43171"
          },
          "md5_hash": "00ff052320057f08c1d118e73fcda471",
          "time": "124300"
        },
        {
          "_id": "56c774e01200c14126000009",
          "activity": "OUT FOR DELIVERY",
          "activity_code": null,
          "date": "20151102",
          "location": {
            "_id": "56c774e01200c1412600000a",
            "city": "West Alyssonstad",
            "country": "US",
            "state": "MS",
            "zip": "92938-8987"
          },
          "md5_hash": "00ff052320057f08c1d118e73fcda472",
          "time": "124300"
        },
        {
          "_id": "56c774e01200c1412600000b",
          "activity": "ARRIVAL SCAN",
          "activity_code": null,
          "date": "20151103",
          "location": {
            "_id": "56c774e01200c1412600000c",
            "city": "Pagacborough",
            "country": "US",
            "state": "WI",
            "zip": "36013-8171"
          },
          "md5_hash": "00ff052320057f08c1d118e73fcda473",
          "time": "124300"
        },
        {
          "_id": "56c774e01200c1412600000d",
          "activity": "DEPARTURE SCAN",
          "activity_code": null,
          "date": "20151104",
          "location": {
            "_id": "56c774e01200c1412600000e",
            "city": "Lake Wyman",
            "country": "US",
            "state": "ID",
            "zip": "35153"
          },
          "md5_hash": "00ff052320057f08c1d118e73fcda474",
          "time": "124300"
        },
        {
          "_id": "56c774e01200c1412600000f",
          "activity": "PICKUP SCAN",
          "activity_code": null,
          "date": "20151105",
          "location": {
            "_id": "56c774e01200c14126000010",
            "city": "Port Dorthaville",
            "country": "US",
            "state": "PA",
            "zip": "75207-8534"
          },
          "md5_hash": "00ff052320057f08c1d118e73fcda475",
          "time": "124300"
        },
        {
          "_id": "56c774e01200c14126000011",
          "activity": "BILLING INFORMATION RECEIVED",
          "activity_code": null,
          "date": "20151106",
          "location": {
            "_id": "56c774e01200c14126000012",
            "city": "East Alba",
            "country": "US",
            "state": "OR",
            "zip": "55134"
          },
          "md5_hash": "00ff052320057f08c1d118e73fcda476",
          "time": "124300"
        }
      ]
    }
  }
]
```

This endpoint tracks 1 or more shipments.

### HTTP Request

`GET https://shipsticks.com/api/beta/shipments/track?tracking_id_type=carrier&tracking_ids[]=1Z12345E0291980793`

### URL Parameters

Parameter | Required | Description
--------- | -------- | -----------
`tracking_ids` | `true` | An array of tracking ids of the same type
`tracking_id_type` | `true` | The type of the tracking ids being used

