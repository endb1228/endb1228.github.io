---
title: CSS Page Layout
author: Jonghyeok Lee
date: 2022-03-18
category: javascript
layout: post
---

## Positioning

[Blog][page layout, blog]

### 1. Normal flow

기본적으로 대부분의 요소들은 normal flow를 따라 부모 요소 안에서 순서대로 배치됨  
만약 특정 요소에 normal flow를 벗어나는 스타일이 적용되면 해당 요소는 normal flow가 적용된 요소들과 독립적으로 배치됨 

### 2. Containing block

[MDN][containing black, MDN]

컨테이닝 블록은 어떤 요소의 크기 및 위치를 결정하는 기준이 되는 영역을 뜻함
일반적으로는 부모 요소의 content 영역이지만, 이는 position 프로퍼티에 따라 달라짐

### 3. Position

[MDN][position, MDN]  

Position 속성은 어떤 요소를 컨테이닝 블록으로 식별할 것인지를 결정함  
Position 속성에는 다음 5가지 종류가 있음

* static  
기본값으로, 요소가 normal flow를 벗어나지 않으며 top, left같은 프로퍼티에도 영향을 받지 않음

  
* relative  
요소가 normal flow를 벗어나지 않으며 자기 자신의 위치(아마 static일 때의 위치)를 기준으로 top, left같은 프로퍼티의 영향을 받음
  

* sticky
요소가 기본적으로 normal flow를 벗어나지 않고 static과 유사하게 작동  
top, left같은 프로퍼티로 지정한 임계값을 벗어나면 normal flow를 벗어나고 fixed와 유사하게 작동  
컨테이닝 블록의 content 영역에 다다르면 다시 fixed가 해제됨


* absolute  
요소가 normal flow를 벗어나며 상위 요소를 기준으로 top, left같은 프로퍼티의 영향을 받음

  
* fixed  
요소가 normal flow를 벗어나며 뷰포트나 페이지 영역을 기준으로 top, left같은 프로퍼티의 영향을 받음


[page layout, blog]: https://blog.tommyzip.co.kr/code/css-basic-layouts-display/#display-outside-inside
[containing black, MDN]: https://developer.mozilla.org/ko/docs/Web/CSS/Containing_block
[position, MDN]: https://developer.mozilla.org/en-US/docs/Web/CSS/Containing_block
