---
title: "サブクラスで生徒IDを追加する"
---

## 問題

`Person`クラスを継承して`Student`クラスを作成しましょう。
また、`Student`には`studentId`を持たせましょう

```typescript
class Person {
  name = "";
  age = 0;
  constructor(name: string, age: number) {
    this.name = name;
    this.age = age;
  }
}

// 以下に、Studentクラスを定義するコードを追加してください
class Student extends Person {}

const student = new Student("John", 20, "123456");
console.log(student.name); // John
console.log(student.age); // 20
console.log(student.studentId); // 123456
```

## 実行環境

以下のリンクから実行環境に遷移できます。

出力される値については、「実行」または「Run」ボタンを押してみてください。

- [生徒情報を出力する:コード](https://www.typescriptlang.org/ja/play?#code/MYGwhgzhAEAKCmAnCB7AdtA3gKGtNYAtvNALzQBEFA3LtGAOYnkAMtew6EALogK7BuKRAAoCxAFzQeiAJZoGAGnpMpaPoQBGSAJRY6ebgAtZEAHTjm+IvHZ5ox02cZWXdgL7ZP2APQ-ogKdygNBygNYMgIAMAMrcfAAm8GjcgPUMgJcMgJ0MgEkMgFnagJX+gJoMgNEMgM0MgD8MgJMM6YC-8YAFSoDqDIBmDIDyDIAGDICqDIAiDNigkDBRsfHc0PAAHtzxMTAIyOj63pxoPNLRcQlk+PAA7tC9y9wiFABSKEZoFMoATCzKFACMZwDMACwArABsFDq0c6gg8GYgKAwRDw+gkLDYPtA-NBDsdOlwUD8-gCgUt+s4mBCoRc4fMEb9-oDgTszET+gBJGKY-y3R6vIA)

## 回答例

以下の通りです。

- [生徒情報を出力する:回答例](https://www.typescriptlang.org/ja/play?#code/MYGwhgzhAEAKCmAnCB7AdtA3gKGtNYAtvNALzQBEFA3LtGAOYnkAMtew6EALogK7BuKRAAoCxAFzQeiAJZoGAGnpMpaPoQBGSAJRY6ebgAtZEAHTjm+IvHZ5ox02cZWXdgL7ZP2APQ-ogKdygNBygNYMgIAMAMrcfAAm8GjcgPUMgJcMgJ0MgEkMgFnagJX+gJoMgNEMgM0MgD8MgJMM6YC-8YAFSoDqDIBmDIDyDIAGDICqDIAiDNigkDBRsfHc0PAAHtzxMTAIyOj6eDx9CQCSMWSUNNh0nGgyAkKillIy8koq8Goa2ojKc3GLMQe8R3o49tJ8AA5IYjbKLjp2hiZzNd+ksVsDbh4vOtNjxpNEbgNyGh4AB3aC9BEiCgAKRQRjQFGUACYWMoKABGIkAZgALABWABsFD+nS4KBA8DMIBQDBE4O4Fhsf2gfmguPxrK27M53N5-OcTGFopJktQHK5PL58P6Zn5SyV-kptMZQA)

親クラスにない新しいプロパティを追加することができることの例です。

TypeScript ではクラスはあまり使いませんが、書けると表現の幅が広がります。

なお、アクセシビリティ修飾子をつけないと`public`になります。

`private`として`name`や`age`が定義されていたら`Person`内でしかアクセスできなくなります。
