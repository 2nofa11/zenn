---
title: "オブジェクト配列中の最小のものを返すを出力する"
---

## 問題

以下のような型を定義して、それを使用した関数を実装してみましょう。

```typescript
type Product = {
  name: string;
  price: number;
};

const array: Product[] = [
  { name: "item1", price: 100 },
  { name: "item2", price: 200 },
  { name: "item3", price: 300 },
];

function minPrice(array: Product[]) {
  // プロパティが最小のものを返す関数を実装する
}

console.log(minPrice(array)); // {"name": "item1","price": 100} 
```

## 実行環境

以下のリンクから実行環境に遷移できます。

- [オブジェクトから最小値を取得する:コード](https://www.typescriptlang.org/ja/play?#code/C4TwDgpgBACgTgewCYFcDGwoF4oG8BQUUAdgIYC2EAXFAM7BwCWxA5gNyFRhNrUkrkARhDgcAvh3xoExelFJw4pEDXjJ0wANoBdbFE2dcJCnwBEjYBHIBGUwBouPPtYAMLqGLuHjlGucvkAEz2joy8NIFuHl5ERmS+UP5WAMwh3GF8yVGe+NqSAGYoxBiMMlDkzPAZABQKSiqwiKgYOgCUeJwA9J1QgOsMgLcMgIsMgGMMgMUMgDIMgADmgPA6gHYMgEEMs4BJDIAr8YCaDIBFqYAOpkuA+dqAoxFrgNEM+GL4UjK0CAA2EAB01wgs1RXEVby1isqtrWxQ3XhTPEIKY-BYrLY7KZ0rxQVBXC4xFB8EA)

皆さんはコメントが書かれてるところに自由に書き込んで、コンソールログから結果を見てみましょう。

「実行」または「Run」ボタンを押してみてください。

## 回答例

以下の通りです。

- [オブジェクトから最小値を取得する:回答](https://www.typescriptlang.org/ja/play?#code/C4TwDgpgBACgTgewCYFcDGwoF4oG8BQUUAdgIYC2EAXFAM7BwCWxA5gNyFRhNrUkrkARhDgcAvh3xoExelFJw4pEDXjJ0wANoBdbFE2dcJCnwBEjYBHIBGUwBouPPtYAMLqGLuHjlGucvkAEz2joy8NIFuHl5ERmS+UP5WAMwh3GF8yVGe+NqSAGYoxBiMMlDkzPAZABQKSiqwiKgYOgCUeJwA9J1QgOsMgLcMgIsMgGMMgMUMgDIMgADmgPA6gHYMgEEMs4BJDIAr8YCaDIBFqYAOpkuA+dqAoxFrgNEMnHAQwChwxPKKygB0Z80Q1bVoaAIoADakwAhwDu9FBBiMAAGqkT4oCDtLAAPk4REBZxB4MhEDu6V4UAAPPI3h9vr84BinFAAPxQJHAsEQqFQGikfHkL4-P6cVrifBSGS0BCfdGfBAsaoVYhVXi1W4gVoc-BAA)

ちょっと複雑reduce問題。
三項演算子の条件に当てはまった値が、`accumulator`に登録されて、それをオブジェクトとして出力できます。
