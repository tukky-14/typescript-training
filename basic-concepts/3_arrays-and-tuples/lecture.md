# 配列とタプル (Arrays and Tuples)

この講義では、TypeScript における配列とタプルの型について学びます。

## 1. 配列の型 (Array Types)

TypeScript では、配列の型を指定することで、配列に含まれる要素の型を統一することができます。

### 配列の型指定

配列の型を指定するには、型名の後に`[]`を付けます。

```typescript
let list: number[] = [1, 2, 3];
```

または、`Array<elementType>`を使用することもできます。

```typescript
let list: Array<number> = [1, 2, 3];
```

### 多次元配列

多次元配列も同様に型を指定することができます。

```typescript
let matrix: number[][] = [
  [1, 2, 3],
  [4, 5, 6],
  [7, 8, 9],
];
```

<br/>

## 2. タプルの型 (Tuple Types)

タプルは、異なる型の要素を含む配列です。固定長の配列として使用され、各要素の型と順序が決まっています。

### タプルの定義

タプルを定義するには、各要素の型を指定します。

```typescript
let tuple: [string, number];
tuple = ["hello", 10]; // OK
// tuple = [10, "hello"]; // Error: 型が一致しない
```

### タプルのアクセスと操作

タプルの要素にアクセスする場合、そのインデックスを使用します。

```typescript
console.log(tuple[0]); // 出力: hello
console.log(tuple[1]); // 出力: 10
```

要素の追加や変更も可能です。

```typescript
tuple[0] = "world"; // OK
// tuple[2] = "error"; // Error: インデックス2は存在しない
```

## タプルの使用例

タプルは、固定された構造のデータを扱う際に便利です。例えば、関数の戻り値として複数の値を返す場合などに使用されます。

```typescript
function getPersonInfo(): [string, number] {
  return ["John Doe", 30];
}

let person: [string, number] = getPersonInfo();
console.log(person); // 出力: ["John Doe", 30]
```
