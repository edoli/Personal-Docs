Kiple API
=============

! Do not use Tab. Instead use spaces.

Data Type
-------------
* Date: ISO 8601


User
----

### Login
사용자 로그인

```
Method: POST
Accept: application/json
Content-Type: application/json

Request:
{ "username" : string, "password" : string, "apikey" : string }
Response:
{ "login-success" : boolean }
```

### User Data
사용자 정보 갖어오기

TODO

### Modify User Data

TODO

### Basket
장바구니 보기

```
Method: GET
Accept: application/json
Content-Type: application/json

Request:
{  }
Response:
{ "items" : 
    [ { "id" : string, 
        "name" : string, 
        "price" : int, 
        "image-url" : string } 
    ] 
}
```

### Pick
찜 옷장 보기

```
Method: GET
Accept: application/json
Content-Type: application/json

Request:
{  }
Response:
{ "items" : 
    [ { "id" : string, 
        "name" : string, 
        "price" : int, 
        "image-url" : string } 
    ] 
}
```

### Check Order
주문 확인하기

TODO

### Cloth History
옷 보내기 히스토리

TODO

### FAQ
도움말
TODO

### Help
1:1 문의하기
TODO

Shop
----

### Cloth

TODO

### Cloth List

TODO

### Special

TODO

### Special List

TODO

Community
---------

### Stream List

```
Method: GET
Accept: application/json
Content-Type: application/json

Request:
{  }
Response:
{ "items" : 
    [ { "id" : string, 
        "name" : string, 
        "content" : string,
        "date" : date,
        "like-number" : int,
        "comment-number": int,
        "image-url" : string } 
    ] 
}
```

### Stream

```
Method: GET
Accept: application/json
Content-Type: application/json

Request:
{ "id" : string  }
Response:
{  "id" : string, 
   "name" : string, 
   "content" : string,
   "date" : date,
   "like-number" : int,
   "image-url" : string,
   "comments": [ { "userid" : string
                             "username" : string
                             "content" : string
                             "date" : date }
                         ] 
} 
```