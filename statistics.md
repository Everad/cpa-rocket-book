#Analytics
Get your traffic and conversions statistics. 

Encode below parameters in using standard query string format for array and objects, e.g. `?someParam[]=someValue1&someParam[]=someValue2` for arrays and `?someParam[someKey1]=someValue1&someParam[someKey2]=someValue2` for objects.
{% method %}
###`GET /analytics/general`
Get date ranged general statistics

**Query parameters:**

```
lang - desired response language (session language by default)
date_range: { -- desired date range (with correct hours, e.g. end of day: 23:59:59.999999)
    start (YYYY-MM-DD HH:mm:ss.SSS)
    end (YYYY-MM-DD HH:mm:ss.SSS)
}
currency -- one of user balances currency
groups: ['date', 'hour', 'dow', 'offer', 'landing', 'transit', 'country', 'city', 'campaign', 'campaign_type', 'traffic_type', 'sid1', 'sid2', 'sid3', 'sid4', 'sid5'] -- several values available
filters: {
    offers: [ids] -- one of /analytics/lists/offers,
    landings: [ids] -- one of /analytics/lists/landings, 
    transits: [ids] -- one of /analytics/lists/transits, 
    countries: [ids] -- one of /analytics/lists/countries,
    cities: [ids] -- one of /analytics/lists/cities, 
    campaigns: [ids] -- one of /analytics/lists/campaigns, 
    campaign_types: [types] -- one of /lists/campaign-types,
    traffic_types: [types] -- one of /lists/traffic-types, 
    sids1: [sid1] -- one of /analytics/lists/sids1, 
    sids2: [sid2] -- one of /analytics/lists/sids2, 
    sids3: [sid3] -- one of /analytics/lists/sids3, 
    sids4: [sid4] -- one of /analytics/lists/sids4, 
    sids5: [sid5] -- one of /analytics/lists/sids5,
    affiliates: [ids] -- one of `/master-account/` . available only for master accounts. by default all stats from master and children account is shown
}
inverse_filters: -- same parameters but inverse filtering
```

{% sample lang="bash" %}
```bash
curl -v -g -X GET -b 'cpa_sid=s%3AvJyC27a4pDMt58b2m_7BNyW4FD9Y0UUG.gbDlAoNjiOA8jmBHC68FCWzoLtYA0Cw9xVRuzErQXAA' https://dashboard.everad.com/v2/analytics/general?lang=ru&currency=rub&date_range[start]=2017-01-01&date_range[end]=2017-02-23%2023:59:59.99999&groups[]=offer&filters[landings][]=5
```
######success response
```
< HTTP/1.1 200 OK
[{"hosts":"6","hits":"6","transitions":"0","accepted_conversions":"0","pending_conversions":"2","declined_conversions":"0","total_conversions":"2","invalid_conversions":"0","accepted_income":"0","pending_income":"200.00","declined_income":"0","offer":"beer"}]
```
{% endmethod %}
{% method %}
###`GET /analytics/conversions`
Get date ranged conversions statistics

**Query parameters:**

```
lang - desired response language (session language by default)
date_range: { -- desired date range (with correct hours, e.g. end of day: 23:59:59.999999)
    start (YYYY-MM-DD HH:mm:ss.SSS)
    end (YYYY-MM-DD HH:mm:ss.SSS)
}
currency -- one of user balances currency (optional)
filters: --same as in general analytics
inverse_filters: -- same parameters but inverse filtering

```

{% sample lang="bash" %}
```bash
curl -v -g -X GET -b 'cpa_sid=s%3AvJyC27a4pDMt58b2m_7BNyW4FD9Y0UUG.gbDlAoNjiOA8jmBHC68FCWzoLtYA0Cw9xVRuzErQXAA' https://dashboard.everad.com/v2/analytics/conversions?lang=ru&currency=rub&date_range[start]=2017-01-01&date_range[end]=2017-02-23%2023:59:59.99999
```
######success response
```
< HTTP/1.1 200 OK
[{"ip":"95.31.18.119","referer":null,"user_agent":"curl/7.47.0","affiliate":"child1@example.com","campaign":"beer campaign","date":"2017-03-06 07:23:59","campaign_type":"novostnik","traffic_type":"bot","status":"approved","currency":"rub","payout":"100.00","id":5,"bonus":"900.00","sid1":null,"sid2":null,"sid3":null,"sid4":null,"sid5":null,"offer":"beer","landing":"landing1","transit":null,"country":"Россия","city":"Москва"}]
```
{% endmethod %}
{% method %}
###`GET /analytics/lists/<field>`
Get avaialable *field* values (up to 5) for filtering analytics requests

**Query parameters:**

```
lang - desired response language (session language by default)
date_range: { -- desired date range (with correct hours, e.g. end of day: 23:59:59.999999)
    start
    end
}
currency -- one of user balances currency
query -- user lookup query
```

{% sample lang="bash" %}
```bash
curl -v -g -X GET -H 'Content-type: application/json' -b 'cpa_sid=s%3AGgkhSULlAbbYwHhCXkOH3CN35FKgQtSo.cPt18fvgg94A2G4Vo%2FmE%2Ff3d%2F%2BF8d8ifqBjjAWkUn9o' https://localhost:4001/v2/analytics/lists/countries?query=po&currency=rub&date_range[end]=2017-02-23%2023:59:59.99999
```
######success response
```
< HTTP/1.1 200 OK
[{"id":2017370,"text":"Россия"}]
```
{% endmethod %}