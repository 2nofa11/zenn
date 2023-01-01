---
title: "型の絞り込みを行う"
---

## 問題

前回の問題を拡張します。
logPerson 関数のコンパイルエラーを修正しましょう。
具体的には、引数として入ってくる`Person`が`Admin`型か`User`型か絞り込みをして、メッセージを出力します。
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

export type Person = User | Admin;

export const persons: Person[] = [
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

export function logPerson(person: Person) {
  let additionalInformation: string;
  if () {
    // 型の絞り込みが行えるようにAdmin型とUser型を修正
    additionalInformation = person.role;
  } else {
    additionalInformation = person.occupation;
  }
  console.log(` - ${person.name}, ${person.age}, ${additionalInformation}`);
}

persons.forEach(logPerson);
```

## 実行環境

以下のリンクから実行環境に遷移できます。

- [疑似的な代数的データ型の定義:コード](https://www.typescriptlang.org/ja/play?#code/JYOwLgpgTgZghgYwgAgKoGdrIN4ChnIhwC2EAXMumFKAOYDc+yct5hArsQEbSMED2CBOwAOcMMH4gKVGiAa4AvrlyhIsRCgCCAE2KgcTIqRnU6fZqwohOPKBaj8ANm1nmlKiAA8R-KGGQwAE8RFAAFaHQpZABeNEwoZAAfZF19EEZcb19-ZAQpKmRQqCiQdAoIkqkAbQBdWORqpjwCAmM2ACIAWTgvZC72KmhiOBAQDoAaJgIWNgAmAFYp1uRBYTEJKQoOgGEAC2BiEAggygB3CAgRSaZFZcMV9u2AKVGUABF+CBuV2YoAZjm9wIjhc2zSoGAsnEfh+yDuzWmhBInQA0uIUF0AD9OFxQOEzKzIOb-YGrISicSSaTIDpaWRSODsMBwhEEFqtJ60gBCUHYSGQAHVgLioQTLGwAGwAFjJoM6gr8Th0lDgADdoKyprVMtk-AEYOwQAhNiBkE5+LRKqUABTFUoVSJSACUD3NEACcB0OmAprgTgAkiAYH4RqbTHIFARgDBkDbXRyCAB6JPIQDR6oA7BkAer6AKIZAD3xgH8GQAyDIAZCMAEgyAaIZABEMgDEGQDWDBCQGnABYMGGgacASQyAO-lAMbWSK9Pr9geDoap0Ti9qkADp5RZFMgIE5MG6Zt7fdT-UGQ1Aw9SGpOQFO1pTTXOmPkys4IFOLbQbQADZAAWmQABJsAep+07m+P07D7MP7vgO66MsO267lIij3s6jDKLgB7oFO24AKKIHsNq3taLr0EAA)

皆さんはコメントが書かれてるところに自由に書き込んで、コンソールログから結果を見てみましょう。

「実行」または「Run」ボタンを押してみてください。

## 回答例

以下の通りです。

- [疑似的な代数的データ型の定義:回答](https://www.typescriptlang.org/ja/play?#code/JYOwLgpgTgZghgYwgAgKoGdrIN4ChkHJhwDmAXAEQCumUFA3PoSHALYRnLphSgmOFkpDshBVWAI2gDCAewQIqABzhhgskJ268Q-XAF9cuUJFiIUAQQAmrUDiYFi5CnBugGD0WxHa+MgsKcYpLSnlCyADY+PH4GRmAAnkooAArQ6BrIALxotMgAPsjWtiCMuAga3MjJUBkg6JxptRoA2gC62cgtnniCgk6UNNAUADSegizsnADkALJwAB7IszSmrHAgINNjfYSByABMAKw7u8jyiipqGjMAwgAWwKwgEAlcAO4QEErTnvqnBF6ZwGLjcIFG42Y3hmACkNigACKyCDbSEBEgiADMBwBfXCURmxVAwG0qlkUF+gn+PTRRFIg1oELOXimyGmAGlVChZgAfiJRCm4wT7A6YoVyBTKVTqTRsizaDRwKhgSmEamCIG7EGuEpMs6TETTABCUCoSGQAHVgPySajmfsAGwAFnFBHxhot5IiVi4cAAbtBVQRDG0yjAqCAENcQMgIrISE06gAKGp1RrpDQASnsgiiYCEViswGjcAiAEkQDByeto1oYrp-MhgDBkCmMyAAHRObJZHKg3XZ7DIAD0w+QgGj1QB2DIA9X0AUQyAHvjAP4MgBkGQAyEYAJBkA0QyACIZAGIMgGsGWmuIsl8uV6vSzI5VMaDvuxv6ZAQCKYHNnY-FmWlitVqA1mWdDenYXFK0YPp4FT1JEEAdnGJBJgABsgAC0yAACTYEBHYGv86GYe2HbCLhGEfqeP4XtG+gIZmjCGLgQHoB2v4AKKIPcSZwYmWb0EAA)

今回は「リテラル型」をそれそれぞれの型（オブジェクト型のそれぞれに”タグ”となるプロパティ）に定義して、入ってくる値を絞り込みしています。
このような絞り込みが起こる理屈は、型情報はタグプロパティはオブジェクトが User ならば`user`であり、Admin ならば`admin`です。
ということは、タグの情報が何なのかを調べれば、オブジェクトが User なのか Admin なのか判別でき、絞り込みが行えます。
これらのテクニックは、代数的データ型といわれます。

サバイバル TypeScript では[判別可能なユニオン型の絞り込み](https://typescriptbook.jp/reference/values-types-variables/discriminated-union#%E5%88%A4%E5%88%A5%E5%8F%AF%E8%83%BD%E3%81%AA%E3%83%A6%E3%83%8B%E3%82%AA%E3%83%B3%E5%9E%8B%E3%81%AE%E7%B5%9E%E3%82%8A%E8%BE%BC%E3%81%BF)あたりを参照するといいかもしれません。
