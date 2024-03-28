---
title: 스프링 기초 - Hello 페이지 만들기 [정적 컨텐츠]
description: >-
    정적 컨텐츠로 Hello 페이지를 만들어봅니다.<br>  
    출처 : [김영한, 스프링 입문 - 코드로 배우는 스프링 부트, 웹 MVC, DB 접근 기술](https://www.inflearn.com/course/%EC%8A%A4%ED%94%84%EB%A7%81-%EC%9E%85%EB%AC%B8-%EC%8A%A4%ED%94%84%EB%A7%81%EB%B6%80%ED%8A%B8
author: Glesep
categories: [Spring, Backend]
tags: [Spring, Backend]
---

## 정적 컨텐츠
하나의 HTML 파일 자체를 웹 브라우저에 전달해 주는 기능이다.
```html
    <!DOCTYPE HTML>
    <html>
        <head>
            <title> 정적 컨텐츠입니다.
            <meta http-equiv="Content Type" content="text/html; charset=UTF-8">
        </head>
        <body>
            정적 컨텐츠입니다.
        </body>
    </html>
```

## 작동 원리
>1. 웹 브라우저에서 톰켓 서버에 url을 전달한다.
>2. 톰켓 서버에서 받은 정보를 스프링 컨테이너에 전달한다.
>3. hello-static 관련 컨트롤러가 없다고 판단, resources: static/hello-static.html 파일에 접근한다.
>4. hello-static.html 파일을 웹 브라우저에 전달한다.