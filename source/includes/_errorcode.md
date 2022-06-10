# Error Code

<aside class="notice">
This error section applies to all paraholic API calls.
</aside>


The Paraholic API uses the following error codes:

Error Code | Meaning | Description
:----: | ------- |  ------- |
400 | Bad Request | The request is invalid.
401 | Unauthorized | The API key is invalid.
404 | Not Found | The specified object could not be found.
429 | Too Many Requests | APIkey rate limit has been exceeded.
500 | Internal Server Error | The servers could not respond your request due to an internal error.
503 | Service Unavailable | The services is temporarily offline for maintenance. Please try again later.

(status code 200 is returned if the request is handled without any error)
