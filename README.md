# 📘 راهنمای کامل TypeScript — همراه با مثال

> یادگیری کامل تایپ‌اسکریپت به زبان ساده و با مثال‌های کاربردی برای پروژه‌های واقعی

---

## 🚀 مقدمه

**TypeScript** یک زبان برنامه‌نویسی متن-باز است که مبتنی بر جاوااسکریپت نوشته شده و تایپ استاتیک را به آن اضافه می‌کند. این زبان به توسعه بهتر، ساختارمندتر و ایمن‌تر اپلیکیشن‌های جاوااسکریپتی کمک می‌کند.

---

## 🔧 نصب و راه‌اندازی

### نصب تایپ‌اسکریپت به صورت سراسری:

```bash
npm install -g typescript

```
## کامپایل یک فایل .ts
```bash
tsc index.ts
```
## ایجاد فایل tsconfig:

```bash
tsc --init
```
## 🧠 انواع داده پایه‌ای

```bash
let isActive: boolean = true;
let age: number = 28;
let firstName: string = "Ali";
let anything: any = "Can be anything";


let isDone: boolean = true;
let count: number = 10;
let name: string = "Ali";
let numbers: number[] = [1, 2, 3];
let tuple: [string, number] = ["Sara", 30];
enum Role { User, Admin }
let role: Role = Role.Admin;

```


## انواع توابع

```bash
function greet(name: string): string {
  return `Hi ${name}`;
}

function log(msg: string = "پیام", id?: number): void {
  console.log(msg, id);
}

```


## 🧱 اینترفیس

```bash
interface User {
  id: number;
  name: string;
  isAdmin?: boolean;
}

let user: User = { id: 1, name: "Reza" };

```


## 🏗 کلاس و وراثت
```bash
class Animal {
  constructor(public name: string) {}
  speak() {
    console.log(`${this.name} sound`);
  }
}

class Dog extends Animal {
  speak() {
    console.log(`${this.name} barks`);
  }
}

```

## 🧬 جنریک‌ها

```bash

function identity<T>(val: T): T {
  return val;
}

let output = identity<number>(5);

```


## 🎲 Union & Type Guards
```bash

function print(id: number | string) {
  if (typeof id === "string") {
    console.log(id.toUpperCase());
  }
}
```


## 🧰 Utility Types
```bash
type Todo = { title: string; done: boolean };

let partial: Partial<Todo> = { title: "Test" };
let readonlyTodo: Readonly<Todo> = { title: "x", done: false };

```


## 📦 پروژه نمونه
```bash
project/
├── src/
│   ├── index.ts
├── tsconfig.json
└── README.md

```


