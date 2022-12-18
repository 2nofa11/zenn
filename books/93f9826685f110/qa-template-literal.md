---
title: "テンプレートリテラルを使う"
---

## 問題

以下のような型を定義して、それを使用した関数を実装してみましょう。

```typescript
type User = {
  name: string;
  age: number;
  location: string;
};

function greet(user: User) {
  // ユーザーを挨拶する処理を実装する
}

const user: User = {
  name: "John",
  age: 30,
  location: "New York",
};

greet(user); // こんにちは、Johnさん。あなたは30歳で、ニューヨークに住んでいますね。

```

## 実行環境

以下のリンクから実行環境に遷移できます。

* [文字列を出力する:コード](https://www.typescriptlang.org/ja/play?#code/C4TwDgpgBAqgzhATlAvFA3gKClAdgQwFsIAuKOYRAS1wHMBubKfW0vAV0ICMlGcAbAPYBjfMCqDcZCtTqMAvo0wAzdrmHjJUWoggRgACnYJEZeEgCUGJgHobUQGcMgH4ZAbQxPASQyAKY0BvRoE0GQNEMgGeKgGAu7oD52oCjEQGY8piYwpIUUMZIZiao1jgExGQARABSggAWuLkANEwsbADMAAwVAiJiElJQuQByEADuUACagogA1uUxSjp6himIFvRQdlCAygyAyQyA1gyAhgyA9gyAgAyFJYCqDEuAQAyAQgyAVgyA+gwbdYDO1oDmDFuA0wyApwxOgBcMToD1DCuA8vJLt4AiDIA-Bl8gFsGQ6YIA)

皆さんはコメントが書かれてるところに自由に書き込んで、コンソールログから結果を見てみましょう。

「実行」または「Run」ボタンを押してみてください。

## 回答例

以下の通りです。

- [文字列を出力する:回答](https://www.typescriptlang.org/ja/play?#code/C4TwDgpgBAqgzhATlAvFA3gKClAdgQwFsIAuKOYRAS1wHMBubKfW0vAV0ICMlGcAbAPYBjfMCqDcZCtTqMAvo0wAzdrmHjJUWoggRgACnYJEZeEgCUGJsMlxB-CADohtA0xwADQMoMgZIZA1gyAhgyA9gyAgAwAJOjGSE4ExPKAqgy+gEAMgEIMgFYMgPoMwZHRiE4sEPKAztaA5gwRUSYuImISuPL+gPLyvqWAIgyAfgyAmgyAtgzJnkwWCpiYtrgUUHlmJqjWOHFsAEQAUoIAFrgLADRMhWQAzAAM2wI1mlJQCwByEADuUACagogA1luYisM6eoZ5g1AA9P8oH4gmEVuskmkssFDmVQoBphkApwyAH4ZABcMyMA9QxNFodHrJTBAA)

シンプルな問題です。（もはやモダンJavaScriptの域ですが、、、）

サバイバルTypeScriptの[文字列リテラル](https://typescriptbook.jp/reference/values-types-variables/string#%E3%83%86%E3%83%B3%E3%83%97%E3%83%AC%E3%83%BC%E3%83%88%E3%83%AA%E3%83%86%E3%83%A9%E3%83%AB)の記載がなかなか体系化されていて「なるほど」となりました。

> 基本的に"を使用する
> ただの文字列で内部で変数展開をしていないのであれば"を使用します。
>
> 文字列の中に"が含まれる場合は'を使用する
> 文字列の中に"が含まれる場合はエスケープするのではなく'を使用します。
>
> 文字列展開する必要があるときは`を使用する
> 式を計算する必要があるときはテンプレートリテラルを使用します。
