# TypeScript の導入

この講義では、TypeScript のインストールとプロジェクトの設定方法について学びます。

## 1. TypeScript のインストール

TypeScript をプロジェクトに導入するには、まず Node.js がインストールされている必要があります。Node.js がインストールされていない場合は、[公式サイト](https://nodejs.org/)からインストールしてください。

### npm を使用して TypeScript をインストール

TypeScript は npm を使用して簡単にインストールできます。以下のコマンドを実行して、TypeScript をプロジェクトにインストールします。

```bash
npm install -g typescript
```

グローバルにインストールする代わりに、プロジェクトごとにインストールすることもできます。その場合は、プロジェクトのルートディレクトリで以下のコマンドを実行します。

```bash
npm install --save-dev typescript
```

### TypeScript コンパイラのバージョン確認

TypeScript コンパイラが正しくインストールされたか確認するために、以下のコマンドを実行してバージョンを確認します。

```bash
tsc -v
```

<br/>

## 2. tsconfig.json の設定

TypeScript プロジェクトの設定は、`tsconfig.json`ファイルで行います。このファイルには、コンパイルオプションやプロジェクトに関する情報が含まれています。

### tsconfig.json ファイルの作成

`tsc --init`コマンドを実行すると、デフォルト設定の`tsconfig.json`ファイルがプロジェクトのルートディレクトリに生成されます。

```bash
tsc --init
```

### tsconfig.json の主要な設定

生成された`tsconfig.json`ファイルには、多くのオプションがコメントアウトされた状態で含まれています。ここでは、基本的な設定項目について説明します。

```json
{
  "compilerOptions": {
    "target": "es6", // JavaScriptのバージョンを指定
    "module": "commonjs", // モジュールシステムを指定
    "strict": true, // 厳格な型チェックを有効化
    "esModuleInterop": true, // ESモジュールとの互換性を有効化
    "skipLibCheck": true, // ライブラリの型チェックをスキップ
    "forceConsistentCasingInFileNames": true // ファイル名の大文字小文字の区別を強制
  },
  "include": ["src/**/*"], // コンパイル対象のファイルを指定
  "exclude": ["node_modules", "**/*.spec.ts"] // コンパイルから除外するファイルを指定
}
```

### 主なコンパイラオプションの説明

- `target`: コンパイル後の JavaScript のバージョンを指定します。`es6`（ES2015）や`es5`などが指定できます。
- `module`: モジュールシステムを指定します。Node.js 環境では`commonjs`を使用します。
- `strict`: 厳格な型チェックを有効にします。これにより、潜在的なエラーを事前に検出できます。
- `esModuleInterop`: ES モジュールとの互換性を有効にします。`import`文を使用する際に便利です。
- `skipLibCheck`: ライブラリの型チェックをスキップします。コンパイル速度を向上させるために使用します。
- `forceConsistentCasingInFileNames`: ファイル名の大文字小文字の区別を強制します。異なるファイルシステム間での互換性を保つために重要です。
- `include`: コンパイル対象とするファイルやディレクトリを指定します。
- `exclude`: コンパイルから除外するファイルやディレクトリを指定します。

## まとめ

この講義では、TypeScript のインストール方法と基本的な`tsconfig.json`の設定方法について学びました。これにより、TypeScript プロジェクトの基本的な環境が整います。次の講義では、基本の型について学びます。
