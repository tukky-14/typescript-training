# 関数 (Functions)

この講義では、TypeScript における関数の型アノテーションについて学びます。関数の引数や戻り値に対して型を明示的に指定することで、より安全で予測可能なコードを書くことができます。

## 1. 関数の型アノテーション (Function Type Annotations)

### 引数と戻り値の型

関数の引数や戻り値の型を指定することで、関数が期待通りに使用されることを保証できます。

```typescript
function add(x: number, y: number): number {
  return x + y;
}

let result = add(2, 3); // OK
// let result = add(2, "3"); // Error: 引数の型が一致しない
```

### 戻り値の型を省略

TypeScript は、関数の戻り値の型を推論できるため、明示的に型を指定しないことも可能です。

```typescript
function subtract(x: number, y: number) {
  return x - y; // 戻り値の型は自動的に number と推論される
}
```

<br/>

## 2. オプション引数とデフォルト引数 (Optional and Default Parameters)

### オプション引数

オプション引数は、関数呼び出し時に指定されなくても良い引数です。`?`を使って指定します。

```typescript
function greet(name: string, greeting?: string): string {
  return `${greeting || "Hello"}, ${name}`;
}

console.log(greet("Alice")); // 出力: Hello, Alice
console.log(greet("Alice", "Good morning")); // 出力: Good morning, Alice
```

### デフォルト引数

デフォルト引数は、関数呼び出し時に引数が指定されなかった場合に使用される値を設定します。

```typescript
function greet(name: string, greeting: string = "Hello"): string {
  return `${greeting}, ${name}`;
}

console.log(greet("Alice")); // 出力: Hello, Alice
console.log(greet("Alice", "Good evening")); // 出力: Good evening, Alice
```

<br/>

## 3. 無名関数とアロー関数 (Anonymous Functions and Arrow Functions)

### 無名関数

無名関数（匿名関数）は、関数名を持たない関数です。TypeScript では、無名関数にも型アノテーションを適用できます。

```typescript
let multiply = function (x: number, y: number): number {
  return x * y;
};

console.log(multiply(2, 3)); // 出力: 6
```

### アロー関数

アロー関数は、短縮した構文で関数を定義できる表記方法です。通常の関数と同様に、型アノテーションを適用できます。

```typescript
let divide = (x: number, y: number): number => {
  return x / y;
};

console.log(divide(6, 3)); // 出力: 2
```

アロー関数では、1 行で書ける場合にさらに簡略化できます。

```typescript
let square = (x: number): number => x * x;

console.log(square(4)); // 出力: 16
```

<br/>

## 4. 関数型 (Function Types)

関数自体を型として扱うことができます。これにより、特定の形状を持つ関数を受け取る変数や引数を定義できます。

```typescript
let add: (x: number, y: number) => number = function (x, y) {
  return x + y;
};

console.log(add(10, 20)); // 出力: 30
```
