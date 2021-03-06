## HTTP Status Code (상태 코드)

### 2XX Success

2xx 번대의 상태 코드들은 서버가 클라이언트의 요청을 성공적으로 처리했다는 의미이다.

- #### 200 OK
  - 클라이언트의 요청을 서버가 정상적으로 처리했다.
  - 성공에 대한 모든 상태 코드를 200으로 응답해도 상관없지만 클라이언트에게 더 정확하고 자세한 정보를 제공하기 위해선 적절한 상태 코드를 보내는 것이 좋다.

- #### 201 Created
  - 클라이언트의 요청을 서버가 정상적으로 처리했고 새로운 리소스가 생겼다.
  - 201 상태 코드는 POST, PUT 요청에 대한 응답에 주로 사용된다.

- #### 202 Accepted
  - 클라이언트의 요청은 정상적이나, 서버가 아직 요청을 완료하지 못했다.
  - 클라이언트의 요청이 정상적이면 서버에선 작업의 성공/실패 응답하는 게 일반적인데, 작업 완료를 위한 일련의 작업들이 오래 걸리기 때문에 나중에 알려주겠다는 의미이다.
  - 202 상태 코드에서 중요한 것은 작업의 확인이다. 비동기 작업은 해당 요청이 언제 완료되는지 알 수 없다.
  - 클라이언트가 요청의 완료 여부를 확인할 수 있는 방법을 제공해야 한다.
  - #### Callback
    - 서버가 작업이 완료되면 클라이언트에게 알려주는 것이다.
  - #### Poling
    - 클라이언트가 주기적으로 해당 작업의 상태를 조회하는 것이다.

- #### 204 No Content
  - 클라이언트의 요청은 정상적이다. 하지만 컨텐츠를 제공하지 않는다.
  - 204 상태 코드는 자원의 삭제 요청에 응답할 수 있다.
  - 자원 삭제 요청을 했고 이 요청이 유효하니 서버는 해당 자원을 삭제했다. 더 이상 응답할 컨텐츠가 없기 때문에 컨텐츠가 없는 204로 응답한다.
  - 204는 200과 달리 HTTP Response body가 존재하지 않는다.

### 4XX Client Errors

4XX의 상태 코드들은 클라이언트의 요청이 유효하지 않아 서버가 해당 요청을 수행하지 않았다는 의미다.

- #### 400 Bad Request
  - 클라이언트의 요청이 유효하지 않아 더 이상 작업을 진행하지 않는 경우
  - API 서버는 클라이언트 요청이 들어오면 바로 작업을 진행하지 않고 **요청이 서버가 정의한 유효성에 맞는지 확인** 후 진행한다.
  - 대부분의 API는 사전에 유효성 검증을 통해 400 상태 코드로 클라이언트에게 유효하지 않은 요청임을 응답한다.
  - 오류 발생 시 **파라미터의 위치(path, query, body), 사용자 입력 값, 에러 이유를 꼭 명시**하는 것이 좋다.

```java
HTTP/1.1 400 Bad Request
{
"message" : "'name'(body) must be String, input 'name': 123"
}
```

- #### 401 UnAuthorized
  - 클라이언트가 권한이 없기 때문에 작업을 진행할 수 없는 경우
  - 상태 코드 이름만 보면 권한(authorized)에 대한 내용처럼 보이지만, 사실 **인증(authenticated)**에 대한 이야기다.
  - 결론적으로 401은 <mark>**인증이 안돼 자원을 이용할 수 없는 상태**</mark>고, 의미상 UnAuthenticated가 더 정확하다.

- #### 403 Forbidden
  - 클라이언트가 권한이 없기 때문에 작업을 진행할 수 없는 경우
  - 403은 권한(authorized)에 대한 내용이다.
  - <mark>**인증된 클라이언트가 권한이 없는 자원에 접근할 때**</mark> 응답하는 상태 코드다.

- #### 404 NotFound
  - 클라이언트가 요청한 자원이 존재하지 않다.
  - REST API에선 크게 두 가지 경우에서 404 상태 코드를 응답한다.
    - **경로가 존재하지 않음**
    - **자원이 존재하지 않음**

``` 
PUT /users/1 경우 /users/:id로 존재하는 경로다.
이 때 서버는 ID 1을 갖는 사용자가 있는지 먼저 확인을 해야 한다.
만약, 존재 여부를 파악하지 않고 그대로 진행을 하면 후속 작업에서 오류가 발생할 가능성이 있고 이것은 5XX 오류로 이어질 수 있다.
즉, 존재하는 경로에 대한 요청이라도 자원이 존재하는지 파악 후, 존재하지 않는다면 404 상태 코드로 응답해야 한다.
```

- #### 405 Method Not ALlowed
  - 클라이언트의 요청이 허용되지 않는 메소드인 경우
  - 메소드란 POST, GET, PUT, DELTE 등 HTTP Method를 말한다.
  - 즉, **자원(URI)은 존재하지만 해당 자원이 지원하지 않는 메소드일 때** 응답하는 상태 코드다.
  - 405 상태 코드는 OPTIONS 메소드와 HTTP header의 Allow와 연관되어있다.
    - OPTIONS는 API가 허용하는 메소드가 어떤 것들이 있는지 확인하는 메소드다.
    - 405오류를 사전에 방지하기 위한 용도에 주로 쓰인다.
    - 이 때 응답 HTTP header의 Allow에 지원하는 메소드를 나열하여 응답한다.
  
```java
HTTP/1.1 200 OK
Allow: GET,PUT,DELETE,OPTIONS,HEAD
```

- #### 404 vs 405
  - 405 상태 코드는 404 상태 코드와 혼동될 수 있기 때문에 규칙을 잘 정해야 한다.
  - ex) /users/:id 는 GET, PATCH, DELETE 메소드는 허용되고 POST은 불가한 URI이다.
  - POST /users/1의 경우 API 설계에 따라 404, 405로 응답할 수 있다.
  - GET, PATCH, DELETE의 경우, 1 사용자가 없는 경우엔 404로 응답한다.
  - POST 요청의 경우 제공하지 않는 메소드기 때문에 405로 응답하는 것이 옳다.

- #### 409 Conflict
  - 클라이언트의 요청이 서버의 상태와 충돌이 발생한 경우
  - 400, 401, 403, 404, 405 상태 코드에 속하기 애매한 오류의 상황들을 409로 응답한다.

ex) 해당 요청의 처리 중 비지니스 로직상 불가능하거나 모순이 생겨서 처리가 불가능한 경우

```java
DELETE /users/1 HTTP/1.1
X-TOKEN: password
```
- 자원(URI) /users/1에 존재하는 메소드고 Not 405
- /users/:id에서 :id가 유효한 형식이고 Not 400
- 1 사용자도 존재하고 Not 404
- 헤더의 인증(X-TOKEN)도 정확하고 Not 401
- 삭제 권한도 있는 경우 Not 403
- 클라이언트의 삭제 요청은 받아들여져서 200 혹은 204로 응답해야 하지만, 사용자의 게시물이 존재하는 경우 사용자를 삭제할 수 없다는 비지니스 로직이 있으면 409 Conflict를 응답한다.

- #### Too Many Requests
  - 클라이언트가 일정 시간 동안 너무 많은 요청을 보낸 경우
  - 비정상적인(DoS attack, Brute-force attack) 방법으로 자원을 요청하는 경우 응답한다.
  - 429 상태 코드는 이러한 경우 일정 시간 뒤 요청할 것을 나타내는 것이다.
  - 따라서 다음과 같이 HTTP hearder Retry-After을 이용한다.
```java
HTTP/1.1 429 Too Many Requests
Retry-After: 3600
```
- 클라이언트는 3600초 후에 다시 해당 자원에 대한 작업을 요청할 수 있다.

### 5XX Server Errors   
  - 5XX 상태 코드들은 서버 오류로 인해 요청을 수행할 수 없다는 의미다.
  - 클라이언트의 요청은 유효하여 작업을 진행했는데 도중에 오류가 발생한 경우다.
  - API 서버의 응답에서 5XX 오류가 발생해서는 안된다.
  - 보통 개발 과정에서 유효하지 않은 요청을 사전에 처리하지 않은 경우(400)에 많이 발생한다.