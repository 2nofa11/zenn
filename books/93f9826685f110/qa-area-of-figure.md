---
title: "図形の面積を求める"
---

## 問題

以下のような型を定義して、それを使用した関数を実装してみましょう。

```typescript
type Shape = {
  type: "square" | "triangle";
  width: number;
  height: number;
};

function area(shape: Shape): number {
  // 面積を計算する処理を実装する
  return 0;
}

const square: Shape = {
  type: "square",
  width: 10,
  height: 10,
};

const triangle: Shape = {
  type: "triangle",
  width: 10,
  height: 10,
};

console.log(area(square)); // 100
console.log(area(triangle)); // 50
```

## 実行環境

以下のリンクから実行環境に遷移できます。

出力される値については、「実行」または「Run」ボタンを押してみてください。

- [図形の面積を求める：コード](https://www.typescriptlang.org/ja/play?#code/C4TwDgpgBAygFgQ0lAvFA3gKClUkBcUARAM4COArggE4RFQA+xw1AlggHYDmANnQNzYoAd1YATYHEIcKAWwBGEaoJxwIrLnGDS5i5ZgC+gzADMKHAMbBWAew5QaEBAAoSiArHcQAlDoVKMIQB6IKhAI3TAWS9AJIZACCjAdO9ATQZAaIZAM8VAMBcowHztQFGI5KFaYApqewAGQ0xMCzsSYChyKlpCeCRoNCwcPAhCUkpHIgAaIVEJKSgARhLB1XVNbXHJw2MqjhrcNk5eLs8W1ECO8C2iFnZuPgGh8UlCCamoNQ0ta4WjCuWSGz4AOh4bLmdHFz1Rzebz8KAheZlN4fCDfX7-WguY4bPggsEQgCsZSAA)

## 回答例

以下の通りです。

- [図形の面積を求める:回答例](https://www.typescriptlang.org/ja/play?#code/C4TwDgpgBAygFgQ0lAvFA3gKClUkBcUARAM4COArggE4RFQA+xw1AlggHYDmANnQNzYoAd1YATYHEIcKAWwBGEaoJxwIrLnGDS5i5ZgC+gzADMKHAMbBWAew5QaEBAAoSiArHcQAlDoVKMIVYTKFcvADo8aBQY4nIqWiJvQJwcWmAKans3JAhwtQ0tKAAqKBzIcNEJOBUoAygIHhJoLFSodMz7MNz89U1gErKIqslkgHooACZag0NMTAs7EgH4x0J4XNQU3HAIQlJKRyIAGiERqSgARgAGU9U+rUIb06N5xY5l3DZOXj3PTbQrR2HiILHY3D4JzO4kkT1uQgK-ThL2M7xINj44R4Ni4zkcLlWtG83n4UDGExu1wWSwxeWxuPxzjBPz4xNJ5KgAFYqUA)

図形のパターンが「四角形（square）」と「三角形（triangle）」のみなので条件分岐は if にしています。

なお、`type: "square" | "triangle";`はリテラル型をユニオン型と組み合わせて使っています。

サバイバル TypeScript の[ここあたり](https://typescriptbook.jp/reference/values-types-variables/literal-types#%E3%83%AA%E3%83%86%E3%83%A9%E3%83%AB%E5%9E%8B%E3%81%AE%E7%94%A8%E9%80%94)を参照するといいかもしれません。
