#Spaces
Manage your traffic sources, used in campaigns.
##Endpoints
{% method %}
####`GET /spaces`

List your spaces.
{% sample lang="bash" %}
```bash
curl -X GET -b 'cpa_sid=s%3AL7xQwNemYqilwERqH8tswYKfk6XfqcaC.P4qkrt3mUix3Dw6A2ze7Z9phswc%2FHIKqGYZ4YJyLYE0' -v https://dashboard.everad.com/v2/spaces
```
######success response
```
< HTTP/1.1 200 OK
[{"id":1,"title":"test space", "type":"social"}]
```
{% endmethod %}
{% method %}
####`GET /spaces/<id>`
Get space data
######success response - same as array item from `/spaces` request.
{% endmethod %}

{% method %}
####`POST /spaces`

Create a new space.
{% sample lang="bash" %}
```bash
curl -X POST -H 'Content-type: application/json' -d '{"title":"test space", "type":"social"}' -b 'cpa_sid=s%3AL7xQwNemYqilwERqH8tswYKfk6XfqcaC.P4qkrt3mUix3Dw6A2ze7Z9phswc%2FHIKqGYZ4YJyLYE0' -v https://dashboard.everad.com/v2/spaces
```
######success response
```
< HTTP/1.1 201 Created
```
{% endmethod %}
{% method %}
####`PUT /spaces/<id>`

Update a space.
{% sample lang="bash" %}
```bash
curl -X PUT -H 'Content-type: application/json' -d '{"title":"test space1", "type":"social"}' -b 'cpa_sid=s%3AL7xQwNemYqilwERqH8tswYKfk6XfqcaC.P4qkrt3mUix3Dw6A2ze7Z9phswc%2FHIKqGYZ4YJyLYE0' -v https://dashboard.everad.com/v2/spaces/1
```
######success response
```
< HTTP/1.1 200 OK
```
{% endmethod %}
{% method %}
####`DELETE /spaces/<id>`

Delete a space.
{% sample lang="bash" %}
```bash
curl -X DELETE -b 'cpa_sid=s%3AL7xQwNemYqilwERqH8tswYKfk6XfqcaC.P4qkrt3mUix3Dw6A2ze7Z9phswc%2FHIKqGYZ4YJyLYE0' -v https://dashboard.everad.com/v2/spaces/1
```
######success response
```
< HTTP/1.1 200 OK
```
{% endmethod %}