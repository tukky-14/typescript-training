# 基本の型 (Basic Types)

この講義では、TypeScript の基本的な型アノテーションと、主要な基本型について学びます。

## 1. 型アノテーション (Type Annotations)

型アノテーションを使用することで、変数や関数の引数、戻り値に対して型を明示的に指定することができます。

### 変数への型アノテーション

```typescript
let message: string = "Hello, TypeScript";
let count: number = 42;
let isValid: boolean = true;
```

### 関数への型アノテーション

```typescript
function add(a: number, b: number): number {
  return a + b;
}
```

<br/>

## 2. 基本型 (Basic Types)

### 数値 (Number)

数値型は全ての数値を表現します。整数、浮動小数点数の両方を扱います。

```typescript
let decimal: number = 6;
let hex: number = 0xf00d;
let binary: number = 0b1010;
let octal: number = 0o744;
```

### 文字列 (String)

文字列型はテキストデータを表現します。シングルクオートまたはダブルクオートで囲みます。

```typescript
let color: string = "blue";
color = "red";
```

テンプレート文字列を使用することもできます。

```typescript
let fullName: string = `Bob Bobbington`;
let age: number = 37;
let sentence: string = `Hello, my name is ${fullName}. I'll be ${
  age + 1
} years old next month.`;
```

### 真偽値 (Boolean)

真偽値型は`true`または`false`の二値を表現します。

```typescript
let isDone: boolean = false;
```

### null と undefined

`null`と`undefined`はそれぞれ独自の型を持ちますが、基本型に含まれます。

```typescript
let u: undefined = undefined;
let n: null = null;
```

### any 型

`any`型は任意の型を表現します。型チェックを無効にしたい場合に使用します。

```typescript
let notSure: any = 4;
notSure = "maybe a string instead";
notSure = false;
```

### void 型

`void`型は、関数が値を返さないことを示します。通常、関数の戻り値の型として使用します。

```typescript
function warnUser(): void {
  console.log("This is my warning message");
}
```

### never 型

`never`型は、決して発生しない値を表現します。常に例外をスローする関数や、無限ループの型として使用されます。

```typescript
function error(message: string): never {
  throw new Error(message);
}

function infiniteLoop(): never {
  while (true) {}
}
```

### unknown 型

`unknown`型は、どのような値も保持できる型です。ただし、`any`とは異なり、操作を行う前に型チェックが必要です。

```typescript
let notSure: unknown = 4;
notSure = "maybe a string instead";

if (typeof notSure === "string") {
  console.log(notSure.toUpperCase()); // 型チェック後に安全に使用できる
}
```
