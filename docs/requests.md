### URI / Method

All requests should be made to the URI and method specified on each section. 

### Headers

You should always include the following headers on your request:

Key           | Value
------------- | ---------------------------------
Content-Type  | application/json, charset=UTF-8
Accept        | application/json, text/plain, \*/\*
Cache         | no-cache
Authorization | Bearer TOKEN

The `TOKEN` details will be provided by an Automizer.cloud representative. 

### HTTP Errors

The API can generate the following HTTP errors:

Error | Description
------| --------------------------------------------------------------------------------------------
401   | Unauthenticated. You failed to provide the `Authorization` header or the `TOKEN` is invalid.
403   | Forbidden. You are not authorized to access the specified resource.
404   | Not found. The specified resource could not be found.
501   | Role not enabled for the specified action.

The response body will also include the following JSON with the error description:

```
{
    "error": {
        "code": 401,
        "message": "Unauthenticated"
    }
}
```

### Rate limit

The API is limited to 15 requests per minute per user.

If the limit is exceeded, you'll receive a `429 HTTP error` with the following body: `Too Many Attempts.`

You can check the response headers to determine how many requests you have left:

Header                | Present       | Description
--------------------- | ------------- | ----------------------------------------------------------------------------
x-ratelimit-limit     | Always        | The number of requests allowed per minute.
x-ratelimit-remaining | Always        | The number of requests remaining for the current minute.
x-ratelimit-reset     | Limit reached | The time at which the current rate limit window resets in UTC epoch seconds.
