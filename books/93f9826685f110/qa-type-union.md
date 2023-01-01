---
title: "複数の型を許容できる型を使う"
---

## 問題

type「User」または type「Admin」をのいずれかの型が入ってくる type「Person」を定義し、persons 配列と logPerson 関数でのコンパイルエラーを解消してください。
（参考元：[Marat Dulin](https://github.com/mdevils)さんの [TypeScriptExercises](https://typescript-exercises.github.io/)）

```typescript
interface User {
  name: string;
  age: number;
  occupation: string;
}

interface Admin {
  name: string;
  age: number;
  role: string;
}

type Person = unknown; // ①Personの型を定義する

const persons: User[] = [
  //②User型をPerson型に変更する
  {
    name: "Max Mustermann",
    age: 25,
    occupation: "Chimney sweep",
  },
  {
    name: "Jane Doe",
    age: 32,
    role: "Administrator",
  },
  {
    name: "Kate Müller",
    age: 23,
    occupation: "Astronaut",
  },
  {
    name: "Bruce Willis",
    age: 64,
    role: "World saver",
  },
];

function logPerson(user: User) {
  //③User型をPerson型に変更する
  console.log(` - ${user.name}, ${user.age}`);
}

persons.forEach(logPerson); //Person型配列のpersonsを正しく出力する
```

## 実行環境

以下のリンクから実行環境に遷移できます。

- [いずれかの型の定義:コード](https://www.typescriptlang.org/ja/play?#code/JYOwLgpgTgZghgYwgAgKoGdrIN4ChnIhwC2EAXMumFKAOYDc+yct5hArsQEbSMED2CBOwAOcMMH4gKVGiAa4AvrlyhIsRCgCCAE2KgcTIqRnU6fZqwohOPKBaj8ANm1nmlKsAE8RKAArQ6FLIALzI7CAA1iD8AO4gyAD0iciABiQBUEEggHYMgNHqgEkMgFnagJX+gJoMgNEMKrgIUlTIvpm1FBjQANoAuqHIrUzJgIYkLVAFGVm5gNYMgJCagC9mFUx4BATGbABEALJwAB7Iq+xU0MRwICDLADRMBCxsAEwArGcLyILCYhJSFMsAwgAWwMQgEF5KLEIBARKcmIp7oYHkt3gApQ4oAAi-Ag4IelwoAGYrlCCI4XO9dPoQMBZOJ+FB0chIXNzoQSCsANLiFCrAA-ThcVLxlmuWN5T1E4kk0mQyy0sikcHYYGptII8wWsPFACEoOwkMgAOrALlk6kXKzIABsABZeQSVtrKU4dJQ4AA3aDys7tRi4GARBCvBJOfi0EZSAAUu2gzUwUAAlDgkolAEYkg2GgSk42mswINRAQRcADp-bRgwADZAAWmQABJsGGoLmlpDK9XI7nLooi1HGMpcA0suhczBKQBRRBfYMFoMgDtxie5QCyiYB0JWyPdq+UAxtaAdQZAPIMgC-FQDZShUgA)

皆さんはコメントが書かれてるところに自由に書き込んで、コンソールログから結果を見てみましょう。

「実行」または「Run」ボタンを押してみてください。

## 回答例

以下の通りです。

- [いずれかの型の定義:回答](https://www.typescriptlang.org/ja/play?#code/JYOwLgpgTgZghgYwgAgKoGdrIN4ChnIhwC2EAXMumFKAOYDc+yct5hArsQEbSMED2CBOwAOcMMH4gKVGiAa4AvrlyhIsRCgCCAE2KgcTIqRnU6fZqwohOPKBaj8ANm1nmlKsAE8RKAArQ6FLIALxomFAAPrr6ICq4CFJUyL5QQSDoFAFpUgDaALqhyLlMeAQExmwARACycAAeyDXsVNDEcCAgVQA0TAQsbABMAKy95ciCwmISUhRVAMIAFsDEIBBelADuEBAiPUyKY4bjlXMAUh0oACL8EPvjAxQAzINHBI4uczGgwLLi-FB7shDqU+oQSNUANLiFA1AA-ThcgLeliGTxRk1E4kk0mQVS0sikcHYYCBIIIZXKpzxACEoOwkMgAOrARG-IH9KzIABsABYUR9qkyAU4dJQ4AA3aBk3r5Ri4GDsEAIGYgZBOfi0bLpAAULWgWUCUgAlDhkExEhlnBAAHQa2g6gAGyAAtMgACTYfVQG2VQ4er0RG0DRSO42MZS4VLpdA2mAAgCiiEWOvt2pN9CAA)

エラーが出ない方法はいくらかありますが、今回は[ユニオン型](https://typescriptbook.jp/reference/values-types-variables/union#%E3%83%A6%E3%83%8B%E3%82%AA%E3%83%B3%E5%9E%8B%E3%81%AE%E5%9E%8B%E6%B3%A8%E9%87%88)を使ってみましょう。
ちなみに配列の要素にユニオン型を使う時は`()`が必要ですので気を付けましょう。

```ts
type Persons = (Admin | User)[];
```
