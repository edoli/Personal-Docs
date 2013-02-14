Kiple API
=============

User
----

### Login
```
method: POST
Accept: application/json
Content-Type: application/json

Request:
{ "username": string, "password": string, "apikey": string }
Response:
{ "userid": string, "token": string }
(아니면 쿠키를 보내줘서 세션유지를 하던가
```