# SEPULSA API CALLBACK

API callback for update transaction.

## base url:
  - Development `https://api-dev.julofinance.com`
  - Staging `https://api-staging.julofinance.com`
  - Production `https://api.julofinance.com`

## list api:

| METHOD | URL | DESCRIPTION |
| ------ | ------ | ------ |
| POST | `base_url`/api/partner/v1/auth/login | get Token for Authentication |
| POST | `base_url`/api/partner/v1/sepulsa/transaction | update transaction |

---

# Get Token

authentication API JULO need token, get token with username and password.

## Requirments:

| Field | Type | Validate |
| ------ | ------ | ------ |
| username | String | Mandatory  |
| password | String | Mandatory  |

## data:

```javascript
{
  'username' : {{username}},
  'password' : {{password}}
}
```

## response success:
```javascript
//STATUS CODE 200
{
  'token' : token, 
}
```

## response validate failed (example)
```javascript
//STATUS CODE 400
{
  'password' : [
        'This field is required.'
    ]
}
```

---

# Update Transaction
API for update transaction success or failed.

## Requirments:

| Field | Type | Validate |
| ------ | ------ | ------ |
| token | String | Mandatory  |
| transaction_id | String | Mandatory  |
| order_id | Integer | Mandatory  |
| customer_number | String | Mandatory  |
| product_id | String | Mandatory  |
| type | String | Mandatory  |
| response_code | String | Mandatory , ['00','10','20','21','22','23','24','25','50','98','99'] |
| status | String | Mandatory  |
| serial_number | String | Mandatory  |

## Headers:

```javascript
{
  'Authorization' : Token {{token}},
  'Content-Type' : application/json
}
```

## data:

```javascript
{
  'transaction_id' : {{transaction_id}},
  'order_id' : {{order_id}},
  'customer_number' : {{customer_id}},
  'product_id': {{product_id}},
  'type' : {{type}},
  'response_code' : {{response_code}},
  'status' : {{status}},
  'serial_number' : {{serial_number}}
}
```

## response success

```javascript
//STATUS CODE 200
{
  'status' : true,
  'message' : 'Update transaction success.',
  'data' : {
      'response_code': '00',
      'transaction_id': '212121',
      'customer_number': '111222',
      'serial_number': '999999',
      'product_id': '31',
      'type': 'mobile',
      'order_id': 1,
      'status': 'success'
    }
}
```

## response failed ORDER ID not found

```javascript
//STATUS CODE 400
{
  'status' : false,
  'message' : "Order id not found!.",
  'data' : {
      'response_code': '00',
      'transaction_id': '212121',
      'customer_number': '111222',
      'serial_number': '999999',
      'product_id': '31',
      'type': 'mobile',
      'order_id': 929,
      'status': 'success'
    }
}
```


## response failed invalid response code

```javascript
//STATUS CODE 400
{
  'response_code': [
      'type invalid'
  ]
}
```
