#Offers
List available offers.
##Endpoints
{% method %}
####`GET /offers`

Get available offers. Availability is marked with an `available` flag. If it's `true` - you can create campaigns with this offer. Otherwise an access request is required (see support section).
{% sample lang="bash" %}
```bash
curl -X GET -b 'cpa_sid=s%3AL7xQwNemYqilwERqH8tswYKfk6XfqcaC.P4qkrt3mUix3Dw6A2ze7Z9phswc%2FHIKqGYZ4YJyLYE0' -v https://dashboard.everad.com/v2/offers
```
######success response
```
< HTTP/1.1 200 OK
[{
    id
    title
    subtitle
    category - one of /lists/offer-categories
    short_description
    description
    rules
    domain
    is_exclusive
    locations: [
        name
        country_code
        is_own_callcenter
        price
        currency - one of /lists/currencies
    ],
    domains: [{
        id
        type - one of /lists/domain-types
        title
        domain
    }],
    payouts: [{
        location - location name
        location_id - location id
        country_code
        traffic_type - one of /lists/traffic-types
        traffic_source - one of /lists/traffic-sources
        amount
        currency - one of /lists/currencies
    }],
    available: true,
    cr,
    epc,
    image,
    display_priority - integer from 1 and above
}]
```
{% endmethod %}
{% method %}
####`GET /offers/<id>`
Get offer data
######success response - same as array item from `/offers` request.
{% endmethod %}
{% method %}
####`GET /offers/<id>/request`
Request offer access. If access is granted, returns `200`, if not - returns `403`. 
{% sample lang="bash" %}
```bash
curl -X GET -b 'cpa_sid=s%3AL7xQwNemYqilwERqH8tswYKfk6XfqcaC.P4qkrt3mUix3Dw6A2ze7Z9phswc%2FHIKqGYZ4YJyLYE0' -v https://dashboard.everad.com/v2/offers/1/request
```
######success response
```
< HTTP/1.1 200 OK
```
######error response
```
< HTTP/1.1 403 Forbidden
```

{% endmethod %}
{% method %}
####`GET /offers/<id>/news`
Get offer news.
{% sample lang="bash" %}
```bash
curl -X GET -b 'cpa_sid=s%3AL7xQwNemYqilwERqH8tswYKfk6XfqcaC.P4qkrt3mUix3Dw6A2ze7Z9phswc%2FHIKqGYZ4YJyLYE0' -v https://dashboard.everad.com/v2/offers/1/news
```
######success response - same as general news

{% endmethod %}

{% method %}
####`GET /offers/<id>/geo-stats?currency=usd&date_range...`
Get offer's statistics by it's locations. Date range is optional, defualt to from -7 days to -1 day
{% sample lang="bash" %}
```bash
curl -X GET -b 'cpa_sid=s%3AL7xQwNemYqilwERqH8tswYKfk6XfqcaC.P4qkrt3mUix3Dw6A2ze7Z9phswc%2FHIKqGYZ4YJyLYE0' -v https://dashboard.everad.com/v2/offers/1/geo-stats?currency=usd
```
######success response
```
< HTTP/1.1 200 OK
[{
    country_code: 'UA',
    cr: 13.989898,
    approve: 4.0909
}, {
    country_code: 'RU',
    cr: 0,
    approve: 1.0909
}]
```

{% endmethod %}