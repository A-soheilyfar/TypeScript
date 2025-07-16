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
TypeScript یک‌سری type helpers داخلی داره که کار با types رو سریع‌تر و امن‌تر می‌کنن.

```ts
type Todo = { title: string; done: boolean };

let partial: Partial<Todo> = { title: "Test" };
let readonlyTodo: Readonly<Todo> = { title: "x", done: false };

```
### 🔹 Partial<T>
تمام پراپرتی‌های یک type رو اختیاری می‌کنه.



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
 ### در TypeScript دو روش اصلی برای تعریف ساختار داده وجود داره:

interface: تعریف قرارداد برای اشیاء

type: تعریف نوع (برای انواع گسترده‌تر)



## ✅ interface
برای تعریف شکل و ساختار یک object، معمولاً از interface استفاده می‌کنیم.







```ts
interface User {
  id: number;
  name: string;
  isAdmin?: boolean; // optional
}

```

### 🎯 مزایا
قابلیت وراثت (extends) داره

مخصوص objectها طراحی شده

مناسب برای استفاده در کلاس‌ها

```ts
interface Admin extends User {
  role: string;
}


```

## ✅ type
type انعطاف‌پذیرتره و می‌تونه برای:

Primitive types

Union / Intersection

توابع، تاپل‌ها، و ...

استفاده بشه:

```ts
type ID = string | number;

type User = {
  id: ID;
  name: string;
};

```



| نوع تعریف | قابلیت گسترش (extend) | استفاده در کلاس | تعریف Primitive |
|-----------|------------------------|------------------|------------------|
| `interface` | ✅ بله                  | ✅ بله            | ❌ خیر            |
| `type`      | 🔸 با ترکیب            | ❌ خیر            | ✅ بله            |

| ویژگی           | `interface`    | `type`             |
| --------------- | -------------- | ------------------ |
| قابلیت توسعه    | ✅ (extendable) | 🔸 (از طریق Union) |
| ترکیب           | ✅              | ✅ (with `&`)       |
| استفاده در کلاس | ✅              | ❌                  |
| تعریف primitive | ❌              | ✅                  |



## 🌐 دسترسی به DOM
```ts
const input = document.querySelector<HTMLInputElement>("#username");

if (input) {
  input.value = "Ali";
}
```

## ❗️ مدیریت خطا (Error Handling)

```ts
function safeDivide(a: number, b: number): number {
  if (b === 0) throw new Error("Division by zero!");
  return a / b;
}

try {
  safeDivide(10, 0);
} catch (error) {
  console.error((error as Error).message);
}

```


```ts
function Log(target: any, propertyName: string) {
  console.log(`Property decorated: ${propertyName}`);
}

class Person {
  @Log
  name: string = "Ali";
}

```
### ⚠️ نیاز به فعال‌سازی در tsconfig.json:

```json

"experimentalDecorators": true


```

<div dir="rtl">


  
## ✅ خلاصه مهم‌ترین نکات
همیشه از strict در tsconfig استفاده کن

Arrow Function از this محیط استفاده می‌کنه

interface برای ساختارهای پیچیده بهتره

type برای primitive‌ها و ترکیب تایپ‌ها عالیه

از async/await برای کار با Promise استفاده کن

از utility type‌ها مثل Partial, Readonly, Record زیاد استفاده کن

## ✅ چک‌لیست یادگیری TypeScript
 انواع داده‌ها (number, string, boolean, ...)

 آرایه و تاپل

 انوم (Enum)

 توابع و Arrow Functions
تفاوت Interface و Type

 کلاس و وراثت

 ماژول‌ها (import/export)

 جنریک‌ها

و Utility Types

 مدیریت خطا

 کار با DOM

 و async/await

و Decorators (اختیاری)

</div>
