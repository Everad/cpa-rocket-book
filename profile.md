#Profile
Manage your profile information.
{% method %}
###`GET /profile/balances`
Get account balances. A balance is a wallet for a single currency.
{% sample lang="bash" %}
```bash
curl -X GET -v -b 'cpa_sid=s%3AL7xQwNemYqilwERqH8tswYKfk6XfqcaC.P4qkrt3mUix3Dw6A2ze7Z9phswc%2FHIKqGYZ4YJyLYE0' https://dashboard.everad.com/v2/profile/balances
```
######success response
```
< HTTP/1.1 200 OK
[
  {
    "currency": "rub",
    "amount": "0.00",
    "hold_amount": "0.00"
  }
]
```
{% endmethod %}
{% method %}
###`POST /profile/balances`
Create a new balance for desired currency. Only one currency balance can be created per account.
{% sample lang="bash" %}
```bash
curl -X POST -v -H 'Content-type: application/json' -d '{"currency": "usd"}' -b 'cpa_sid=s%3AL7xQwNemYqilwERqH8tswYKfk6XfqcaC.P4qkrt3mUix3Dw6A2ze7Z9phswc%2FHIKqGYZ4YJyLYE0' https://dashboard.everad.com/v2/profile/balances
```
######success response
```
< HTTP/1.1 201 OK
```
{% endmethod %}

{% method %}
###`PUT /profile/password`
Change your profile password.
{% sample lang="bash" %}
```bash
curl -X PUT -v -H 'Content-type: application/json' -d '{"old_password": "1", "new_password":"2"}' -b 'cpa_sid=s%3AL7xQwNemYqilwERqH8tswYKfk6XfqcaC.P4qkrt3mUix3Dw6A2ze7Z9phswc%2FHIKqGYZ4YJyLYE0' https://dashboard.everad.com/v2/profile/password
```
######success response
```
< HTTP/1.1 200 OK
```
######error response
```bash
< HTTP/1.1 400 Bad Request
```
{% endmethod %}
{% method %}
###`GET /profile/manager`
Get your manager contact info.
{% sample lang="bash" %}
```bash
curl -X GET -H 'Content-type: application/json' -b 'cpa_sid=s%3AZ7vljuUpdxc4dYVpKIaSkne_18SkDvjm.WQwobn6eVQ%2BNOo%2FOtmocjGRm8HZcQxw9c2W9ncpa7RM' -v https://dashboard.everad.com/v2/profile/manager
```
######success response
```
< HTTP/1.1 200 OK
{
  "email":"Gregory.Powlowski@hotmail.com",
  "skype":"regory.Powlowski"
}
```
{% endmethod %}
{% method %}
###`GET /profile`
Get general info about your profile.
{% sample lang="bash" %}
```bash
curl -X GET -v -b 'cpa_sid=s%3AL7xQwNemYqilwERqH8tswYKfk6XfqcaC.P4qkrt3mUix3Dw6A2ze7Z9phswc%2FHIKqGYZ4YJyLYE0' https://dashboard.everad.com/v2/profile
```
######success response
```
< HTTP/1.1 200 OK
{
    language
    email
    skype
    phone
    avatar
    contest_points
    is_master - flag indicating master mode (see `Master account` section)
    status - one of /lists/affiliate-statuses
    timezone - one of /list/timezones
}
```
{% endmethod %}
{% method %}
###`PUT /profile`
Update your profile general info.
```
language - one of /lists/languages
phone
skype - can only be updated if previously was empty
```
{% sample lang="bash" %}
```bash
curl -X GET -v -H 'Content-type: application/json' -d '{"phone": "11111"}' -b 'cpa_sid=s%3AL7xQwNemYqilwERqH8tswYKfk6XfqcaC.P4qkrt3mUix3Dw6A2ze7Z9phswc%2FHIKqGYZ4YJyLYE0' https://dashboard.everad.com/v2/profile
```
######success response
```
< HTTP/1.1 200 OK
```
{% endmethod %}
{% method %}
###`GET /profile/payout-systems`
Get available payout systems for your profile balance currencies
{% sample lang="bash" %}
```bash
curl -v -X GET -b 'cpa_sid=s%3A8D9teXFlvopv65U1YFayTgBT5iq9WS3R.rhDzTzI4blRSzPwGe6P0PNiZa0otDLMvF4rwsEK4QuU' https://dashboard.everad.com/v2/profile/payout-systems
```
######success response
```
< HTTP/1.1 200 OK
[
  {
    "id":1,
    "title":"рубли наличными",
    "currency":"rub",
    "fields":{
      "account":{
        "type":"string"
      }
    },
    "credentials":null
  }
]
```
{% endmethod %}
{% method %}
###`PUT /profile/payout-systems/<id>`
Update payout system's credentials (based on fields from `/profile/payout-systems` request)
{% sample lang="bash" %}
```bash
curl -v -X PUT -H 'Content-type: application/json' -d '{"account": "кошель"}' -b 'cpa_sid=s%3A8D9teXFlvopv65U1YFayTgBT5iq9WS3R.rhDzTzI4blRSzPwGe6P0PNiZa0otDLMvF4rwsEK4QuU' https://dashboard.everad.com/v2/profile/payout-systems/1
```
######success response
```
< HTTP/1.1 200 OK
```
{% endmethod %}
{% method %}
###`GET /profile/novostnik`
{% sample lang="bash" %}
```bash
curl -X GET -b 'cpa_sid=s%3AZ7vljuUpdxc4dYVpKIaSkne_18SkDvjm.WQwobn6eVQ%2BNOo%2FOtmocjGRm8HZcQxw9c2W9ncpa7RM' -v https://dashboard.everad.com/v2/profile/novostnik
```
######success response
```
< HTTP/1.1 200 OK
{
  "novostnik_domain": "test.com",
  "novostnik_domain_type": "external",
  "novostnik_postback_url": "test.postback.com",
  "novostnik_postback_type": "approve"
}
```
{% endmethod %}
{% method %}
###`PUT /profile/novostnik`
Update profile personal news page (novostnik) settings.
{% sample lang="bash" %}
```bash
curl -X PUT -H 'Content-type: application/json' -b 'cpa_sid=s%3AZ7vljuUpdxc4dYVpKIaSkne_18SkDvjm.WQwobn6eVQ%2BNOo%2FOtmocjGRm8HZcQxw9c2W9ncpa7RM' -d '{ "novostnik_domain": "test.com", "novostnik_domain_type": "external", "novostnik_postback_url": "test.postback.com", "novostnik_postback_type": "approve", "novostnik_postback_ignore_trash": true}' -v https://dashboard.everad.com/v2/profile/novostnik
```
######success response
```
< HTTP/1.1 200 OK
```
{% endmethod %}
{% method %}
###`GET /profile/global-postback`
Retrieve profile global postback settings.
{% sample lang="bash" %}
```bash
curl -X GET -b 'cpa_sid=s%3AZ7vljuUpdxc4dYVpKIaSkne_18SkDvjm.WQwobn6eVQ%2BNOo%2FOtmocjGRm8HZcQxw9c2W9ncpa7RM' -v https://dashboard.everad.com/v2/profile/global-postback
```
######success response
```
< HTTP/1.1 200 OK
{
  "global_postback_url": "test.com",
  "global_postback_type": "approve",
  "global_postback_ignore_trash": true
}
```
{% endmethod %}
{% method %}
###`PUT /profile/global-postback`
Update profile global postback settings.
{% sample lang="bash" %}
```bash
curl -X PUT -H 'Content-type: application/json' -b 'cpa_sid=s%3AZ7vljuUpdxc4dYVpKIaSkne_18SkDvjm.WQwobn6eVQ%2BNOo%2FOtmocjGRm8HZcQxw9c2W9ncpa7RM' -d '{ "global_postback_url": "test.com", "global_postback_type": "approve", "global_postback_ignore_trash": true }' -v https://dashboard.everad.com/v2/profile/global-postback
```
######success response
```
< HTTP/1.1 200 OK
```
{% endmethod %}
{% method %}
###`PUT /profile/notifications`
Update profile notification settings.
{% sample lang="bash" %}
```bash
curl -X PUT -H 'Content-type: application/json' -b 'cpa_sid=s%3AZ7vljuUpdxc4dYVpKIaSkne_18SkDvjm.WQwobn6eVQ%2BNOo%2FOtmocjGRm8HZcQxw9c2W9ncpa7RM' -d '{ "offer_change": [], "new_offer": ["sms"], "new_ticket": ["email", "sms"] }' -v https://dashboard.everad.com/v2/profile/notifications
```
######success response
```
< HTTP/1.1 200 OK
```
{% endmethod %}
{% method %}
###`GET /profile/notifications`
Retrieve profile notification settings.
{% sample lang="bash" %}
```bash
curl -X GET -b 'cpa_sid=s%3AZ7vljuUpdxc4dYVpKIaSkne_18SkDvjm.WQwobn6eVQ%2BNOo%2FOtmocjGRm8HZcQxw9c2W9ncpa7RM' -v https://dashboard.everad.com/v2/profile/notifications
```
######success response
```
< HTTP/1.1 200 OK
{
  "offer_change":[
    "sms",
    "email"
  ],
  "new_offer":[
    "email"
  ],
  "new_thread":[
  "email"
  ],
  "new_thread_post":[
    "email"
  ],
  "promo":[
    "email"
  ],
  "digest":null,
  "payout_status_change":null
}
```
{% endmethod %}
{% method %}
###`PUT /profile/avatar`
Upload avatar (all cropping and resizing on client side).
{% sample lang="bash" %}
```bash
curl -X PUT -H 'Content-type: multipart/form-data' -F avatar=@/home/user/me.jpg -v https://dashboard.everad.com/v2/profile/avatar
```
######success response
```
< HTTP/1.1 200 OK
```
{% endmethod %}
{% method %}
###`GET /profile/contest-standings`
Get your current contest position.
{% sample lang="bash" %}
```bash
curl -X GET -b 'cpa_sid=s%3AZ7vljuUpdxc4dYVpKIaSkne_18SkDvjm.WQwobn6eVQ%2BNOo%2FOtmocjGRm8HZcQxw9c2W9ncpa7RM' -v https://dashboard.everad.com/v2/profile/contest-standings
```
######success response
```
< HTTP/1.1 200 OK
[{"email":"geor**********skiy@g***l.com","rank":"1","points":100500},"email":"Wil********y89@y***o.com","rank":"2","points":10050}]
```
{% endmethod %}