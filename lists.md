#Lists
Endpoints for receiving different lists, used by other parts of API. 

Use `?lang=ru` or `?lang=en` query parameters in the URL to explicitly request localized versions of lists. English is set by default unless your browser language or your user profile language are supported by the API.
##Endpoints
{% method %}
###`GET /lists`
Use this endpoint to get all non-persionalized lists with one request
{% sample lang="bash" %}
```bash
curl -X GET -v https://dashboard.everad.com/v2/lists/
```
######success response
```
< HTTP/1.1 200 OK
{"adv-systems":[{"id":"other","text":"Other"},{"id":"target_mail","text":"MyTarget"}],"available-currencies":[{"id":"usd","text":"usd"},{"id":"rub","text":"rub"}]}
```
{% endmethod %}
{% method %}
###`GET /lists/languages`
Retrieve available response languages.
{% sample lang="bash" %}
```bash
curl -X GET -v https://dashboard.everad.com/v2/lists/languages
```
######success response
```
< HTTP/1.1 200 OK
[{"id":"en","text":"English"},{"id":"ru","text":"Russian"}]
```
{% endmethod %}
{% method %}
###`GET /lists/space-types`
Retrieve possible space types.
{% sample lang="bash" %}
```bash
curl -X GET -v https://dashboard.everad.com/v2/lists/space-types
```
######success response
```
< HTTP/1.1 200 OK
[{"id":"site","text":"site"},{"id":"context","text":"context"},{"id":"social","text":"social"},{"id":"doorway","text":"doorway"},{"id":"email","text":"email"},{"id":"arbitrage","text":"arbitrage"}]
```
{% endmethod %}
{% method %}
###`GET /lists/offer-categories`
Retrieve possible offer categories.
{% sample lang="bash" %}
```bash
curl -X GET -v https://dashboard.everad.com/v2/lists/offer-categories
```
######success response
```
< HTTP/1.1 200 OK
[{"id":"slimming","text":"slimming"},{"id":"cosmetics","text":"cosmetics"},{"id":"adult","text":"adult"},{"id":"medical","text":"medical"},{"id":"auto","text":"auto"},{"id":"other","text":"other"}]
```
{% endmethod %}
{% method %}
###`GET /lists/currencies`
Retrieve all currencies.
{% sample lang="bash" %}
```bash
curl -X GET -v https://dashboard.everad.com/v2/lists/currencies
```
######success response
```
< HTTP/1.1 200 OK
[{"id":"usd","text":"usd"},{"id":"rub","text":"rub"},{"id":"byn","text":"byn"},{"id":"kgs","text":"kgs"},{"id":"kzt","text":"kzt"},{"id":"mdl","text":"mdl"},{"id":"azn","text":"azn"},{"id":"gel","text":"gel"},{"id":"uah","text":"uah"},{"id":"ron","text":"ron"},{"id":"thb","text":"thb"},{"id":"amd","text":"amd"}]
```
{% endmethod %}
{% method %}
###`GET /lists/available-currencies`
Retrieve available currencies.
{% sample lang="bash" %}
```bash
curl -X GET -v https://dashboard.everad.com/v2/lists/available-currencies
```
######success response
```
< HTTP/1.1 200 OK
[{"id":"usd","text":"usd"},{"id":"rub","text":"rub"}]
```
{% endmethod %}
{% method %}
###`GET /lists/campaign-domains` - available only for active session
`adv_system` - one of `/lists/adv-systems`
{% sample lang="bash" %}
```bash
curl -X GET -b 'connect.sid=s%3AWt1ZtB7mMKQCcTAVs7_iPVQ5-EU6o_0Q.0aMir6l0Raw%2BCJrZYPoAWQM1ATFWhUX2VxgYL%2FuqEy0' -v https://dashboard.everad.com/v2/lists/campaign-domains?adv_system=other
```
######success response
```
< HTTP/1.1 200 OK
[{"id":1,"text":"example.com"},{"id":2,"text":"example2.com"}]
```
{% endmethod %}
{% method %}
###`GET /lists/offer-domain-types`
Retrieve possible offer domain types.
{% sample lang="bash" %}
```bash
curl -X GET -v https://dashboard.everad.com/v2/lists/offer-domain-types
```
######success response
```
< HTTP/1.1 200 OK
[{"id":"landing","text":"landing"},{"id":"transit","text":"transit"}]
```
{% endmethod %}
{% method %}
###`GET /lists/timezones`
Retrieve possible system timezones.
{% sample lang="bash" %}
```bash
curl -X GET -v https://dashboard.everad.com/v2/lists/timezones
```
######success response
```
< HTTP/1.1 200 OK
[{"id":"Europe/Moscow","text":"Europe/Moscow"},{"id":"Europe/Minsk","text":"Europe/Minsk"}]
```
{% endmethod %}
{% method %}
###`GET /lists/traffic-types`
Retrieve possible system traffic types.
{% sample lang="bash" %}
```bash
curl -X GET -v https://dashboard.everad.com/v2/lists/traffic-types?lang=ru
```
######success response
```
< HTTP/1.1 200 OK
[{"id":"desktop","text":"компьютер"},{"id":"tablet","text":"планшет"},{"id":"phone","text":"смартфон"},{"id":"bot","text":"бот"},{"id":"tv","text":"телевизор"}]
```
{% endmethod %}
{% method %}
###`GET /lists/traffic-sources`
Retrieve possible system traffic sources.
{% sample lang="bash" %}
```bash
curl -X GET -v https://dashboard.everad.com/v2/lists/traffic-sources?lang=ru
```
######success response
```
< HTTP/1.1 200 OK
[{"id":"general","text":"общий / не определен"},{"id":"social","text":"социальный"},{"id":"teasers","text":"тизерный"}]
```
{% endmethod %}
{% method %}
###`GET /lists/campaign-types`
Retrieve possible system campaign types.
{% sample lang="bash" %}
```bash
curl -X GET -v https://dashboard.everad.com/v2/lists/campaign-types?lang=ru
```
######success response
```
< HTTP/1.1 200 OK
[{"id":"general","text":"общий"},{"id":"novostnik","text":"с новостника"},{"id":"parked_novostnik","text":"с паркованного новостника"}]
```
{% endmethod %}

{% method %}
###`GET /lists/news-types`
Retrieve possible news types.
{% sample lang="bash" %}
```bash
curl -X GET -v https://dashboard.everad.com/v2/lists/news-types?lang=ru
```
######success response
```
< HTTP/1.1 200 OK
[{"id":"new_offer","text":"новинки"},{"id":"offer_stop","text":"приостановка офферов"},{"id":"offer_change","text":"изменение офферов"},{"id":"geo_change","text":"расширение гео"},{"id":"new_landing","text":"новые лэндинги"},{"id":"custom","text":"системные тикеты"}]
```
{% endmethod %}
{% method %}
###`GET /lists/payout-statuses`
Retrieve possible payout statuses.
{% sample lang="bash" %}
```bash
curl -X GET -v https://dashboard.everad.com/v2/lists/payout-statuses?lang=ru
```
######success response
```
< HTTP/1.1 200 OK
[{"id":"pending","text":"в обработке"},{"id":"approved","text":"проверена"},{"id":"confirmed","text":"подтверждена"},{"id":"paid","text":"оплачена"},{"id":"rejected","text":"отклонена"}]
```
{% endmethod %}
{% method %}
###`GET /lists/thread-statuses`
Retrieve possible support thread statuses.
{% sample lang="bash" %}
```bash
curl -X GET -v https://dashboard.everad.com/v2/lists/thread-statuses?lang=ru
```
######success response
```
< HTTP/1.1 200 OK
[{"id":"active","text":"активный"},{"id":"closed","text":"закрытый"}]
```
{% endmethod %}
{% method %}
###`GET /lists/thread-priorities`
Retrieve possible support thread priorities.
{% sample lang="bash" %}
```bash
curl -X GET -v https://dashboard.everad.com/v2/lists/thread-priorities?lang=ru
```
######success response
```
< HTTP/1.1 200 OK
[{"id":"normal","text":"обычный"},
{"id":"high","text":"высокий"},{"id":"critical","text":"критический"}]
```
{% endmethod %}
{% method %}
###`GET /lists/thread-categories`
Retrieve possible support thread categories.
{% sample lang="bash" %}
```bash
curl -X GET -v https://dashboard.everad.com/v2/lists/thread-categories?lang=ru
```
######success response
```
< HTTP/1.1 200 OK
[{"id":"affiliate_question","text":"вопросы вебов"},{"id":"offer_access","text":"доступ к офферу"},{"id":"admin_ticket","text":"тикет от администрации"},{"id":"new_landing_transit","text":"добавление лендингов/транзитов"}]
```
{% endmethod %}
{% method %}
###`GET /lists/payout-credential-fields`
Retrieve possible payout credential fields.
{% sample lang="bash" %}
```bash
curl -X GET -v https://dashboard.everad.com/v2/lists/payout-credential-fields?lang=ru
```
######success response
```
< HTTP/1.1 200 OK
[{"id":"purse","text":"кошелек"},{"id":"account","text":"счет"},{"id":"card","text":"карта"}]
```
{% endmethod %}
{% method %}
###`GET /lists/campaign-domain-types`
Retrieve possible domain types to be used in campaign creation/editing.
{% sample lang="bash" %}
```bash
curl -X GET -v https://dashboard.everad.com/v2/lists/campaign-domain-types
```
######success response
```
< HTTP/1.1 200 OK
[{"id":"internal","text":"internal"},{"id":"external","text":"external"}]
```
{% endmethod %}
{% method %}
###`GET /lists/adv-systems`
Retrieve possible advertising systems to be used in campaign creation/editing.
{% sample lang="bash" %}
```bash
curl -X GET -v https://dashboard.everad.com/v2/lists/campaign-domain-types
```
######success response
```
< HTTP/1.1 200 OK
[{"id":"other","text":"Other"},{"id":"target_mail","text":"MyTarget"}]
```
{% endmethod %}
{% method %}
###`GET /lists/notification-transports`
Retrieve possible advertising systems to be used in campaign creation/editing.
{% sample lang="bash" %}
```bash
curl -X GET -v https://dashboard.everad.com/v2/lists/campaign-domain-types
```
######success response
```
< HTTP/1.1 200 OK
[{"id":"email","text":"email"},{"id":"sms","text":"sms"},{"id":"push","text":"push"}]
```
{% endmethod %}
{% method %}
###`GET /lists/landings-snippets`
Get landings snippets list to be used in campaign creation/editing. Available for active session only.
{% sample lang="bash" %}
```bash
curl -X GET -v -b 'cpa_sid=s%3AWt1ZtB7mMKQCcTAVs7_iPVQ5-EU6o_0Q.0aMir6l0Raw%2BCJrZYPoAWQM1ATFWhUX2VxgYL%2FuqEy0' https://dashboard.everad.com/v2/lists/landings-snippets
```
######success response
```
< HTTP/1.1 200 OK
[{"id":"email","text":"email"},{"id":"sms","text":"sms"},{"id":"push","text":"push"}]
```
{% endmethod %}
{% method %}
###`GET /lists/contest-top`
Retrieve top 100 contest users.
{% sample lang="bash" %}
```bash
curl -X GET -v https://dashboard.everad.com/v2/lists/contest-top
```
######success response
```
< HTTP/1.1 200 OK
[{"email":"geor**********skiy@g***l.com","rank":"1"},"email":"Wil********y89@y***o.com","rank":"2"}]
```
{% endmethod %}