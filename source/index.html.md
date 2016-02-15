---
title: API Reference

language_tabs:
  - shell
  - ruby
  - python

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to the ShipSticks API! You can use our API to access ShipSticks API endpoints, which can get information on users, shipments, etc., in our database.

We have language bindings in Shell, Ruby and Python . You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.


# Authentication

> To authorize, use this code:

```ruby
require 'shipsticks'

api = ShipSticks::APIClient.authorize!('API-KEY')
```

```python
import shipsticks

api = shipsticks.authorize('shipsticks')
```

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

```ruby
require 'shipsticks'

api = ShipSticks::APIClient.authorize!('API-KEY')
api.users.get
```

```python
import shipsticks

api = shipsticks.authorize('API-KEY')
api.users.get()
```

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

```ruby
require 'shipsticks'

api = ShipSticks::APIClient.authorize!('API-KEY')
api.users.get("56c201289200c2b03000000f")
```

```python
import shipsticks

api = shipsticks.authorize('API-KEY')
api.users.get("56c201289200c2b03000000f")
```

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

```ruby
require 'shipsticks'

api = ShipSticks::APIClient.authorize!('API-KEY')
api.users.search("jane@shipsticks.com")
```

```python
import shipsticks

api = shipsticks.authorize('API-KEY')
api.users.search("jane@shipsticks.com")
```

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

```ruby
require 'shipsticks'

api = ShipSticks::APIClient.authorize!('API-KEY')
api.users.create(
  user: {
    first_name: "Geoff",
    last_name: "Skoch",
    email: "geoff@shipsticks.com",
    phone_number: "5614440000"
  }
)
```

```python
import shipsticks

api = shipsticks.authorize('API-KEY')
api.users.create()
```

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

This endpoint retrieves a specific user.


### HTTP Request

`POST https://shipsticks.com/api/beta/search/users/`

### URL Parameters

Parameter | Required | Description
--------- | -------- | -----------
`first_name` | `true` | The `first name` of the user to retrieve
`last_name` | `true` | The `last name` of the user to retrieve
`email` | `true` | The `email` of the user to retrieve
`phone_number` | `false` | The `phone number` of the user to retrieve


## Update a User

```ruby
require 'shipsticks'

api = ShipSticks::APIClient.authorize!('API-KEY')
api.users.update(
  {
    id: "56c201289200c2b03000000k",
    user: {
      first_name: "Nick"
    }
  }
)
```

```python
import shipsticks

api = shipsticks.authorize('API-KEY')
api.users.update()
```

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

This endpoint retrieves a specific user.


### HTTP Request

`PUT https://shipsticks.com/api/beta/search/users/<ID>`

### URL Parameters

Parameter | Required | Description
--------- | -------- | -----------
`id` | `true` | The `id` of the user to retrieve
`first_name` | `false` | The `first name` of the user to retrieve
`last_name` | `false` | The `last name` of the user to retrieve
`email` | `false` | The `email` of the user to retrieve
`phone_number` | `false` | The `phone number` of the user to retrieve

