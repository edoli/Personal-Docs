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

**Shoptype**: 필요없어!

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

**Gender**: Int
> * 0: 남아
> * 1: 여아
> * 2: 공용


User
----

### Login

사용자 로그인. apikey는 "kiple_mobile"로 하도록 하자.

```
URL: /api/login/
Method: POST
Accept: application/json
Content-Type: application/json

Request:
{ "username" : string, "password" : string, "apikey" : string }

Response:
{ "login-success" : boolean }
```

### Logout

사용자 로그아웃

```
URL: /api/logout/
Method: POST
Accept: application/json
Content-Type: application/json

Request:
{}

Response:
{ "logout-success" : boolean }
```

### Signup

회원가입

```
URL: /api/signup/
Method: POST
Accept: application/json
Content-Type: application/json

Request:
{ "name" : string ,
  "email" : string,
  "password" : string,
  "house-phone-number" : string,
  "cell-phone-number" : string,
  "address" : string,
  "detail-address": string,
  "children" : [ Child ] 
  }

Response:
{ "signup-success" : boolean }
```

### User Data
사용자 정보 갖어오기

```
URL: /api/user_data/
Method: GET
Accept: application/json
Content-Type: application/json

Request:
{ }

Response:
{ "id" : int,
  "name" : string,
  "email" : string,
  "house-phone-number" : string,
  "cell-phone-number" : string,
  "address" : string,
  "kiple-point" : int,
  "children" :
    [ { "id" : int,
        "gender" : gender,
        "birthday" : date }
    ]
 }
```

### Modify User Data

```
URL: 
Method: POST
Accept: application/json
Content-Type: application/json

Request:
{ "name" : string,
  "email" : string,
  "house-phone-number" : string,
  "cell-phone-number" : string,
  "address" : string }

Response:
{ "success" : boolean }
```

### Add Child

```
URL: 
Method: POST
Accept: application/json
Content-Type: application/json

Request:
{ "gender" : gender
  "birthday" : date }

Response:
{ "success" : boolean }
```

### Remove Child

```
URL:
Method: POST
Accept: application/json
Content-Type: application/json

Request:
{ "id" : int }

Response:
{ "success" : boolean }
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
    [ { "id" : int, 
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
    [ { "id" : int, 
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
    [ { "id" : int, 
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
그냥 앱 안에 하드코딩하는게 편하겠다
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
URL: /api/cloth_list/
Method: GET0
Accept: application/json
Content-Type: application/json

Request:
{ "id" : int
  "gender" : int,
  "age" : int,
  "category" : category,
  "color" : color,
  "seasons" : [ string ] // ex) [ "봄", "여름", "가을" ],
  "page" : int
}
// 데이터가 없으면 전체를 보여준다.
// ex) 나이 데이터가 들어있지 않으면 모든 나이대의 데이터를 response한다.
// ex) 아무 데이터가 들어있지 않으면 전체 데이터를 response한다.

Response:
{ "items" : 
    [ { "id" : int, 
        "name" : string, 
        "price" : int,
        "max-age" : int,
        "min-age" : int,
        "gender" : int,
        "image-url" : string } 
    ] 
}
```

### Item

아이템의 id를 이용하여 특정 옷의 정보를 갖어온다.

```
URL: /cloth/
Method: GET
Accept: application/json
Content-Type: application/json

Request:
{ "id" : int  }

Response:
{  "id" : int, 
   "name" : string, 
   "content" : string, // 자세한 정보 부분. ex) 이 옷에는 얼룩이 약간 묻어 있습니다.
   "price" : int,
   "gender" : int,
   "max-kpt" : int, // 키플머니 사용 가능액
   "max-age" : int,
   "min-age" : int,
   "seasons" : [ string ], // ex) [ "봄", "여름", "가을" ]
   "category" : string, 
   "", 왜이렇게 state들을 나눠놨어
   "color" : color,
  "discount-rate": int,
   "image-urls" : [ string ]
} 
```

### Special List

```
URL: 
Method: GET
Accept: application/json
Content-Type: application/json

Request:
{ }

Response:
{ "items" : 
    [ { "id" : int, 
        "name" : string, 
        "image-url" : string } 
    ] 
}
```

### Special

// Special id를 이용하여 특정 Special의 아이템 리스트를 갖어온다.

```
URL: 
Method: GET
Accept: application/json
Content-Type: application/json

Request:
{ "id" : int }

Response:
{ "items" : 
    [ { "id" : int, 
        "name" : string, 
        "price" : int,
        "image-url" : string } 
    ] 
}
```

Community
---------

### Stream List

```
URL: /api/stream_list/
Method: GET
Accept: application/json
Content-Type: application/json

Request:
{  }

Response:
{ "items" : 
    [ { "id" : int, 
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
{  "id" : int, 
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

### Write Stream

```
URL:
Method: Post
Accept: application/json
Content-Type: application/json

Request:
{ "content" : string,
  "date" : date,
  "image" : buffer }

Response:
{  "success" : boolean }
```
