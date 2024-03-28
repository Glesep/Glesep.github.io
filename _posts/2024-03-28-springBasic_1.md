---
title: 스프링 기초 - Hello 페이지 만들기 [MVC & 템플릿]
description: >-
    MVC & 템플릿 방식으로 Hello 페이지를 만들어봅니다.<br>  
    출처 : [김영한, 스프링 입문 - 코드로 배우는 스프링 부트, 웹 MVC, DB 접근 기술](https://www.inflearn.com/course/%EC%8A%A4%ED%94%84%EB%A7%81-%EC%9E%85%EB%AC%B8-%EC%8A%A4%ED%94%84%EB%A7%81%EB%B6%80%ED%8A%B8
author: Glesep
categories: [Spring, Backend]
tags: [Spring, Backend]
---

## Controller 작성
```java
    @Controller                                         // 컨트롤러라는 것을 알림
    public class HelloController {

        @GetMapping("hello")
        public String hello(Model model) {
            // data라는 속성명을 찾아서 그 곳에 spring!!이라는 내용을 넣는다.
            model.addAttribute("data", "spring!!");
            // resources:templates/hello.html을 찾아서 렌더링(Thymeleaf 템플릿 엔진 처리) 
            return "hello";
        }
    }
```

## hello.html 작성
```html
    <!DOCTYPE HTML>
    <!--thymeleaf 템플릿 엔진 사용할 것-->
    <html xmlns:th = "http://www.thymeleaf.org">
        <head>
            <title>hello</title>
            <meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
        </head>
        <body>
            <!--thymeleaf 템플릿 엔진이 작동하면 th:text=""부분이 작동, 아니면 안녕하세요. 손님 출력-->
            <!--위에서 언급된 ${data}가 여기임-->
            <p th:text="'안녕하세요. ' + ${data}">안녕하세요. 손님</p>
        </body>
    </html>
```

## 작동 원리
> 1. 웹 브라우저에서 url 전송
> 2. 톰켓 서버에서 url을 받고 그 안의 정보들을 helloController에 전달.
> 3. return: hello, model(data, spring!!) 값들을 viewResolver에 전달
> 4. templates/hello.html 파일을 찾아 템플릿 처리
    
