Kiple API
=============

! Do not use Tab. Instead use spaces.

* [Data Type](#data-type)
* [User](#user)
    * [Login](#login)
    * [User Data](#user-data)
    * [Modify User Data](#modify-user-data)
    * [Basket](#basket)
    * [Pick](#pick)
    * [Check Order](#check-order)
    * [Cloth History](#cloth-history)
    * [FAQ](#faq)
    * [Help](#help)
* [Shop](#shop)
    * [Cloth List](#cloth-list)
    * [Cloth](#cloth)
    * [Special List](#special-list)
    * [Special](#special)
* [Community](#community)
    * [Stream List](#stream-list)
    * [Stream](#stream)


Data Type
-------------

**Date**: String. ISO 8601

**Color**: String as Hexa format

> * "none"
> * "#010101"
> * "#808080"
> * "#c0c0c0"
> * "#ffffff"
> * "#0000ff"
> * "#000080"
> * "#87ceeb"
> * "#99cc32"
> * "#008000"
> * "#ffa500"
> * "#ffc0cb"
> * "#ee82ee"
> * "#800080"
> * "#ff0000"
> * "#8b4513"
> * "#ffff00"
> * "#f0e68c"
>
> 위의 컬러표는 현재 키플에서 사용하는 컬러표인듯하다.
> 정확한 컬러표는 나중에 결정하는게 좋을 듯하다.

**Shoptype**: TODO

**Category**: Int. Sub category takes two more digits to represent the category.
> example 
> * 0000: 티셔츠
> * 0100: 긴팔
> * 0200: 반팔
> * 0001: 바지
> * 0101: 긴바지
> * 0201: 반바지
> * 0002: 남방/블라우스
> * 0102: 긴팔
> * 0202: 반팔
> * 0003: 스커트
> * 0004: 원피스
> * 0005: 정장/드레스
> * 0006: 스웨터/조끼/가디건
> * 0007: 자켓/점퍼/코트
> * 0008: 내의
> * 0009: 신생아의류
> * 0010: 수영복
> * 0011: 한복 
> * 0012: 스키복
> * 0013: 기타
> * 0014: 가방
> * 0015: 신발 
> * 0016: 기타
> * 0017: 도서/DVD





> * etc...
> 정확한 카테고리는 나중에 결정하는게 좋을 듯 하다.

**Gender**: Int
> * 0: 남아
> * 1: 여아
> * 2: 공용


User
----

### Login

사용자 로그인

```
URL:
Method: POST
Accept: application/json
Content-Type: application/json

Request:
{ "username" : string, "password" : string }

Response:
{ "login-success" : boolean }
```

### User Data
사용자 정보 갖어오기

```
TODO
```

### Modify User Data

```
TODO
```

### Basket

장바구니 보기

```
URL:
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
URL:
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

```
TODO
```

### Cloth History

옷 보내기 히스토리

```
URL:
Method: GET
Accept: application/json
Content-Type: application/json

Request:
{ }

FIXME 아직 좀더 알아봐야 함
Response:
{ "items" : 
    [ { "id" : string, 
        "name" : string, 
        "quantity" : int,
        "send-date" : date,
        "state" : string } 
    ] 
}
```

### FAQ

도움말

```
TODO
```

### Help

1:1 문의하기

```
TODO
```

Shop
----

### Cloth List

검색 또는 옷장에서 옷 리스트를 받아온다.

```
URL: 
Method: GET
Accept: application/json
Content-Type: application/json

Request:
{ "gender" : gender,
  "age" : int,
  "category" : category,
  "color" : color,
  "shop-type" : shoptype,
  "season" : [ string ] // ex) [ "봄", "여름", "가을" ]
}
// 데이터가 없으면 전체를 보여준다.
// ex) 나이 데이터가 들어있지 않으면 모든 나이대의 데이터를 response한다.
// ex) 아무 데이터가 들어있지 않으면 전체 데이터를 response한다.

Response:
{ "items" : 
    [ { "id" : string, 
        "name" : string, 
        "price" : int,
        "age" : string,
        "image-url" : string } 
    ] 
}
```

### Cloth

옷 id를 이용하여 특정 옷의 정보를 갖어온다.

```
URL:
Method: GET
Accept: application/json
Content-Type: application/json

Request:
{ "id" : string  }

Response:
{  "id" : string, 
   "name" : string, 
   "content" : string, // 자세한 정보 부분. ex) 이 옷에는 얼룩이 약간 묻어 있습니다.
   "price" : int,
   "available-kiplemoney" : int, // 키플머니 사용 가능액
   "age" : string,
   "size" : string,
   "season" : [ string ], // ex) [ "봄", "여름", "가을" ]
   "item" : string, // ex) 바지(긴바지), - , (상태 - 중)
   "color" : color,
   "image-urls" : [ { "url" : string } ]
} 
```

### Special List

```
TODO
```

### Special

// Special id를 이용하여 특정 Special의 옷 리스트를 갖어온다.

```
URL:
Method: GET
Accept: application/json
Content-Type: application/json

Request:
{ "id" : string }

Response:
{ "items" : 
    [ { "id" : string, 
        "name" : string, 
        "price" : int,
        "age" : string,
        "image-url" : string } 
    ] 
}
```

Community
---------

### Stream List

```
URL:
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
URL:
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
