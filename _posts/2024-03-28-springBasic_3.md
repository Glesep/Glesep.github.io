---
title: 스프링 기초 - Hello 페이지 만들기 [API]
description: >-
    API로 Hello 페이지를 만들어봅니다.
author: Glesep
categories: [Spring, Basic]
tags: [Spring, Backend]
---

## @ResponseBody를 이용한 문자 반환
MVC & 템플릿 이용 방식과는 다르게 viewResolver를 사용하지 않습니다.  
@ResponseBody로 인해 문자 내용을 HTTP의 BODY에 직접 반환합니다.

    ```java
        @Controller
        public class HelloController {
            
            // hello-string이라는 경로로 접속합니다.
            @GetMapping("hello-string")
            // HTTP BODY에 직접 반환합니다.
            @ResponseBody
            // @RequestParam("name"): name이라는 파라미터를 받습니다.
            // String name: 위에서 받아온 값을 name 변수에 넣습니다.
            public String helloString(@RequestParam("name") String name) {
                // 아래의 문자가 반환됩니다.
                return "hello " + name;
            }
        }
    ```
### 객체 반환 작동 원리
>1. 웹 브라우저에서 url에 대한 정보를 톰켓 서버로 전달
>2. 톰켓 서버에서 url에서 얻은 정보를 스프링 컨테이너로 전달
>3. 스프링 컨테이너에 있는 컨트롤러(helloController)에서 @ResponseBody 발견 후 문자를 HttpMessageConverter로 전달
>4. 문자를 웹 브라우저로 전달 

## @ResponseBody를 이용한 객체 반환
이번엔 @ResponseBody를 이용해 객체를 반환해 봅니다.

    ```java
        @Controller
        public class HelloController {

            @GetMapping("hello-api")
            @ResponseBody
            public Hello helloApi(@RequestParam("name") String name) {
                // 객체를 만듭니다.
                Hello hello = new Hello();
                // 객체의 이름을 name 파라미터로 받아 온 값으로 정의합니다.
                hello.setName(name);
                // 객체를 반환합니다.
                return hello;
            }

            static class Hello {
                private String name;

                // Getter
                public String getName() {
                    return name;
                }
                // Setter
                public void setName(String name) {
                    this.name = name;
                }
            }
        }
    ```
객체를 반환 시, 객체가 JSON으로 변환됩니다.

### 객체 반환 작동 원리
>1. 웹 브라우저에서 url에 대한 정보를 톰켓 서버로 전달
>2. 톰켓 서버에서 url에서 얻은 정보를 스프링 컨테이너로 전달
>3. 스프링 컨테이너에 있는 컨트롤러(helloController)에서 @ResponseBody 발견 후 hello 객체를 HttpMessageConverter로 전달
>4. 객체를 JSON 파일 형식으로 변환 후 웹 브라우저로 전달 