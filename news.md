#News
Get available news.
##Endpoints
{% method %}
####`GET /news`

Get **last** 100 available news (use `offset` to get earlier news).
Use `types` query string param - one of `lists/news-types` - to select news by category and `search` param to search relevant news. Use `date_range` param to select news between needed dates. Use `offer_ids` param to filter by offers.

{% sample lang="bash" %}
```bash
curl -X GET -g -v -b 'cpa_sid=s%3AadtIeCZXVwjWFcGnsmw-BS3IVX6uhggo.a%2BvVlFq1keQhw%2F6Jlpjf4TeS%2BmTzfpbLjoM1RoDdDkc' 'https://dashboard.everad.com/v2/news?types[]=new_offer&types[]=offer_stop&offset=100&search=test'
```
######success response
```
< HTTP/1.1 200 OK
[
  {
    "published_at": "2017-03-01 09:42:26",
    "title": "test quos qui",
    "text": "Atque quia officia. Error et vel quae. Est temporibus libero nemo doloremque non consequuntur voluptates. Porro esse ipsum. Voluptatem vitae facilis est beatae corporis veniam. Voluptatem quia maiores omnis aut.\n \rQuia molestiae aut doloribus veritatis dolorem error porro sed reiciendis. Sit quae inventore voluptatem autem et incidunt et iure. Velit at et eius a impedit quam. Placeat minus officia possimus laborum maiores et alias consectetur maxime.\n \rQuos aut eos dolorem. Aliquam doloremque distinctio id libero explicabo consequatur ipsum vitae doloremque. Corporis possimus aut officiis. Quisquam omnis consequatur accusantium. Ea deserunt voluptatibus reiciendis aliquam commodi est fugiat. Voluptas repudiandae corrupti unde optio esse.",
    "type": "new_offer"
  }
]
```
{% endmethod %}
{% method %}
####`GET /news/<id>`

Get news entry by id.

{% sample lang="bash" %}
```bash
curl -X GET -g -v -b 'cpa_sid=s%3AadtIeCZXVwjWFcGnsmw-BS3IVX6uhggo.a%2BvVlFq1keQhw%2F6Jlpjf4TeS%2BmTzfpbLjoM1RoDdDkc' 'https://dashboard.everad.com/v2/news/1'
```
######success response
```
< HTTP/1.1 200 OK
{"published_at":"2017-03-24 16:07:23","title":"Расширение гео на оффере Микроэмульсия Нано-ботокс от морщин на Узбекистан","text":"<div>Уважаемые партнеры, рады сообщить о расширении гео на оффере <a href=\"https://everad.ru/dashboard#offer/317\">Микроэмульсия Нано-ботокс от морщин</a> на Узбекистан.</div><div>Выплата за подтвержденный заказ составляет 250 рублей.</div>","type":"custom","news_offers":[{"id":431,"title":"Микроэмульсия Нано-ботокс от морщин","image":"https://everad-attachments.s3.amazonaws.com/production/6813-1vtt2r4.png","cr":0.75,"epc":4.86,"currency":"rub","min_payout":100,"max_payout":105}]}
```
{% endmethod %}