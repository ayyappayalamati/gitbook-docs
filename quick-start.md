# Quick Start

{% hint style="info" %}
**Good to know:** A quick start guide can be good to help folks get up and running with your API in a few steps. Some people prefer diving in with the basics rather than meticulously reading every page of documentation!
{% endhint %}

## Get your API keys

We use API keys to allow access to the API. If you are a new partner and want to register with a new username and password, please contact us at **contact@cashforcars.com**. If you already have a username and password, please go ahead and follow the process below.

Our API's expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: eyJhbGciOiJIUzI1NiJ9....`

## Make your first request

**Token Generation API**.

{% swagger baseUrl="https://partner.cashforcars.com/api/v1/publishers/toke" method="post" path="n" summary="Token Generation API." %}
{% swagger-description %}
Issues a token upon validation of provided username and password.
{% endswagger-description %}

{% swagger-parameter in="body" name="partnerId" required="true" type="string" %}
partnerId
{% endswagger-parameter %}

{% swagger-parameter in="body" name="password" required="true" type="string" %}
password
{% endswagger-parameter %}

{% swagger-response status="200" description="Token successfully generated" %}
```javascript
{
    "access_token": "xxxxxxxxxxxxxxxxxxxxxxx",
    "refresh_token": "xxxxxxxxxxxxxxxxxxxxxxx"
}
```
{% endswagger-response %}

{% swagger-response status="401: Unauthorized" description="Authentication credentials are missing or invalid." %}
```javascript
{
    "timestamp": "xxxxxxxxxxxxxxxxxxxxxxx",
    "status": "error",
    "error_code": "Unauthorized",
    "message": "Unauthorized",
    "description": "Authentication credentials are missing or invalid."
}
```
{% endswagger-response %}

{% swagger-response status="403: Forbidden" description="You don't have authorization" %}
```javascript
{
    "timestamp": "xxxxxxxxxxxxxxxxxxxxxxx",
    "status": "error",
    "error_code": "Forbidden",
    "message": "Forbidden",
    "description": "You don't have authorization."
}
```
{% endswagger-response %}
{% endswagger %}

Take a look at how you might call this method using our official libraries, or via `curl`:

{% tabs %}
{% tab title="curl" %}
```
curl https://partner.cashforcars.com/api/v1/publishers/token 
    -d partnerId='xxxxx'  
    -d password='xxxxx'
```
{% endtab %}

{% tab title="Node" %}
```javascript
const axios = require('axios');

const url = 'https://partner.cashforcars.com/api/v1/publishers/token';
const data = {
  partnerId: 'xxxxx',
  password: 'xxxxx'
};

axios.post(url, data)
  .then(response => {
    console.log(response.data);
  })
  .catch(error => {
    console.error(`Error: ${error.response.status}\n${error.response.data}`);
  });
```
{% endtab %}

{% tab title="Python" %}
```python
import requests

response = requests.post("https://partner.cashforcars.com/api/v1/publishers/token", data={"partnerId": "xxxxx", "password": "xxxxx"})

print(response.text) if response.ok else print(f"Error: {response.status_code}\n{response.text}")

```
{% endtab %}
{% endtabs %}
