#Master account
Manage your child accounts (when in master mode)
##Endpoints
{% method %}
####`GET /master-account`
Get list of all child affiliate accounts.
{% sample lang="bash" %}
```bash
curl -v -X GET -b 'cpa_sid=s%3AjqL-ubOG0LAvIsQf2cfHT9EnMvgkLtZH.B4LmgxlrTpnmmHD6VXxVdTbwIkWuZOQ2ZtK1%2FQnMKys' https://dashboard.everad.com/v2/master-account
```
######success response
```
< HTTP/1.1 200 OK
[{"id":88,"email":"child1@example.com"}]
```
{% endmethod %}

{% method %}
####`GET /master-account/child-offer-payouts/<child_affiliate_id>/<offer_id>`
Get list of child account offer payouts
{% sample lang="bash" %}
```bash
curl -v -X GET -b 'cpa_sid=s%3AjqL-ubOG0LAvIsQf2cfHT9EnMvgkLtZH.B4LmgxlrTpnmmHD6VXxVdTbwIkWuZOQ2ZtK1%2FQnMKys' https://dashboard.everad.com/v2/master-account/child-offer-payouts/88/1
```
######success response (same as `/offers/<id>` .payouts for your account)
```
< HTTP/1.1 200 OK
[{"traffic_type":null,"traffic_source":null,"amount":100,"location":"Россия","location_id":2017370}]
```

{% endmethod %}
{% method %}
####`PUT /master-account/child-offer-payouts/<child_affiliate_id>/<offer_id>`
Set child account payout settings for specified offer (offer become available for this account if it has corresponding balance)
```
location_id
traffic_type - one from `/lists/traffic-types` or `null`
traffic_source - one from `/lists/traffic-sources` or `null`
amount - from `0.01` to your account current payout amount

N.B. only values from your personal payout settings can be passed.
```

{% sample lang="bash" %}
```bash
curl -v -X PUT -b 'cpa_sid=s%3AjqL-ubOG0LAvIsQf2cfHT9EnMvgkLtZH.B4LmgxlrTpnmmHD6VXxVdTbwIkWuZOQ2ZtK1%2FQnMKys' -H 'Content-type: application/json' -d '[{"location_id":"2017370", "traffic_type": null, "traffic_source": null, "amount":100}]' https://dashboard.everad.com/v2/master-account/child-offer-payouts/88/1
```
######success response
```
< HTTP/1.1 200 OK
```
{% endmethod %}
