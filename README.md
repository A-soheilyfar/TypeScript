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

```ts
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

```ts
function greet(name: string): string {
  return `Hi ${name}`;
}

function log(msg: string = "پیام", id?: number): void {
  console.log(msg, id);
}

```


## 🧱 اینترفیس

```ts
interface User {
  id: number;
  name: string;
  isAdmin?: boolean;
}

let user: User = { id: 1, name: "Reza" };

```


## 🏗 کلاس و وراثت
```ts
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

```ts

function identity<T>(val: T): T {
  return val;
}

let output = identity<number>(5);

```


## 🎲 Union & Type Guards
```ts

function print(id: number | string) {
  if (typeof id === "string") {
    console.log(id.toUpperCase());
  }
}
```


## 🧰 Utility Types
```ts
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
## ⚙️ tsconfig.json
```json
{
  "compilerOptions": {
    "target": "ES6",
    "module": "commonjs",
    "strict": true,
    "esModuleInterop": true
  }
}
```

## 🔹 Arrow Function

<div dir="rtl">
Arrow function‌ ها در TypeScript مشابه JavaScript هستند اما با تایپ استاتیک.</div>


```ts
const sum = (a: number, b: number): number => {
  return a + b;
};

```

## 🔍 تفاوت function و arrow function
```ts
//function
function greet1(name: string): string {
  return `Hello ${name}`;
}

// Arrow Function
const greet2 = (name: string): string => {
  return `Hello ${name}`;
};


```

## 🚫 مهم: تفاوت در رفتار this
```ts
class Counter {
  count = 0;

  // تابع معمولی - this اشتباه میشه
  startWrong() {
    setTimeout(function () {
      this.count++;
      console.log(this.count); // ❌ undefined یا NaN
    }, 1000);
  }

  // Arrow Function - this درست باقی می‌مونه
  startRight() {
    setTimeout(() => {
      this.count++;
      console.log(this.count); // ✅ درست
    }, 1000);
  }
}


```

## 🕰 async / await در TypeScript
```ts

const fetchData = async (): Promise<string> => {
  return "Data fetched";
};

fetchData().then((data) => console.log(data));


```

## 📦 Import / Export (ماژول‌ها)
### export در فایل A:

```ts
export const PI = 3.14;

export function calcArea(radius: number): number {
  return PI * radius * radius;
}

```
### import در فایل B:

```ts
import { PI, calcArea } from "./circle";
```


## 🗂 namespace vs module
### ✅ Module
از import/export استفاده می‌کنه

بهترین روش در پروژه‌های مدرن



### 🧩 Namespace (قدیمی‌تر):
```ts
namespace Utils {
  export function log(msg: string) {
    console.log(msg);
  }
}

Utils.log("Hello");

```

## ⚖️ interface vs type

