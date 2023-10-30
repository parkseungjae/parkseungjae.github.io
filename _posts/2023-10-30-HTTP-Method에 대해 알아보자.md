---
title: "HTTP Method에 대해 알아보자"
excerpt: "HTTP Method란?"

date: 2023-10-30
last_modified_at: 2023-10-30

toc: true
toc_sticky: true

categories:
    - 인터넷
tags:
    - Internet
    - HTTP
---

# 1. HTTP Method란?

**HTTP Method**란.
클라이언트 - 서버구조에서 **Request**와 **Response**가 이루어진는 방식을 의미한다.

**HTTP를 사용하는 이유는?**<br>
리소스와 동작을 분리하기 위함.<br>
HTTP Method를 통해 서버가 수행할 동작을 지정하면, URI는 리소스만 식별하면 되기 때문.

# 2. HTTP Method의 종류

**HTTP Method**의 종류는 8가지가 있으며, 다음과 같다.

  **GET** : 리소스 조회<br>
  **POST** : 데이터 추가,등록<br>
  **PUT** : 리소스 대체, 수정 / 해당 리소스 없을시 신규 생성<br>
  **DELETE** : 리소스 삭제<br>
  **PATCH** : 리소스 수정<br>
  **HEAD** : GET과 동일하지만, HTTP 메세지의 body 제외한 부분 조회<br>
  **OPTIONS** : 서버와 브라우저가 통신하기 위한 통신옵션 확인<br>
    서버가 어떤 method, header, content-type을 제공하는지 확인 불가.<br>
  **CONNECT** : 대상 자원으로 식별되는 서버에 대한 연결 요청<br>

## 2-1. GET Method
  리소스를 조회하는 메서드. (ex. URL 입력, 링크 클릭)<br>
  GET 요청은 **멱등성**(연산을 여러번 적용하더라도 결과가 달라지지 않는 성질) 이라는 개념을 지님,<br> 
  그래서 여러번 조회 하여도 리소스는 바뀌지 않는다.<br>
  GET 요청으로 서버에 데이터를 전달하면, **쿼리스트링**(url 주소에 미리 협의된 데이터를 파라미터를 통해 넘기는 것)을 통해 전달.<br>
  이 경우, 쿼리스트링은 클라이언트에게 전달하는 데이터정보가 노출되며, 브라우저 히스토리에도 기록이 남는다.

## 2-2. POST Method
  주로 신규 리소스를 생성시 사용한다.<br>
  성공적으로 생성할 경우 **201** HTTP 응답을 반환.<br>
  데이터를 메세지 바디에 쿼리 파라미터 형식으로 전달한다.<br>
    이때 쿼리 파라미터는 **Key-Value** 형식으로 되어있다. <br>(ex. Conetent-Type: application/json Content-Length : 100)<br>
    이는 GET과는 달리 클라이언트에게 전달하는 데이터정보가 노출되지 않는다.<br>
  POST로도 조회가 가능은 하지만, GET Method 와는 달리 멱등성을 지니지 않아 POST Method를 여러번 수행할 경우 같은 값이 나오는걸 보장해주진 않는다.<br>
  그리고 GET Method는 캐싱을 이용하기 때문에, 조회 속도 또한 POST Method에 비해 우수하다.<br>
  데이터를 전송할 때, Body에 담아 전송하기 때문에 길이의 제한이 없다.<br>
  문자열 뿐 아니라, 객체의 값도 전달이 가능하다.<br>

## 2-3. PUT Method
  리소스를 완전 대체(덮어쓰기)
  클라이언트가 리소스를 식별 가능.
  클라이언트가 구체적인 리소스 위치를 아는 상태에서, URI를 지정
  부분수정이 불가능하다.
  기존 (데이터 A,B) 존재 -> PUT 요청(데이터 C) -> (데이터 A,B 삭제) -> (데이터 C로 대체)

## 2-4. PATCH Method
  리소스를 수정하는 역할.
  PUT과 달리 리소스를 부분 변경한다.
  기존 (데이터 A,B) 존재 -> B = C 대체후 PATCH 요청 -> (데이터 A,C로 변경)
  PATCH Method를 지원하지 않는 서버도 있다. 이때는 POST를 사용

## 2-5. DELETE Method
  리소스를 제거.