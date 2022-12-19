---
title: "数値の合計を出力する"
---

## 問題

以下のような型を定義して、それを使用した関数を実装してみましょう。

```typescript
function sum(numbers: number[]) {
  // 配列内の数値を加算して返す処理を実装する
}

console.log(sum([1, 2, 3, 4, 5])); // 15
```

## 実行環境

以下のリンクから実行環境に遷移できます。

- [数値の合計を出力する:コード](https://www.typescriptlang.org/ja/play?#code/GYVwdgxgLglg9mABAZxAWwBRnQIwKYBOyAXItmvgQNoC6AlIgN4BQiiA9O4oLKJg6EqChioDsGQA6mgEgVASQyACpUDp3oHUGQGYMgFfjAmgyAzxUBgLuMD52oFGI5YGiGZgF9mzCAmRwANngB0VuAHMMqTFQCMAGkQAmbwGZvABZvAFZ6OgBuDi53UOYgA)

皆さんはコメントが書かれてるところに自由に書き込んで、コンソールログから結果を見てみましょう。

「実行」または「Run」ボタンを押してみてください。

## 回答例

以下の通りです。

- [数値の合計を出力する:回答](https://www.typescriptlang.org/ja/play?#code/GYVwdgxgLglg9mABAZxAWwBRnQIwKYBOyAXItmvgQNoC6AlIgN4BQiiA9O4oLKJg6EqChioDsGQA6mgEgVASQyACpUDp3oHUGQGYMgFfjAmgyAzxUBgLuMD52oFGI5YGiGVogJ4oIAknKVkAOhMATEBDwYMAQwA0OBgF4AfIhuiADUiDiIRnTMAL7MzBAIyHAANng2yXAA5hiomFQAjB6IAExFAMxFACxFAKz0dADcHFz5NcxAA)

これもシンプルな問題。
どうせなら reduce の使い方を勉強しましょう。
MDN の[Array.prototype.reduce()](https://developer.mozilla.org/ja/docs/Web/JavaScript/Reference/Global_Objects/Array/reduce)の記述がわかりやすいです。
コールバック関数を使うことで、巻子がより高度な抽象化を提供できるようになります。
次の例題でも、reduce を使った問題を考えました。
