# 列挙型 (Enums)

この講義では、TypeScript の列挙型（enum）について学びます。列挙型は、関連する定数をグループ化して扱うために使用します。

## 1. 列挙型の定義 (Defining Enums)

列挙型を定義するには、`enum`キーワードを使用します。各メンバーにはデフォルトで数値が割り当てられますが、カスタム値を設定することもできます。

### 数値列挙型 (Numeric Enums)

数値列挙型では、各メンバーに自動的に連続した数値が割り当てられます。

```typescript
enum Direction {
  Up,
  Down,
  Left,
  Right,
}

let dir: Direction = Direction.Up;
console.log(dir); // 出力: 0
```

メンバーにカスタム値を割り当てることもできます。

```typescript
enum Direction {
  Up = 1,
  Down,
  Left,
  Right,
}

console.log(Direction.Up); // 出力: 1
console.log(Direction.Down); // 出力: 2
console.log(Direction.Left); // 出力: 3
console.log(Direction.Right); // 出力: 4
```

### 文字列列挙型 (String Enums)

文字列列挙型では、各メンバーに文字列を割り当てることができます。

```typescript
enum Direction {
  Up = "UP",
  Down = "DOWN",
  Left = "LEFT",
  Right = "RIGHT",
}

console.log(Direction.Up); // 出力: "UP"
console.log(Direction.Down); // 出力: "DOWN"
console.log(Direction.Left); // 出力: "LEFT"
console.log(Direction.Right); // 出力: "RIGHT"
```

## 2. 列挙型の使用 (Using Enums)

列挙型は、複数の関連する定数をグループ化して扱う際に便利です。例えば、状態管理やディレクション（方向）の指定などに使用されます。

### 例: 状態管理

```typescript
enum Status {
  NotStarted,
  InProgress,
  Done,
}

let currentStatus: Status = Status.NotStarted;

function updateStatus(status: Status): void {
  currentStatus = status;
  console.log(`Current status: ${Status[currentStatus]}`);
}

updateStatus(Status.InProgress); // 出力: Current status: InProgress
updateStatus(Status.Done); // 出力: Current status: Done
```

### 例: ディレクションの指定

```typescript
enum Direction {
  Up,
  Down,
  Left,
  Right,
}

function move(direction: Direction): void {
  switch (direction) {
    case Direction.Up:
      console.log("Moving up");
      break;
    case Direction.Down:
      console.log("Moving down");
      break;
    case Direction.Left:
      console.log("Moving left");
      break;
    case Direction.Right:
      console.log("Moving right");
      break;
  }
}

move(Direction.Left); // 出力: Moving left
move(Direction.Right); // 出力: Moving right
```

## 3. 定数列挙型 (Const Enums)

定数列挙型（`const enum`）は、コンパイル時にインライン展開されるため、パフォーマンスの向上が期待できます。ただし、通常の列挙型と異なり、リフレクション機能が制限されます。

```typescript
const enum Direction {
  Up,
  Down,
  Left,
  Right,
}

let direction = Direction.Up;
console.log(direction); // 出力: 0
```
