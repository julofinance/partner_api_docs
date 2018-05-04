# SEPULSA API CALLBACK

API callback for update transaction.

## base url:
  - Development `https://api-dev.julofinance.com` 
  - Staging `https://api-staging.julofinance.com`
  - Production `https://api.julofinance.com`
  
## IP:
  - Development `52.220.237.20` 
  - Staging `13.228.4.68`
  - Production `13.229.235.68`

## list ur api:

| METHOD | URL | DESCRIPTION |
| ------ | ------ | ------ |
| POST | `base_url`/api/integration/v1/callbacks/sepulsa/transaction | update transaction |

---

# Update Transaction
API for update transaction success or failed.

## Requirments:

| Field | Type | Validate |
| ------ | ------ | ------ |
| transaction_id | String | Mandatory  |
| order_id | Integer | Mandatory  |
| customer_number | String | Mandatory  |
| product_id | String | Mandatory  |
| type | String | Mandatory  |
| response_code | String | Mandatory , ['00','10','20','21','22','23','24','25','50','98','99'] |
| status | String | Mandatory  |
| serial_number | String | Mandatory  |


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
