# User Registration

{% api-method method="post" host="" path="/api/v1/register/" %}
{% api-method-summary %}
User Registration
{% endapi-method-summary %}

{% api-method-description %}
User registration endpoint.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-body-parameters %}
{% api-method-parameter name="username" type="string" required=true %}
A username can contain any uppercase, lowercase, or numbers
{% endapi-method-parameter %}

{% api-method-parameter name="password" type="string" required=true %}
The plain text password.
{% endapi-method-parameter %}

{% api-method-parameter name="email" type="string" required=true %}

{% endapi-method-parameter %}

{% api-method-parameter name="fullName" type="string" required=true %}

{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Registered and Email Verification has been sent.
{% endapi-method-response-example-description %}

```javascript
{
    "username": "aaa",
    "fullName": "aaaa",
    "emailAddress": "user@email.com",
    "registration_id": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJlbWFpbCI6ImFzZGFzZmFzZmdAZWFtYS5jb20iLCJleHAiOjE1MzA3NzIzNTkxNTl9.QZn-KRgtlG6km6QhzObacubhzuDuU5oOkAOCPTWk2IU"
}
```
{% endapi-method-response-example %}
{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Registered and Email Verification has been sent 2.
{% endapi-method-response-example-description %}

```javascript
{
    "username": "aaa",
    "fullName": "aaaa",
    "emailAddress": "user@email.com",
    "registration_id": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJlbWFpbCI6ImFzZGFzZmFzZmdAZWFtYS5jb20iLCJleHAiOjE1MzA3NzIzNTkxNTl9.QZn-KRgtlG6km6QhzObacubhzuDuU5oOkAOCPTWk2IU"
}
```
{% endapi-method-response-example %}
{% api-method-response-example httpCode=400 %}
{% api-method-response-example-description %}
Incomplete Fields or Validation errors.
{% endapi-method-response-example-description %}

```javascript
{
    "email": ["This email is already used"],
    "password": ["Password too short"],
    "username": ["Username is taken", "Username is not allowed."],
    "fullName": ["This field is required"]
}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="/" path="entrance/verify-email" %}
{% api-method-summary %}
Email Verification
{% endapi-method-summary %}

{% api-method-description %}
Verify Email
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-query-parameters %}
{% api-method-parameter name="token" type="string" required=false %}
A random url-safe string. This is the email proof of the registered user.
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Responses in 2 ways.  
If JSON Response is requested it will respond with \`OK\`. Otherwise  
It will redirect to the home page that tell's that the email has been confirmed and the user is automatically logged in.
{% endapi-method-response-example-description %}

```
OK
```
{% endapi-method-response-example %}

{% api-method-response-example httpCode=400 %}
{% api-method-response-example-description %}
Verification Failed. Either the verification link is expired or used.
{% endapi-method-response-example-description %}

```
Token Expired/Invalid
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

