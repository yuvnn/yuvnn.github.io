---
title: 클론코딩  해보기 | 쿠팡로그인 페이지
author: yuvnn
date: 2023-09-03 20:28:00 +0900
categories: [web]
tags: [html,css,javascipt]
published: true 
---


경아(교수님)의 추천으로 웹 개발이전에 클론코딩을 통해 실전 개발감각을 익혀 보기로 했다. 
참고한 영상은 [여기](https://youtu.be/tshTCv1hwJQ?si=fO934Q2VrddAKaxM)

약 3~4시간 정도 소요

# 발생한 자잘한 오류들과 해결방법

## 1. css 표에서 블릿 없애기
```css
list-style: none;
```
 + 들여쓰기 없애기
 
```css
padding - left : 0px;
```

 + 목록 스타일 (블릿 스타일 바꾸기)
```css
list-style-type: ~~;
```
## 2. > 이거 뭐지?
![Desktop View](/assets/img/m2023-09-03-coupang-login-page/coupang-login-page-1.jpg)
결국 코드 하나씩 지워보면서 발견
html 주석달 때 오타난 거 였음
이런 실수 너무 시러 진짜.....

## 3. 정렬이 이상하다잉
![Desktop View](/assets/img/2023-09-03-coupang-login-page/coupang-login-page-2.jpg)
```
align-self: center;
```
## 4. 자바스트립트  오류 - true is not defined

![Desktop View](/assets/img/2023-09-03-coupang-login-page/coupang-login-page-3.jpg)
갑자기 뜬 오류

![Desktop View](/assets/img/2023-09-03-coupang-login-page/coupang-login-page-4.jpg)
입력할때 텍스트가 아니라 예약어로 입력되어야 하나봄
(사진의 ture 목록 중 아래가 아닌 위 선택)
개발환경에서 색깔로 되면 제대로 된거임

##### + 
자바스크립트에서는 
TRUE (X) FALSE (X)
true (O) false (O)


# 기억하면 좋을 듯

## 1. span tag에 title 속성 넣어줘서 마우스 올렸을 때 메세지 뜨게 할 것 (역할 표시)

## 2. css에서 하이퍼링크 밑줄 없애기
```css
text-decoration: none;
```
## 3. span 수직 정렬 : vertical-align
```css
vertical-align: bottom;
```
![Desktop View](/assets/img/2023-09-03-coupang-login-page/coupang-login-page-5.jpg)
저 네모상자랑은 무슨 이유에서인지는 몰라도 center가 아니라 bottom 을 해야 정렬이 맞음.

## 4. js css랑 제대로 연결되고 있는지 확인하기 위해
console.log() 사용하기

# 완성!
![Desktop View](/assets/img/2023-09-03-coupang-login-page/coupang-login-page-6.jpg)


---
> Written with [StackEdit](https://stackedit.io/).
