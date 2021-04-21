---
title: "Typescript Interface"
categories: typescript
date: 2021-04-19 00:00:00 -06:00
toc: true
tags:
  - typescript
---


> 개인적으로 배우고 실수한 내용을 노트한 포스트 입니다

## Typescript Interface with Classes

```ts
// Interface 
interface IsPerson {
  name: string
  age: number
  speak(a: string): void
  spend(a: number): number
}

const me: IsPerson = {
  name: 'mk',
  age: 36,
  speak(text: string): void {
    console.log(text)
  },
  spend(amoount: number): number {
    return amount
  }
}

const greetPerson = (pereson: IsPerson) => {
  console.log('hello', person.name)
}

greetPerson(me)

// Use Interface alongside with classes

interface HasFormatter {
  format(): string
}


// since Invoice class has format() method returns string, it successfully implements HasFormatter
class Invoice implements HasFormatter{
  readonly client: string 
  private details: string
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

// since Invoice class has format() method returns string, it successfully implements HasFormatter
class Payment implements HasFormatter{
  readonly recipient: string 
  private details: string
  public amount: number

  constructor(c: string, d: string, a: number) {
    this.recipient = c
    this.details = d
    this.amount = a
  }

  format() {
    return `${this.recipient} owed $${this.amount} for ${this.details}`
  }
}


let docOne: HasFormatter
let docTwo: HasFormatter




```
