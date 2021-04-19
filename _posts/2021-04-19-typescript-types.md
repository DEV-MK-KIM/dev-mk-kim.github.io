---
title: "Typescript Type Casting"
categories: typescript
date: 2021-04-19 00:00:00 -06:00
toc: true
tags:
  - typescript
---


> 개인적으로 배우고 실수한 내용을 노트한 포스트 입니다

## Typescript 에러

### object is possibly null
```ts

const anchor = document.querySelector('a')

console.log(a.href) //=> object is possibly null
```
This feature is called "strict null checks", to turn it off ensure that the --strictNullChecks compiler flag is not set.

or 
```ts

const anchor = document.querySelector('a')!

console.log(a.href) //=> error's gone
```

or use type casting
```ts
const form = doucment.querySelector('.new-item-form') as HTMLFormElement
//.new-item-form => 클래스 네임
```


