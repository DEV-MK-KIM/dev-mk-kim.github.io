---
title: "Typescript Classes, Public, Private, Readonly"
categories: typescript
date: 2021-04-19 00:00:00 -06:00
toc: true
tags:
  - typescript
---


> 개인적으로 배우고 실수한 내용을 노트한 포스트 입니다

## Typescript 타입 종류

```ts

// all classes are 'public' by default
class Invoice {
  readonly client: string //readonly => can have access inside or ouside of the class but not modifiable in inside/outside 
  private details: string //private => cannot acceess, change this value outside of the class.
  public amount: number

  constructor(c: string, d: string, a: number) {
    this.client = c
    this.details = d
    this.amount = a
  }

  format() {
    return `${this.client} owes $${this.amount} for ${this.details}`
  }
}

//to make it simple
class Invoice {

  constructor(
    readonly client: string,
    private details: string,
    public amount: number,
  ) {}

  format() {
    return `${this.client} owes $${this.amount} for ${this.details}`
  }
}

const invOne = new Invoice('mk','work',333)
const invTwo = new Invoice('ee','play', 555)

let invoices: Invoice[] = []

invoices.push(invOne)
invoices.push(invTwo)


```

