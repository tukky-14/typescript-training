# ジェネリクス (Generics)

この講義では、TypeScript のジェネリクスについて学びます。ジェネリクスを使うことで、型に依存しない汎用的な関数やクラスを作成することができます。

## 1. ジェネリック関数 (Generic Functions)

ジェネリック関数は、関数の入力と出力に任意の型を指定できるようにします。これにより、異なる型のデータを処理する同じロジックを再利用できます。

### ジェネリック関数の基本

ジェネリック関数を定義するには、関数名の後に角括弧`<T>`を付けます。`T`はジェネリック型パラメータを表します。

```typescript
function identity<T>(arg: T): T {
  return arg;
}

let output1 = identity<string>("Hello");
let output2 = identity<number>(123);

console.log(output1); // 出力: Hello
console.log(output2); // 出力: 123
```

### 型推論

TypeScript は、引数からジェネリック型を推論できるため、明示的に型を指定しなくても良い場合があります。

```typescript
let output1 = identity("Hello");
let output2 = identity(123);

console.log(output1); // 出力: Hello
console.log(output2); // 出力: 123
```

<br/>

## 2. ジェネリックインターフェース (Generic Interfaces)

ジェネリックインターフェースは、インターフェース内の型をジェネリックにすることで、より柔軟な型定義を可能にします。

### ジェネリックインターフェースの定義

```typescript
interface KeyValuePair<K, V> {
  key: K;
  value: V;
}

let pair: KeyValuePair<string, number> = {
  key: "age",
  value: 30,
};

console.log(pair.key); // 出力: age
console.log(pair.value); // 出力: 30
```

この例では、`KeyValuePair`インターフェースは 2 つのジェネリック型パラメータ`K`と`V`を受け取り、それぞれ`key`と`value`の型を定義しています。

<br/>

## 3. ジェネリッククラス (Generic Classes)

ジェネリッククラスは、クラスのメンバーに対してジェネリック型を使用することで、クラスをより汎用的に設計できます。

### ジェネリッククラスの定義

```typescript
class GenericNumber<T> {
  zeroValue: T;
  add: (x: T, y: T) => T;

  constructor(zeroValue: T, addFunction: (x: T, y: T) => T) {
    this.zeroValue = zeroValue;
    this.add = addFunction;
  }
}

let myNumber = new GenericNumber<number>(0, (x, y) => x + y);
console.log(myNumber.add(myNumber.zeroValue, 10)); // 出力: 10

let myString = new GenericNumber<string>("", (x, y) => x + y);
console.log(myString.add(myString.zeroValue, "hello")); // 出力: hello
```

この例では、`GenericNumber`クラスがジェネリック型`T`を受け取り、`zeroValue`と`add`メソッドの型として使用しています。

<br/>

## 4. 制約付きジェネリクス (Generic Constraints)

ジェネリック型に制約を設けることで、ジェネリック型が特定のプロパティを持つことを保証できます。これにより、ジェネリック型で可能な操作を限定できます。

### 制約の定義

制約を定義するには、`extends`キーワードを使用して、ジェネリック型が従うべき型を指定します。

```typescript
interface Lengthwise {
  length: number;
}

function logLength<T extends Lengthwise>(arg: T): T {
  console.log(arg.length);
  return arg;
}

logLength("Hello"); // 出力: 5
logLength([1, 2, 3, 4, 5]); // 出力: 5
// logLength(10); // エラー: 'number' 型に 'length' プロパティがないため
```

この例では、`logLength`関数は`Lengthwise`インターフェースを拡張するジェネリック型を受け取ります。これにより、引数`arg`が`length`プロパティを持つことが保証されます。

## 5. ジェネリック型のデフォルト値 (Default Types)

ジェネリック型にデフォルトの型を指定することができます。これにより、型が明示的に指定されなかった場合に使用されるデフォルトの型が提供されます。

### デフォルト型の定義

```typescript
function createArray<T = string>(length: number, value: T): T[] {
  return Array(length).fill(value);
}

let stringArray = createArray(3, "hello");
console.log(stringArray); // 出力: [ 'hello', 'hello', 'hello' ]

let numberArray = createArray<number>(3, 42);
console.log(numberArray); // 出力: [ 42, 42, 42 ]
```

この例では、`createArray`関数はデフォルトで`string`型を使用しますが、必要に応じて他の型を指定することもできます。
