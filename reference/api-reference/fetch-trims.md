# Fetch Trims

**Note**[**:**](#user-content-fn-1)[^1] If you have the VIN number handy, you can skip the step of fetching years, makes, models, and directly proceed to the 'Get Offer' API page. Having the VIN eliminates the need to input Year, Make, Model, and Trim.

## Retrieve trims

{% swagger baseUrl="https://www.cashforcars.com/publishers/v3/" method="get" path="trims/{year}/{make}/{model}" summary="Retrieve list of trims" %}
{% swagger-description %}
Retrieve list of trims.
{% endswagger-description %}

{% swagger-parameter in="header" name="Authorization" type="string" required="true" %}
The Authorization header provides credentials for accessing a protected resource.
{% endswagger-parameter %}

{% swagger-parameter in="header" name="correlationId" required="true" type="string" %}
A UUID or any string uniquely identifying each request. It is used to trace the complete lifecycle of a particular request; therefore, it should be uniquely generated for every request
{% endswagger-parameter %}

{% swagger-parameter in="header" name="source" type="string" required="true" %}
Company Name - Here, you can pass the company name used to identify the client/source of each request
{% endswagger-parameter %}

{% swagger-parameter in="path" name="year" type="string" required="true" %}

{% endswagger-parameter %}

{% swagger-parameter in="path" name="make" type="string" required="true" %}

{% endswagger-parameter %}

{% swagger-parameter in="path" name="model" type="string" required="true" %}

{% endswagger-parameter %}

{% swagger-response status="200" description="Request was successful" %}
```javascript
{
    "status": "success",
    "message": "Request was successful",
    "data": {
      "years": [
        "2012",
        "2011",
        "........."
      ]
    },
    "correlationId": "xxxxxxxx"
    
}
```
{% endswagger-response %}

{% swagger-response status="400: Bad Request" description="" %}

{% endswagger-response %}

{% swagger-response status="401: Unauthorized" description="Permission denied" %}

{% endswagger-response %}

{% swagger-response status="403: Forbidden" description="" %}

{% endswagger-response %}

{% swagger-response status="500: Internal Server Error" description="" %}

{% endswagger-response %}
{% endswagger %}

[^1]: 
