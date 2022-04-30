---
title: API Reference | SalesBlink

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
  - javascript

toc_footers:
  - <a href='https://run.salesblink.io/auth/signup'>Sign Up for an API Key</a>
  - <a href='https://help.salesblink.io'>SalesBlink Help</a>
  - <a href='https://salesblink.io'>Visit SalesBlink</a>

includes:
  - errors

search: true

code_clipboard: true

meta:
  - name: description
    content: Documentation for the Kittn API
---

# Introduction

Welcome to the SalesBlink API! You can use our API to access SalesBlink API endpoints, which can get information on campaigns, prospects and more.

We have language bindings in Shell, and JavaScript! You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.

# Authentication

> To authorize, use this code:

```shell
# With shell, you can just pass the correct header with each request
curl "api_endpoint_here" \
  -H "Authorization: your_salesblink_key"
```

```javascript
var axios = require('axios');

var config = {
  method: 'get',
  url: 'api_endpoint_here',
  headers: { 
    'Authorization': 'your_salesblink_key'
  }
};

axios(config)
.then(function (response) {
  console.log(JSON.stringify(response.data));
})
.catch(function (error) {
  console.log(error);
});

```

> Make sure to replace `your_salesblink_key` with your API key.

SalesBlink uses API keys to allow access to the API. You can register a new SalesBlink API key from [integrations page](https://run.salesblink.io/integrations).

SalesBlink expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: your_salesblink_key`

<aside class="notice">
You must replace <code>your_salesblink_key</code> with your own API key.
</aside>

# Campaigns

## Search Campaign

```shell
curl --location --request GET 'https://run.salesblink.io/api/campaign?term=campaign_name' \
--header 'Authorization: your_salesblink_key'
```

```javascript
var axios = require('axios');

var config = {
  method: 'get',
  url: 'https://run.salesblink.io/api/campaign?term=campaign_name',
  headers: { 
    'Authorization': 'your_salesblink_key'
  }
};

axios(config)
.then(function (response) {
  console.log(JSON.stringify(response.data));
})
.catch(function (error) {
  console.log(error);
});
```

This endpoint searches for campaigns.

### HTTP Request

`GET https://run.salesblink.io/api/campaign?term=campaign_name`

You will receive the campaignID and other campaign information of each campaign that contains your search term.

### URL Parameters

| Query Parameter | Description                       |
| --------------- | --------------------------------- |
| term            | name or part of the campaign name |

## Get All Campaigns

```shell
curl --location --request GET 'https://run.salesblink.io/api/campaigns' \
--header 'Authorization: your_salesblink_key'
```

```javascript
var axios = require('axios');

var config = {
  method: 'get',
  url: 'https://run.salesblink.io/api/campaigns',
  headers: { 
    'Authorization': 'your_salesblink_key'
  }
};

axios(config)
.then(function (response) {
  console.log(JSON.stringify(response.data));
})
.catch(function (error) {
  console.log(error);
});

```
<!-- 
> The above command returns JSON structured like this:

```json
{
    "success": true,
    "error": false,
    "data": [
      {
        "user_name":"Sushant Shekhar",
        "email":"support@salesblink.io",
        "company_name": "SalesBlink",
        "user_picture":"_base64_image_"
      }
    ]
}
``` -->

This endpoint retrieves all campaigns.

### HTTP Request

`GET https://run.salesblink.io/api/campaigns`

You will receive a campaignID for each of the campaigns you have access to, you can use this to perform different API requests.

## Get a Specific Campaign

```shell
curl --location --request GET 'https://run.salesblink.io/api/campaign/<campaignID>' \
--header 'Authorization: your_salesblink_key'
```

```javascript
var axios = require('axios');

var config = {
  method: 'get',
  url: 'https://run.salesblink.io/api/campaign/<campaignID>',
  headers: { 
    'Authorization': 'your_salesblink_key'
  }
};

axios(config)
.then(function (response) {
  console.log(JSON.stringify(response.data));
})
.catch(function (error) {
  console.log(error);
});

```
<!-- 
> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "name": "Max",
  "breed": "unknown",
  "fluffiness": 5,
  "cuteness": 10
}
``` -->

This endpoint retrieves a specific campaign by its campaignID.
### HTTP Request

`GET https://run.salesblink.io/api/campaign/<campaignID>`

### URL Parameters

| Parameter  | Description                        |
| ---------- | ---------------------------------- |
| campaignID | The ID of the campaign to retrieve |

## Pause a Campaign

```shell
curl --location --request POST 'https://run.salesblink.io/api/campaign-status' \
--header 'Authorization: your_salesblink_key' \
--header 'Content-Type: application/json'
--data-raw '{
    "campaignID": "<campaignID>",
    "pause": true
}'
```

```javascript
var axios = require('axios');
var data = JSON.stringify({
  "campaignID": "<campaignID>",
  "pause": true
});

var config = {
  method: 'post',
  url: 'https://run.salesblink.io/api/campaign-status',
  headers: { 
    'Authorization': 'your_salesblink_key', 
    'Content-Type': 'application/json'
  },
  data : data
};

axios(config)
.then(function (response) {
  console.log(JSON.stringify(response.data));
})
.catch(function (error) {
  console.log(error);
});

```

<!-- > The above command returns JSON structured like this:

```json
{
  "id": 2,
  "deleted" : ":("
}
``` -->

This endpoint pauses a specific campaign.

### HTTP Request

`POST https://run.salesblink.io/api/campaign-status`

### Body Parameters

| Parameter  | Description                     | Type              |
| ---------- | ------------------------------- | ----------------- |
| campaignID | The ID of the campaign to pause | string            |
| pause      | The ID of the campaign to pause | bool (true,false) |

## UnPause a Campaign

```shell
curl --location --request POST 'https://run.salesblink.io/api/campaign-status' \
--header 'Authorization: your_salesblink_key' \
--header 'Content-Type: application/json'
--data-raw '{
    "campaignID": "<campaignID>",
    "pause": false
}'
```

```javascript
var axios = require('axios');
var data = JSON.stringify({
  "campaignID": "<campaignID>",
  "pause": false
});

var config = {
  method: 'post',
  url: 'https://run.salesblink.io/api/campaign-status',
  headers: { 
    'Authorization': 'your_salesblink_key', 
    'Content-Type': 'application/json'
  },
  data : data
};

axios(config)
.then(function (response) {
  console.log(JSON.stringify(response.data));
})
.catch(function (error) {
  console.log(error);
});

```

<!-- > The above command returns JSON structured like this:

```json
{
  "id": 2,
  "deleted" : ":("
}
``` -->

This endpoint pauses a specific campaign.

### HTTP Request

`POST https://run.salesblink.io/api/campaign-status`

### Body Parameters

| Parameter  | Description                     | Type              |
| ---------- | ------------------------------- | ----------------- |
| campaignID | The ID of the campaign to pause | string            |
| pause      | The ID of the campaign to pause | bool (true,false) |

# Prospects

## Search Prospect

```shell
curl --location --request GET 'https://run.salesblink.io/api/prospect?term=email@company.com' \
--header 'Authorization: your_salesblink_key'
```

```javascript
var axios = require('axios');

var config = {
  method: 'get',
  url: 'https://run.salesblink.io/api/prospect?term=email@company.com',
  headers: { 
    'Authorization': 'your_salesblink_key'
  }
};

axios(config)
.then(function (response) {
  console.log(JSON.stringify(response.data));
})
.catch(function (error) {
  console.log(error);
});
```

This endpoint searches for prospect by prospect Email address.

### HTTP Request

`GET https://run.salesblink.io/api/prospect?term=email@company.com`

You will receive the prospect information if your email matches with any prospect email that was previously saved.

### URL Parameters

| Query Parameter | Description                   |
| --------------- | ----------------------------- |
| term            | email address of the prospect |


## List Prospects

```shell
curl --location --request GET 'https://run.salesblink.io/api/prospects/<campaignID>' \
--header 'Authorization: your_salesblink_key'
```

```javascript
var axios = require('axios');

var config = {
  method: 'get',
  url: 'https://run.salesblink.io/api/prospects/<campaignID>',
  headers: { 
    'Authorization': 'your_salesblink_key'
  }
};

axios(config)
.then(function (response) {
  console.log(JSON.stringify(response.data));
})
.catch(function (error) {
  console.log(error);
});
```
<!-- 
> The above command returns JSON structured like this:

```json
{
    "success": true,
    "error": false,
    "data": [
      {
        "user_name":"Sushant Shekhar",
        "email":"support@salesblink.io",
        "company_name": "SalesBlink",
        "user_picture":"_base64_image_"
      }
    ]
}
``` -->

This endpoint retrieves all prospects for a specific campaign.

### HTTP Request

`GET https://run.salesblink.io/api/prospects/<campaignID>`

### URL Parameters

| Parameter  | Description            |
| ---------- | ---------------------- |
| campaignID | The ID of the campaign |

## Get Prospect

```shell
curl --location --request GET 'https://run.salesblink.io/api/prospect/<prospectID>' \
--header 'Authorization: your_salesblink_key'
```

```javascript
var axios = require('axios');

var config = {
  method: 'get',
  url: 'https://run.salesblink.io/api/prospect/<prospectID>',
  headers: { 
    'Authorization': 'your_salesblink_key'
  }
};

axios(config)
.then(function (response) {
  console.log(JSON.stringify(response.data));
})
.catch(function (error) {
  console.log(error);
});
```
<!-- 
> The above command returns JSON structured like this:

```json
{
    "success": true,
    "error": false,
    "data": [
      {
        "user_name":"Sushant Shekhar",
        "email":"support@salesblink.io",
        "company_name": "SalesBlink",
        "user_picture":"_base64_image_"
      }
    ]
}
``` -->

This endpoint retrieves a specific prospects for a specific campaign.

### HTTP Request

`GET https://run.salesblink.io/api/prospect/<prospectID>`

### URL Parameters

| Parameter  | Description                        |
| ---------- | ---------------------------------- |
| prospectID | The ID of the prospect to retrieve |

## Add Prospect

```shell
curl --location --request POST 'https://run.salesblink.io/api/prospect-add' \
--header 'Authorization: your_salesblink_key' \
--header 'Content-Type: application/json' \
--data-raw '{
    "campaignID": "<campaignID>",
    "data": {
        "First Name": "Sushant",
        "Last Name": "Shekhar",
        "Email":"sushant@salesblink.io",
        "Company": "SalesBlink",
        "Example Key": "Any Value",
        "Extra Key":"Any Value"
    }
}'
```

```javascript
var axios = require('axios');
var data = JSON.stringify({
  "campaignID": "<campaignID>",
  "data": {
    "First Name": "Sushant",
    "Last Name": "Shekhar",
    "Email": "sushant@salesblink.io",
    "Company": "SalesBlink",
    "Example Key": "Any Value",
    "Extra Key": "Any Value"
  }
});

var config = {
  method: 'post',
  url: 'https://run.salesblink.io/api/prospect-add',
  headers: { 
    'Authorization': 'your_salesblink_key', 
    'Content-Type': 'application/json'
  },
  data : data
};

axios(config)
.then(function (response) {
  console.log(JSON.stringify(response.data));
})
.catch(function (error) {
  console.log(error);
});

```

<!-- > The above command returns JSON structured like this:

```json
{
  "id": 2,
  "deleted" : ":("
}
``` -->

This endpoint adds a prospect to a campaign

These fields can be used as macros in your email, LinkedIn and phone campaigns.

### HTTP Request

`POST https://run.salesblink.io/api/prospect-add`

### Body Parameters

| Parameter  | Description                                      | Type   |
| ---------- | ------------------------------------------------ | ------ |
| campaignID | The ID of the campaign where prospect is added   | string |
| data       | Object containing custom fields for the prospect | object |

## Update Prospect

```shell
curl --location --request POST 'https://run.salesblink.io/api/prospect' \
--header 'Authorization: your_salesblink_key' \
--header 'Content-Type: application/json' \
--data-raw '{
    "prospectID": "<prospectID>",
    "key":"<key_to_update>",
    "value":"<value_to_update>"
}'
```

```javascript
var axios = require('axios');
var data = JSON.stringify({
  "prospectID": "<prospectID>",
  "key": "<key_to_update>",
  "value": "<value_to_update>"
});

var config = {
  method: 'post',
  url: 'https://run.salesblink.io/api/prospect',
  headers: { 
    'Authorization': 'your_salesblink_key', 
    'Content-Type': 'application/json'
  },
  data : data
};

axios(config)
.then(function (response) {
  console.log(JSON.stringify(response.data));
})
.catch(function (error) {
  console.log(error);
});
```

<!-- > The above command returns JSON structured like this:

```json
{
  "id": 2,
  "deleted" : ":("
}
``` -->

This endpoint updates fields a specific prospect.

These fields can be used as macros in your email, LinkedIn and phone campaigns.

### HTTP Request

`POST https://run.salesblink.io/api/prospect`

### Body Parameters

| Parameter  | Description                                | Type   |
| ---------- | ------------------------------------------ | ------ |
| prospectID | The ID of the prospect to update           | string |
| key        | Key to update. Ex. email                   | string |
| value      | Value to update. Ex. support@salesblink.io | string |


## Unsubscribe Prospect

```shell
curl --location --request POST 'https://run.salesblink.io/api/prospect-unsubscribe' \
--header 'Authorization: your_salesblink_key' \
--header 'Content-Type: application/json' \
--data-raw '{
    "prospectID": "<prospectID>"
}'
```

```javascript
var axios = require('axios');
var data = JSON.stringify({
  "prospectID": "<prospectID>"
});

var config = {
  method: 'post',
  url: 'https://run.salesblink.io/api/prospect-unsubscribe',
  headers: { 
    'Authorization': 'your_salesblink_key', 
    'Content-Type': 'application/json'
  },
  data : data
};

axios(config)
.then(function (response) {
  console.log(JSON.stringify(response.data));
})
.catch(function (error) {
  console.log(error);
});


```

<!-- > The above command returns JSON structured like this:

```json
{
  "id": 2,
  "deleted" : ":("
}
``` -->

This endpoint unsubscribed a specific prospect. 
All their upcoming email, LinkedIn and call tasks are deleted.

### HTTP Request

`POST https://run.salesblink.io/api/prospect-unsubscribe`

### Body Parameters

| Parameter  | Description                           | Type   |
| ---------- | ------------------------------------- | ------ |
| prospectID | The ID of the prospect to unsubscribe | string |

# Team
## List Members

```shell
curl --location --request GET 'https://run.salesblink.io/api/my-team' \
--header 'Authorization: your_salesblink_key'
```

```javascript
var axios = require('axios');

var config = {
  method: 'get',
  url: 'https://run.salesblink.io/api/my-team',
  headers: { 
    'Authorization': 'your_salesblink_key'
  }
};

axios(config)
.then(function (response) {
  console.log(JSON.stringify(response.data));
})
.catch(function (error) {
  console.log(error);
});

```
<!-- 
> The above command returns JSON structured like this:

```json
{
    "success": true,
    "error": false,
    "data": [
      {
        "user_name":"Sushant Shekhar",
        "email":"support@salesblink.io",
        "company_name": "SalesBlink",
        "user_picture":"_base64_image_"
      }
    ]
}
``` -->

This endpoint retrieves members of your current team.

### HTTP Request

`GET https://run.salesblink.io/api/my-team`