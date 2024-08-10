# ユニオン型とインターセクション型 (Union and Intersection Types)

この講義では、TypeScript のユニオン型とインターセクション型について学びます。これらの型は、複数の型を組み合わせることで、より柔軟な型定義を可能にします。

## 1. ユニオン型 (Union Types)

ユニオン型を使用すると、変数やプロパティが複数の型を持つことができるようになります。これは、特定の値がいくつかの異なる型のうちのどれか一つになる可能性がある場合に便利です。

### ユニオン型の定義

ユニオン型は、`|`（パイプ）記号を使用して複数の型を結合することで定義します。

```typescript
let value: string | number;
value = "Hello";
value = 42;
```

この場合、`value`は`string`または`number`のどちらかの型を持つことができます。

### ユニオン型の使用例

ユニオン型を使用することで、異なる型の値を受け取る関数を定義できます。

```typescript
function printId(id: string | number) {
  console.log(`Your ID is: ${id}`);
}

printId("12345"); // 出力: Your ID is: 12345
printId(67890); // 出力: Your ID is: 67890
```

### 型ガード

ユニオン型を使用する場合、実際にその型が何であるかをチェックすることが重要です。これを「型ガード」と呼びます。

```typescript
function printId(id: string | number) {
  if (typeof id === "string") {
    console.log(`Your ID is: ${id.toUpperCase()}`);
  } else {
    console.log(`Your ID is: ${id}`);
  }
}

printId("abc"); // 出力: Your ID is: ABC
printId(123); // 出力: Your ID is: 123
```

<br/>

## 2. インターセクション型 (Intersection Types)

インターセクション型を使用すると、複数の型を結合して新しい型を作成できます。インターセクション型は、指定されたすべての型のプロパティを持つオブジェクトを定義するために使用されます。

### インターセクション型の定義

インターセクション型は、`&`（アンパサンド）記号を使用して複数の型を結合することで定義します。

```typescript
interface Person {
  name: string;
}

interface Employee {
  employeeId: number;
}

type EmployeePerson = Person & Employee;

let employee: EmployeePerson = {
  name: "Alice",
  employeeId: 12345,
};

console.log(employee.name); // 出力: Alice
console.log(employee.employeeId); // 出力: 12345
```

この例では、`EmployeePerson`型は`Person`と`Employee`の両方のプロパティを持つことを要求します。

### インターセクション型の使用例

インターセクション型を使用して、複数のインターフェースを組み合わせた複雑な型を定義できます。

```typescript
interface Drivable {
  drive(): void;
}

interface Flyable {
  fly(): void;
}

type FlyingCar = Drivable & Flyable;

let myCar: FlyingCar = {
  drive() {
    console.log("Driving");
  },
  fly() {
    console.log("Flying");
  },
};

myCar.drive(); // 出力: Driving
myCar.fly(); // 出力: Flying
```

<br/>

## 3. ユニオン型とインターセクション型の組み合わせ

ユニオン型とインターセクション型を組み合わせることで、より複雑な型を表現することができます。

```typescript
interface A {
  a: string;
}

interface B {
  b: number;
}

type C = (A & { c: boolean }) | (B & { d: boolean });

let example1: C = { a: "Hello", c: true };
let example2: C = { b: 42, d: false };

console.log(example1); // 出力: { a: 'Hello', c: true }
console.log(example2); // 出力: { b: 42, d: false }
```
