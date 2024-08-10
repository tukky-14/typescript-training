# 型の拡張 (Type Extensions)

この講義では、TypeScript における型の拡張について学びます。型の拡張を使用すると、既存の型を再利用しつつ、新しいプロパティを追加したり、既存の型に機能を加えることができます。

## 1. インターフェースの拡張 (Extending Interfaces)

インターフェースの拡張を使用すると、既存のインターフェースに新しいプロパティを追加して、新しいインターフェースを作成することができます。

### 基本的なインターフェースの拡張

既存のインターフェースを拡張するには、`extends`キーワードを使用します。

```typescript
interface Person {
  name: string;
  age: number;
}

interface Employee extends Person {
  employeeId: number;
}

let employee: Employee = {
  name: "John",
  age: 30,
  employeeId: 12345,
};

console.log(employee.name); // 出力: John
console.log(employee.age); // 出力: 30
console.log(employee.employeeId); // 出力: 12345
```

この例では、`Employee`インターフェースは`Person`インターフェースを拡張して、新たに`employeeId`プロパティを追加しています。

### 複数のインターフェースを拡張

インターフェースは複数のインターフェースを同時に拡張することも可能です。

```typescript
interface Person {
  name: string;
  age: number;
}

interface Skills {
  skills: string[];
}

interface Employee extends Person, Skills {
  employeeId: number;
}

let employee: Employee = {
  name: "Alice",
  age: 28,
  skills: ["JavaScript", "TypeScript"],
  employeeId: 98765,
};

console.log(employee.name); // 出力: Alice
console.log(employee.skills); // 出力: [ 'JavaScript', 'TypeScript' ]
console.log(employee.employeeId); // 出力: 98765
```

この例では、`Employee`インターフェースは`Person`と`Skills`の両方を拡張しています。

<br/>

## 2. 型エイリアスの拡張 (Extending Type Aliases)

型エイリアスもまた、既存の型を拡張して新しい型を定義することができます。型エイリアスの拡張は、交差型（Intersection Types）を使用して実現されます。

### 型エイリアスの拡張の例

```typescript
type Person = {
  name: string;
  age: number;
};

type Employee = Person & {
  employeeId: number;
};

let employee: Employee = {
  name: "Bob",
  age: 35,
  employeeId: 54321,
};

console.log(employee.name); // 出力: Bob
console.log(employee.age); // 出力: 35
console.log(employee.employeeId); // 出力: 54321
```

この例では、`Employee`型エイリアスは`Person`型を拡張して、新たに`employeeId`プロパティを追加しています。

### 条件付き型の拡張

条件付き型を使用すると、ある型が特定の条件を満たす場合に異なる型を適用することができます。これにより、より柔軟な型定義が可能になります。

```typescript
type MessageOf<T> = T extends { message: unknown } ? T["message"] : never;

type Email = {
  message: string;
};

type Dog = {
  bark(): void;
};

type EmailMessageContents = MessageOf<Email>; // string
type DogMessageContents = MessageOf<Dog>; // never
```

この例では、`MessageOf`型が条件に基づいて`T["message"]`または`never`を返しています。

<br/>

## 3. インターフェースと型エイリアスの違い

インターフェースと型エイリアスは似ていますが、いくつかの違いがあります。

### インターフェースの特徴

- **宣言のマージ**: 同じ名前のインターフェースが複数回宣言された場合、これらは自動的にマージされます。
- **クラスの実装**: クラスはインターフェースを`implements`キーワードで実装できます。

### 型エイリアスの特徴

- **プリミティブ型、ユニオン型、タプル型のエイリアス**: 型エイリアスは、オブジェクト型だけでなく、プリミティブ型や複雑な型（ユニオン型、タプル型など）にも使用できます。
- **拡張のための制限が少ない**: 型エイリアスはインターフェースよりも拡張において柔軟です。

```typescript
// 型エイリアスの例
type ID = string | number;

// インターフェースではできない拡張例
type Name = "Alice" | "Bob";
```
