#Campaigns
Manage your campaigns.
##Endpoints
{% method %}
###`GET /campaigns`
Get your campaigns.
{% sample lang="bash" %}
```bash
curl -X GET -v -b 'cpa_sid=s%3AL7xQwNemYqilwERqH8tswYKfk6XfqcaC.P4qkrt3mUix3Dw6A2ze7Z9phswc%2FHIKqGYZ4YJyLYE0' https://dashboard.everad.com/v2/campaigns
```
######success response
```
[{
    id
    created_at
    updated_at
    title
    is_active - flag indicating that campaign can receive traffic
    offer_id
    space_id
    currency - one of /lists/currencies
    postback_url
    postback_type - one of /lists/postback-types
    postback_ignore_trash - flag
    trafficback_url
    landing_domain
    landing_domain_type - one of /lists/campaign-domain-types
    transit_domain
    transit_domain_type - one of /lists/campaign-domain-types
    traffic_source - one of /lists/traffic-sources
    sid1_utm
    sid2_utm
    sid3_utm
    sid4_utm
    sid5_utm
    is_novostnik_on_transit_enabled
    is_novostnik_after_submit_enabled
    is_comebacker_enabled,
    domains: [{
        id -  one of /offers/<id> domains.id
    }],
    adv_system - one of /lists/adv-systems,
    landings_snippets_codes: {
        landing: [{id: 1, text: 'code'}], - id = external_id from /lists/landings-snippets
        transit: [{id: 1, text: 'code'}]
    } 
}]
```
{% endmethod %}
{% method %}
###`GET /campaigns/<id>`
Get a campaign by id.
{% sample lang="bash" %}
```bash
curl -X GET -v -b 'cpa_sid=s%3AL7xQwNemYqilwERqH8tswYKfk6XfqcaC.P4qkrt3mUix3Dw6A2ze7Z9phswc%2FHIKqGYZ4YJyLYE0' https://dashboard.everad.com/v2/campaigns/1
```
######success response
```
< HTTP/1.1 200 OK
{
    id
    created_at
    ...
}
```
{% endmethod %}
{% method %}
###`POST /campaigns`
Create a new campaign (required fields are marked with `*`).
```
*title
*offer_id - one of /offers with an `available` flag set to true
space_id - one of /spaces
postback_url
postback_type - one of /lists/postback-types
trafficback_url
*landing_domain - if local, should end with one of /lists/campaign-domains.
*landing_domain_type - one of /lists/campaign-domain-types
transit_domain - if local, should end with one of /lists/campaign-domains.
transit_domain_type - one of /lists/campaign-domain-types
sid1_utm
sid2_utm
sid3_utm
sid4_utm
sid5_utm
is_novostnik_on_transit_enabled
is_novostnik_after_submit_enabled
is_comebacker_enabled
*domains: [{
    *id - one of /offers/<id> domains.id   
}],
*adv_system - one of /lists/adv-systems,
landings_snippets_codes: {
    landing: [{id: 1, text: 'code'}], - id = external_id from /lists/landings-snippets
    transit: [{id: 1, text: 'code'}]
}
*currency - one of offers.<id>.payouts currency
```

{% sample lang="bash" %}
```bash
curl -X POST -v -H 'Content-type: application/json' -b 'cpa_sid=s%3AL7xQwNemYqilwERqH8tswYKfk6XfqcaC.P4qkrt3mUix3Dw6A2ze7Z9phswc%2FHIKqGYZ4YJyLYE0' -d '{"offer_id": 1, "landing_domain": "google.com", "landing_domain_type": "external", "domains": [{"id": 1}], "adv_system": "other", "currency": "usd"}' https://dashboard.everad.com/v2/campaigns
```
######success response
```
< HTTP/1.1 201 Created
```
{% endmethod %}
{% method %}
###`PUT /campaigns/<id>`
Update an existing campaign. Input fields are the same as when creating a new campaign.
{% sample lang="bash" %}
```bash
curl -X PUT -v -H 'Content-type: application/json' -b 'cpa_sid=s%3AL7xQwNemYqilwERqH8tswYKfk6XfqcaC.P4qkrt3mUix3Dw6A2ze7Z9phswc%2FHIKqGYZ4YJyLYE0' -d '{"offer_id": 1, "landing_domain": "google.com", "landing_domain_type": "external"}' https://dashboard.everad.com/v2/campaigns/1
```
######success response
```
< HTTP/1.1 200 OK
```
{% endmethod %}
{% method %}
###`DELETE /campaigns/<id>`
Remove a campaign.
{% sample lang="bash" %}
```bash
curl -X DELETE -v -b 'cpa_sid=s%3AL7xQwNemYqilwERqH8tswYKfk6XfqcaC.P4qkrt3mUix3Dw6A2ze7Z9phswc%2FHIKqGYZ4YJyLYE0' https://dashboard.everad.com/v2/campaigns/1
```
######success response
```
< HTTP/1.1 200 OK
```
{% endmethod %}
{% method %}
###`GET /:id/split-sessions` - available only for active session
Retrieve split sessions list for specified campaign.
{% sample lang="bash" %}
```bash
curl -X GET -v https://dashboard.everad.com/v2/lists/split-sessions/1
```
######success response
```
< HTTP/1.1 200 OK
[
  {
    "id": 1,
    "session_key": "dbdcb8a6-25b1-48f9-9fe6-084b79a36be3",
    "campaign_id": 11,
    "affiliate_id": 11,
    "created_at": "2017-05-08T07:50:29.710Z",
    "stopped_at": null
  }
]
```
{% endmethod %}


{% method %}
###`GET /:id/postback-log`
Retrieve postback logs for specified campaign.
{% sample lang="bash" %}
```bash
curl -X GET -v https://dashboard.everad.com/v2/campaigns/1/postback-log
```
######success response
```
< HTTP/1.1 200 OK
[
  {
    "date": "2017-05-08T07:50:29.710Z",
    "affiliate_id": 1,
    "campaign_id": 11,
    "conversion_id": 123,
    "type": "campaign",
    "url": "https://trololo.requestcatcher.com/...traffic_type=desktop&sid1=&status=pending&payout=2.00&currency=usd"
    "status": 200 
  }
]
```
{% endmethod %}