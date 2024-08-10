# オブジェクトの型 (Object Types)

この講義では、TypeScript におけるオブジェクトの型定義について学びます。オブジェクトは JavaScript の基本的なデータ構造であり、TypeScript ではオブジェクトの構造とそのプロパティの型を厳密に定義することができます。

## 1. オブジェクトリテラル (Object Literals)

オブジェクトリテラルを使って、オブジェクトの型を定義することができます。各プロパティに対して、型アノテーションを指定します。

```typescript
let person: { name: string; age: number } = {
  name: "John",
  age: 30,
};

console.log(person.name); // 出力: John
console.log(person.age); // 出力: 30
```

### オプショナルプロパティ

オブジェクトのプロパティに`?`を付けることで、そのプロパティがオプショナル（任意）であることを示すことができます。

```typescript
let person: { name: string; age?: number } = {
  name: "Alice",
};

console.log(person.name); // 出力: Alice
console.log(person.age); // 出力: undefined
```

<br/>

## 2. インターフェース (Interfaces)

インターフェースを使って、オブジェクトの型を再利用可能に定義することができます。インターフェースは、オブジェクトの形状を定義するための契約（コントラクト）を表します。

### インターフェースの定義

```typescript
interface Person {
  name: string;
  age: number;
}

let person: Person = {
  name: "Bob",
  age: 25,
};

console.log(person.name); // 出力: Bob
console.log(person.age); // 出力: 25
```

### オプショナルプロパティと読み取り専用プロパティ

インターフェースでは、オプショナルプロパティや読み取り専用プロパティを定義できます。

```typescript
interface Person {
  name: string;
  age?: number; // オプショナルプロパティ
  readonly id: number; // 読み取り専用プロパティ
}

let person: Person = {
  name: "Carol",
  id: 123,
};

// person.id = 456; // エラー: 'id' は読み取り専用です
```

<br/>

## 3. インデックスシグネチャ (Index Signatures)

インデックスシグネチャを使って、動的なプロパティを持つオブジェクトの型を定義できます。

```typescript
interface StringArray {
  [index: number]: string;
}

let myArray: StringArray = ["Alice", "Bob"];
console.log(myArray[0]); // 出力: Alice
console.log(myArray[1]); // 出力: Bob
```

<br/>

## 4. タイプエイリアス (Type Aliases)

タイプエイリアスを使って、複雑なオブジェクトの型に別名を付けることができます。タイプエイリアスはインターフェースと似ていますが、より柔軟に使用できます。

### タイプエイリアスの定義

```typescript
type Point = {
  x: number;
  y: number;
};

let point: Point = {
  x: 10,
  y: 20,
};

console.log(point.x); // 出力: 10
console.log(point.y); // 出力: 20
```

### 型の合成 (Union Types with Type Aliases)

タイプエイリアスを使って、複数の型を組み合わせることもできます。

```typescript
type Animal = {
  species: string;
};

type Human = {
  name: string;
};

type Cyborg = Animal & Human;

let cyborg: Cyborg = {
  species: "Human",
  name: "RoboCop",
};

console.log(cyborg.species); // 出力: Human
console.log(cyborg.name); // 出力: RoboCop
```
