#Master account
Manage your child accounts (when in master mode)
##Endpoints
{% method %}
####`GET /master-account/full`
Get list of all child affiliate accounts.
{% sample lang="bash" %}
```bash
curl -v -X GET -b 'cpa_sid=s%3AjqL-ubOG0LAvIsQf2cfHT9EnMvgkLtZH.B4LmgxlrTpnmmHD6VXxVdTbwIkWuZOQ2ZtK1%2FQnMKys' https://dashboard.rocketprofit.com/v2/master-account
```
######success response
```
< HTTP/1.1 200 OK
{"total":"3","rows":[{"id":100017,"email":"test@google.com","avatar":avatarurl.jpg,"nickname":"test","answered_poll_ids":[],"offer_ids":[1,3,5,4],"total_count":"3"},{"id":100016,"email":"asd@yandex.ru","avatar":"avatarurl.jpg","nickname":"lol","answered_poll_ids":[],"offer_ids":[1,3,5,4],"total_count":"3"},{"id":100014,"email":"myemail@yandex.ru","avatar":avatarurl.jpg,"nickname":"asd","answered_poll_ids":[],"offer_ids":[1,3,5,4],"total_count":"3"}]}
```
{% endmethod %}

