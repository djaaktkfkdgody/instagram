REST API Spec.
version 0.1 (2025/6/11)
사용자 계정
사용자 생성
Endpoint
POST /users
Request body
nickname (string): 사용자 nickname, 필수
name (string): 사용자 이름, 필수
password (string): 비밀번호, 필수
age (int, optional): 사용자 나이
email (string, optional): 사용자 email 주소
~~~
{
  "nickname": "kevin",
  "name": "이승학",
  "password": "1234",
  "email": "kevin.spreatics@gmail.com"
}
~~~

Description
사용자 계정을 생성한다. nickname과 name, password는 필수 입력값이다.
nickname은 고유한 값이며 기존 사용자와 중복되면 생성이 실패한다.
Response body
status (string): created, failed
user_id (int): 생성 성공 시, user_id 반환
reason (string): 실패 시, 실패 원인
~~~
{
  "status": "created",
  "user_id": 105
}

{
  "status": "failed",
  "reason": "nickname, kevin is duplicated"
}
~~~
사용자 삭제
Endpoint
DELETE /users/<user_id>
user_id (int): 삭제할 사용자 id
Request body
없음
Description
user_id에 해당하는 사용자 계정을 삭제한다.
user_id가 없으면 삭제가 실패한다.
Response body
status (string): deleted, failed
reason (string): 실패시, 실패 원인
~~~
{
  "status": "failed",
  "reason": "user_id, 101 doesn't exist"
}
~~~
