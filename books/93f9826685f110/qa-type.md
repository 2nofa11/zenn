---
title: "型を使う"
---

## 問題

type「User」を定義し、以下コードで発生しているコンパイルエラーを解消してください。
（参考元：[Marat Dulin](https://github.com/mdevils)さんの [TypeScriptExercises](https://typescript-exercises.github.io/)）

```typescript
type User = {
  // 型を定義してください。
};

const users: unknown[] = [
  {
    name: "Jhon",
    age: 25,
  },
  {
    name: "Taro",
    age: 23,
  },
];

function logPerson(user: unknown) {
  console.log(` - ${user.name}, ${user.age}`); // 型が定義されていないためエラーが発生しています
}

console.log("Users:");
users.forEach(logPerson);
```

## 実行環境

以下のリンクから実行環境に遷移できます。

- [型の定義:コード](https://www.typescriptlang.org/ja/play?#code/C4TwDgpgBAqgzhATlAvFA3gKClA9LqQaPVAkhkCztQSv9B1BkDMGQeQZADBkFUGQEQZAgBkwF8BuTTAYwD2AOzjAoAVwSI4ALglCA1kIEB3IQG0AuqijrsODPoMGhAQwC2EOQHIAUgAth1gDRHjUUwHMrUAEwBWNw5XYyx3EwsfawAVU0QBFzdjLx9fAGYgzE0eTAAzcSE+YABLYSgAGwFPAAUkOGEACkkkOQKlVSEASkNjQREBcogAOkrPBoADKABaKAASdGbEIbNLYLmFqSGUjnHOrjwCQkAZBgpGQBiGamZAKwZmQH0GQECGQAqGQEuGQB+GI8AvN0B8VxpmQD8GQCaDFBOLw+vVBiMqg1rPA6jJrHtMIs4ENcgJEABRUx8ewNUa1aTCRFAA)

皆さんはコメントが書かれてるところに自由に書き込んで、コンソールログから結果を見てみましょう。

「実行」または「Run」ボタンを押してみてください。

## 回答例

以下の通りです。

- [型の定義:回答](https://www.typescriptlang.org/ja/play?#code/C4TwDgpgBAqgzhATlAvFA3gKCjqA7AQwFsIAuOYRASzwHMAabXA2svAVyICMlMBfANyZMAYwD2eClHYJEcUrFkBtALqooSpjiy5d+YmSgByAFIALCUcZ7mrBQCYArFqh9ruHTf0kFRgCoEiGJWLroshvYAzC58mCpCmABm7HgiwFQSUAA2YrQACkhwEgAUMkgK8EgAlBgu4pJiWRAAdDm0xQAGUAC0UAAk6GWIzYQkbv2Dss3hfB1VAlAA9ItQgNHqgDIMgFnagJX+gKoMgDEMgGYMgCIMgFYMx4D6DICBDIAVDICXDIA-DOuAXm6A+K6A6gwngH4MgJoMUPzCepFJqtXLFIyVOSkIzzTBDODNRJiRAAUQIIjMxTaBTkElhQA)
