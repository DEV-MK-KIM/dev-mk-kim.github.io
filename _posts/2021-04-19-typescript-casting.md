---
title: "Typescript Explicit Types"
categories: typescript
date: 2021-04-19 00:00:00 -06:00
toc: true
tags:
  - typescript
---


> 개인적으로 배우고 실수한 내용을 노트한 포스트 입니다

## Typescript 타입 종류

```ts
// explicit types
let character: string
let age: nunber
age = 30
character = "hi"

//arrays

// let ninja: string[] wont'w work because it was not initialized
let ninja: string[] = []
ninjas.push('mk')

// union types
let mixed: (string|number|boolean)[] = []
mixed.push('hello')
mixed.push(20)

//objects
let ninjaOne: object;
ninjaOne = { name: 'yoshi'. age: 30}

let ninjaTwo: {
  name: string,
  age: number,
  beltColour: string
}

ninjaTwo = {
  name: 'mario',
  age: 20,
  beltColour: 'black'
}

//function

let greet: Function
greet = () => {
  console.log('hello')
}

const greet = (a: number, b: number) => {
  console.log(a + b)
}

//function signature

//example 1
let greet: (a: string, b: string) => void

greet = (name: sring, greeting: string) => {
  console.log(`${name} says ${greeting}`)
}

//example2
let calc: (a: number, b: number) => number
calc = (numOne: number, numTwo:number) => {
  return numOne + numTwo
}




```

