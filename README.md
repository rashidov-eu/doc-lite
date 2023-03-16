# Methods

* [Authentication](#authentication)
* [Get gadget metrics data](#get-gadget-metrics-data)

## Authentication

### Request

`POST /api/v1/auth`

#### Headers

* `Content-type: application/json`

#### Body

```json
{
    "username": "Your phone number",
    "password": "Your password"
}
```

### Response

```json
{
    "token": "Your token",
    "expirationDate": "Expiration date"
}
```

### Example

```shell
curl -X POST https://app.rashidov.eu/api/v1/auth                    \
-H "Content-type: application/json"                                 \
-d '{"username": "Your phone number", "password": "Your password"}'
```

## Get gadget metrics data

### Request

`GET /api/v1/metrics`

#### Headers

* `Content-type: application/json`
* `Auth-token: [token]`

#### Params

* `startDate`, format `YYYY-MM-DD`
* `endDate`, format `YYYY-MM-DD`
* `timezoneOffset`, in minutes, it uses to days bounds for gain calculation
* `scaleId`, optional

### Response

```json
{
    "ok": true,
    "gains": [
        {
            "date": "string with date",
            "[scaleId]": number
        },
        ...
    ],
    "values": [
        {
            "date": "string with date",
            "weigh": number,
            "temperature": number
        }
    ]
}
```

### Example

```shell
curl https://app.rashidov.eu/api/v1/metrics?startDate=2023-03-01&endDate=2023-03-08&timezoneOffset=60&gadgetId=421  \
-H "Content-type: application/json"                                                                                 \
-H "Auth-token: your token"
```
