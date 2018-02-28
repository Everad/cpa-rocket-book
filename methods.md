# Session
Session data is passed over an http cookie, returned to you on calling `PUT` or `POST` methods - login and registration. Use this cookie to authorize further requests when needed.
##Endpoints
{% method %}
####`POST /session`

Register your affiliate account and get session cookie at once.
```
email
password
language - one from `/lists/languages`
timezone - one from `/lists/timezones`
```
{% sample lang="bash" %}
```bash
curl -X POST -H 'Content-type: application/json' -d '{"email":"test2@example.com", "password":"1", "language":"ru"}' -v https://dashboard.everad.com/v2/session
```
######success response
```
< HTTP/1.1 201 OK
< set-cookie: cpa_sid=s%3AL7xQwNemYqilwERqH8tswYKfk6XfqcaC.P4qkrt3mUix3Dw6A2ze7Z9phswc%2FHIKqGYZ4YJyLYE0; Path=/; Expires=Fri, 17 Mar 2017 08:49:53 GMT; HttpOnly
```
######error response
```bash
< HTTP/1.1 400 Bad Request
[{"keyword":"uniqueAffiliateEmail","dataPath":".email","schemaPath":"#/properties/email/uniqueAffiliateEmail","params":{"keyword":"uniqueAffiliateEmail"},"message":"should pass \"uniqueAffiliateEmail\" keyword validation"}]
```
{% endmethod %}
{% method %}
###`PUT /session`
Login to your already registered account.
{% sample lang="bash" %}
```bash
curl -X PUT -H 'Content-type: application/json' -d '{"email":"test2@example.com", "password":"1"}' -v https://dashboard.everad.com/v2/session
```
######success response
```
< HTTP/1.1 200 OK
< set-cookie: cpa_sid=s%3AL7xQwNemYqilwERqH8tswYKfk6XfqcaC.P4qkrt3mUix3Dw6A2ze7Z9phswc%2FHIKqGYZ4YJyLYE0; Path=/; Expires=Fri, 17 Mar 2017 08:49:53 GMT; HttpOnly
```
######error response
```bash
< HTTP/1.1 400 Bad Request
```
{% endmethod %}
{% method %}
###`DELETE /session`
Logout from your account.
{% sample lang="bash" %}
```bash
curl -X DELETE -v -b 'cpa_sid=s%3AL7xQwNemYqilwERqH8tswYKfk6XfqcaC.P4qkrt3mUix3Dw6A2ze7Z9phswc%2FHIKqGYZ4YJyLYE0' https://dashboard.everad.com/v2/session
```
######success response
```
< HTTP/1.1 200 OK
```
{% endmethod %}

{% method %}
###`POST /session/password`
Remind password
{% sample lang="bash" %}
```bash
curl -X POST -v -H 'Content-type: application/json' -d '{"email":"test@example.com"} https://dashboard.everad.com/v2/session/password
```
######success response
```
< HTTP/1.1 201 OK
```
{% endmethod %}