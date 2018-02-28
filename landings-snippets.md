#Landings snippets
External analytics systems, for each of which we can add a code when creating/editing a campaign. 
##Endpoints
{% method %}
###`GET /landings-snippets`
Get a list of snippets.
{% sample lang="bash" %}
```bash
curl -X GET -v -b 'connect.sid=s%3AL7xQwNemYqilwERqH8tswYKfk6XfqcaC.P4qkrt3mUix3Dw6A2ze7Z9phswc%2FHIKqGYZ4YJyLYE0' http://dashboard.everad.com/v2/landings-snippets
```
######success response
```
[
  {
    "name": "Google",
    "external_id": "1"
  },
  {
    "name": "Яндекс",
    "external_id": "2"
  }
]
```
{% endmethod %}
