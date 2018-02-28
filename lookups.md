#Lookups
{% method %}
####`GET /lookups/offers`
Return up to 5 results based on query. Only offers, available for campaign creation, can be returned.

**Params:**

`query` - title part (optional)

`lang` - query lang (optional, profile language used by default)

`only_available` - flag for only connected offers lookup

{% sample lang="bash" %}
```bash
curl -X GET -b 'connect.sid=s%3AL7xQwNemYqilwERqH8tswYKfk6XfqcaC.P4qkrt3mUix3Dw6A2ze7Z9phswc%2FHIKqGYZ4YJyLYE0' -v https://dashboard.everad.com/v2/lookups/offers?title=intox

### To test non-English lookup with curl, you'll need the following command syntax:

curl -X GET -b 'cpa_sid=s%3AKYaiGDA6QNmBM_S4xtY7vZJzYV_D8-8c.Yjmbs%2Fjz3ofZckJjWEjH3fTQXB%2Bk9%2BLNeeEowSvaMto' -v https://dashboard.everad.com/v2/lookups/offers -G --data-urlencode "query=тест"
```
######success response
```
< HTTP/1.1 200 OK
[{"id":"1","text":"intoxic"},{"id":"2","text":"intoxic+"}]
```
{% endmethod %}