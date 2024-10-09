# 홈 화면

### API Endpoint
```sql
GET /users/home/{userId}
```

### Request Body
```
{
    "id" : "userId"
}
```

### Request Header
Authorization : accessToken (user)

### Query String
필요없음

### Path variable
{userId}


# 마이 페이지 리뷰 작성

### API Endpoint
```sql
POST /shops/reviews/upload
```

### Request Body
```
{
    "userName" : {userName}
    "content" : {content}
    "rating" : {rating}
    "shopId" : {shopId}
}
```

### Request Header
Authorization : accessToken (user)

### Query String
필요없음

### Path Variable
필요없음


# 미션 목록 조회(진행중, 진행완료)

### API EndPoint
GET /home/users/missions

### Request Body
필요없음

### Request Header
Authorization : accessToken (user)

### Query String
?userId=1234
&
?is_complete=true //진행완료
?is_complete=false //진행중

### Path Variable
필요없음


# 미션 성공 누르기

### API EndPoint

### Request Body

### Request Header

### Query String

### Path Variable


# 회원가입 하기

### API EndPoint

### Request Body

### Request Header

### Query String

### Path Variable