# Everad CPA v2 Dashboard API

This describes the **API** for managing your affiliate account inside **Everad CPA** application.

API operates on **REST** principles with some deviations described explicitly in method's description.

All incoming data is passed in **JSON** format \(with specified `Content-type: application/json` header)

#### Response usable data:

**HTTP Status Code** indicates whether your request was successfully processed \(`200`, `201` codes\) or ended with error \(`400` - bad input data, `403` - you don't have a permission to access the requested endpoint, `500` - internal server error, contact support\).

**Response Body** contains requested data or error info \(for `400` status codes\).

#### Base url

`https://dashboard.everad.com/v2`

#### Methods available:

`/lists` - fetch available data enums, used in other endpoints.

`/session` - manage your current session and permissions to access internal methods.

`/profile` - manage profile data \(contacts, payments, language info\).

`/finances` - manage your finances (daily transactions, payouts).

`/news` - fetch current news.

`/offers` - fetch available offers, manage your current offer permissions.

`/spaces` - manage your personal spaces for grouping your incoming traffic.

`/campaigns` - manage your campaigns.

`/support` - manage your support requests.

`/analytics` - get your traffic and financial statistics

`/lookups` - lookup for data by partial name

`/master-account` - manage your children account preferences (if your account is in `master` mode)

`/oauth` - authorize third-party systems with password grant oauth2 mechanism



