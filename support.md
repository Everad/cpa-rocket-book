#Support
Retrieve your communication with support.

##Endpoints
{% method %}
####`GET /threads`

Get a list of your threads.

{% sample lang="bash" %}
```bash
curl -X GET -v -b 'cpa_sid=s%3A7OKmdhfZr6qJ_H5OWLKJCRWfyoWAtm6q.yzfCuK0Flvj5xW8UlRES3JTyZNMGLhiTF8aPEZ3MFOo' 'https://dashboard.everad.com/v2/threads'
```
######success response
```
< HTTP/1.1 200 OK
[
  {
    "id": 1,
    "created_at": "2017-03-02 15:07:51",
    "updated_at": "2017-03-02 15:07:51",
    "status": "active",
    "category": "affiliate_question",
    "priority": "critical",
    "title": "умысел иллюстрирует продукт",
    "offer_title": null,
    "viewed": false,
    "total_posts": "2",
    "new_posts": "1"
  }
]
```
{% endmethod %}
{% method %}
###`GET /threads/:id`
Get posts within a thread by its id.
{% sample lang="bash" %}
```bash
curl -X GET -v -b 'cpa_sid=s%3A09OpKmlx3UY73RKvuKH1-KpaorJNxuwN.GMThTayHUQ0kjmztr4Gf4xIjrs%2FQcJXJAzTabTELFuM' 'https://dashboard.everad.com/v2/threads/2'
```
######success response
```
< HTTP/1.1 200 OK
{
  "id": 1,
  "created_at": "2017-03-02 15:07:51",
  "updated_at": "2017-03-02 15:07:51",
  "closed_at": null,
  "status": "active",
  "category": "affiliate_question",
  "priority": "critical",
  "title": "умысел иллюстрирует продукт",
  "offer_id": null,
  "admin_id": 1,
  "admin_viewed": true,
  "affiliate_viewed": false,
  "total_posts": "2",
  "new_posts": "1",
  "posts": [
    {
      "id": 1,
      "created_at": "2017-02-20 09:35:32",
      "updated_at": "2017-02-20 09:35:32",
      "text": "Пуанта нуждается определению артиста Представленный Веселых. Хотя среда рассматривать несостоятельно. В известно но устного медиавес. Гипноз экзистенциальный индуцирует.",
      "author": "affiliate",
      "name": "affiliate@example.com",
      "avatar": null,
      "attachments": [
        {
          "name": "Screenshot_2016-12-06_14-09-08.png",
          "path": "https://example.com/attachment/11_46e2d876-cb00-4e52-a2fd-8df902d752e9_Screenshot_2016-12-06_14-09-08.png"
        }
      ]
    },
    {
      "id": 2,
      "created_at": "2017-02-21 09:32:32",
      "updated_at": "2017-02-21 09:32:32",
      "text": "Осознаёт англо-саксонской институциональный штраф провоз. Преимущества известно перспективной Инвестиционный собак понимает своей. Продукт психолингвистическим в.",
      "author": "admin",
      "name": "Super support",
      "avatar": null,
      "attachments": null
    }
  ]
}
```
{% endmethod %}
{% method %}
###`POST /threads`
Create a thread.
{% sample lang="bash" %}
```bash
curl -X POST -v -H 'Content-type: application/json' -b 'cpa_sid=s%3A9RnpiJ4u9OE2WWFHGLG49jP01sTScNFq.WrmLKZAsFsVO1OkDvAaurzdeQnQMOeKOpvbZADY%2B5m8' -d '{"title":"i want offer access", "priority": "critical", "offer_id": 10, "category": "offer_access", "text": "please give me access to this order thanks"}' https://dashboard.everad.com/v2/threads
```
######success response
```
< HTTP/1.1 201 Created
{
  "id": 1,
  "created_at": "2017-03-02 15:07:51",
  "updated_at": "2017-03-02 15:07:51",
  "closed_at": null,
  "status": "active",
  "category": "offer_access",
  "priority": "critical",
  "title": "i want offer access",
  "offer_id": 10,
  "admin_id": 1,
  "admin_viewed": false,
  "affiliate_viewed": false,
  "total_posts": "1",
  "new_posts": "1",
  "posts": [
    {
      "id": 65,
      "admin_id": null,
      "affiliate_id": 11,
      "attachments": null,
      "created_at": "2017-05-18T07:42:36.805Z",
      "text": "please give me access to this order thanks",
      "thread_id": 1,
      "updated_at": "2017-05-18T07:42:36.805Z",
      "viewed_at": null
    }
  ]
}
```
{% endmethod %}
{% method %}
###`POST /threads/:id`
Create a post in a thread.
{% sample lang="bash" %}
```bash
curl -X POST -v -b 'cpa_sid=s%3AVvfflLue_6MkfHEN5S9N2tN9-z50Zdxf.ASQBDXkdlsoRIklt6ltLiEGGdr%2BtawqRF%2BhLX51apbg' 'https://dashboard.everad.com/v2/threads/15' -H 'Content-type: application/json' -d '{ "text": "post text here" }'
```
######success response
```
< HTTP/1.1 201 Created
{
  "id": 165,
  "admin_id": null,
  "affiliate_id": 11,
  "attachments": null,
  "created_at": "2017-05-18T07:42:36.805Z",
  "text": "post text here",
  "thread_id": 15,
  "updated_at": "2017-05-18T07:42:36.805Z",
  "viewed_at": null
}

```
{% endmethod %}
{% method %}
###`PUT /threads/:post-id/attachments`
Add attachments to thread post.
{% sample lang="bash" %}
```bash
curl -X PUT -v -b 'cpa_sid=s%3AVvfflLue_6MkfHEN5S9N2tN9-z50Zdxf.ASQBDXkdlsoRIklt6ltLiEGGdr%2BtawqRF%2BhLX51apbg' 'https://dashboard.everad.com/v2/threads/1040/attachments' -H 'Content-type: multipart/form-data' -F file1=@/home/user/me.jpg
```
######success response
```
< HTTP/1.1 200
```
{% endmethod %}
{% method %}
###`PUT /threads/:id/close`
Close a thread.
{% sample lang="bash" %}
```bash
curl -X PUT -v -b 'cpa_sid=s%3AVvfflLue_6MkfHEN5S9N2tN9-z50Zdxf.ASQBDXkdlsoRIklt6ltLiEGGdr%2BtawqRF%2BhLX51apbg' 'https://dashboard.everad.com/v2/threads/15/close'
```
######success response
```
< HTTP/1.1 201 Created

```

{% endmethod %}