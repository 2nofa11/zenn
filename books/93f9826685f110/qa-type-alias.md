---
title: "型エイリアスを使う"
---

## 問題

型エイリアスを使用して、複雑な型を定義してみましょう。

```typescript
type Profile = {
  name: string;
  age: number;
  location: string;
  hobbies: string[];
};

type User = {
  id: number;
  email: string;
  profile: Profile;
};

const user: User = {
  // 以下が出力されるようにインスタンス情報を設定する
};

console.log(user); // 以下が出力される
/*
{
  "id": 1,
  "email": "john@example.com",
  "profile": {
    "name": "John",
    "age": 30,
    "location": "New York",
    "hobbies": [
      "guitar",
      "reading"
    ]
  }
}
*/
```

## 実行環境

以下のリンクから実行環境に遷移できます。

- [型エイリアス:コード](https://www.typescriptlang.org/ja/play?#code/C4TwDgpgBACgTgewGYEsA20C8UDeAoKKAOwEMBbCALigGdg4UiBzAGgKhKauIFcyAjCHDaE0CAMYlgKBEWp0GzEVAAWCfvxQQa8+oyYBtALp4AvnjyhIUAKo0hUbPkIoAJtSJ9Bw9hDIl0XUVWdjBEVAxqeGR0CDMLcVk6KB57OGo7Byd2AHocqEBTuUBoOUAZBkAvxUBspUBVBkAYhkBohkAIhkAxBkBrBkAShkBnhkBOhkB+hm7AUYNARg1AJIZAWijALO1ATQY6+LxEohoEDAA6MSYAClShAEpCPMLSytq6oA)

皆さんはコメントが書かれてるところに自由に書き込んで、コンソールログから結果を見てみましょう。

「実行」または「Run」ボタンを押してみてください。

## 回答例

以下の通りです。

- [文字列を出力する:回答](https://www.typescriptlang.org/ja/play?#code/C4TwDgpgBACgTgewGYEsA20C8UDeAoKKAOwEMBbCALigGdg4UiBzAGgKhKauIFcyAjCHDaE0CAMYlgKBEWp0GzEVAAWCfvxQQa8+oyYBtALp4AvnjyhIUAKo0hUbPkIoAJtSJ9Bw9hDIl0XUVWdjBEVAxqeGR0CDMLcVk6KB57OGo7Byd2N2oARmU-ALRqAHIAKwQVIgABCAAPcjAMADpEslLlMJjI3HZCUgoygCkqok7+ji5qAGYABmVRCSkZOShSgDkIAHcoAE0EOABrCcJCNQ0tHSgDUqYeFGASOE71uAgSV31Sk0JzczwiSINAQrTETAAFKkhABKQhAA)

型を使って、複雑な型を表現する練習です。
サバイバル TypeScript の[型エイリアス](https://typescriptbook.jp/reference/values-types-variables/type-alias)がまとまっていました。
