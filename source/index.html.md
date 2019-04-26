---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
  # - ruby
  # - python
  # - javascript

toc_footers:
  - <a href='https://nightwatch.io'>Sign Up for Nightwatch</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to the [Nightwatch](https://nightwatch.io) API docs! Here you can find guides on how to interact with data associated with your Nightwatch account using HTTP requests (REST API).

If you don't have an account yet, [sign up](https://app.nightwatch.io) for a Nightwatch account


# Authentication


Nightwatch API uses `access_token` authentication. You need to provide your `access_token` for all requests you issue against our API.


`https://api.nightwatch.io/some_action?access_token=ACCESS_TOKEN`

<aside class="notice">
You must replace <code>ACCESS_TOKEN</code> with your personal access token.
</aside>

# Access Token

## Obtain an access token for your user

<!-- ```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get
``` -->

```shell
curl 'https://api.nightwatch.io/api/v1/token'
-H 'Content-Type: application/json'
--data-binary '{"email":"YOUR_EMAIL","password":"YOUR_PASSWORD"}
```

> The above command returns JSON structured like this:

```json
  {
    "access_token": "TOKEN"
  }
```

This endpoint gets you the access token that you must include with all your requests.

### HTTP Request

`POST https://api.nightwatch.io/api/v1/token`

### Query Parameters

Parameter | Description
--------- | -----------
email | Your Nightwatch e-mail
password | Your Nightwatch password

<aside class="notice">
  This token is permanent and you only need to get it once. It is only necessary to get it again when you revoke it.
</aside>

## Revoke an access token for your user

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get(2)
```

```shell
curl "http://example.com/api/kittens/2"
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.get(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "name": "Max",
  "breed": "unknown",
  "fluffiness": 5,
  "cuteness": 10
}
```

# Groups

A group is a top-level container for your URLs and global views.

<aside class="notice">Having at least one group is the prerequisite for adding URLs, keywords and other resources.</aside>

## List groups

### HTTP Request

`GET https://api.nightwatch.io/api/v1/url_groups?access_token=ACCESS_TOKEN`

```shell
  curl 'https://api.nightwatch.io/api/v1/url_groups?access_token=6e7157c356ebbf8193512c3496c58304f7179706bfa625e8af0986ed074423c9' -H 'Content-Type: application/json'
```

> The above command returns JSON structured like this:

```json
  [{"id":36242,"name":"Testing","url_count":13,"url_type":null,"group_type":"static","dynamic_view_count":1}, {...}, ...]
```

## Create a group

### HTTP Request

`GET https://api.nightwatch.io/api/v1/url_groups?access_token=ACCESS_TOKEN`

```shell
  curl 'https://api.nightwatch.io/api/v1/url_groups?access_token=6e7157c356ebbf8193512c3496c58304f7179706bfa625e8af0986ed074423c9' -H 'Content-Type: application/json'
```

> The above command returns JSON structured like this:

```json
  [{"id":36242,"name":"Testing","url_count":13,"url_type":null,"group_type":"static","dynamic_view_count":1}, {...}, ...]
```


## Delete a Specific Kitten

```ruby
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.delete(2)
```

```python
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.delete(2)
```

```shell
curl "http://example.com/api/kittens/2"
  -X DELETE
  -H "Authorization: meowmeowmeow"
```

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let max = api.kittens.delete(2);
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "deleted" : ":("
}
```

This endpoint deletes a specific kitten.

### HTTP Request

`DELETE http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to delete

