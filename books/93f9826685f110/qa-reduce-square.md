---
title: "配列の数値を 2 乗する"
---

## 問題

以下の配列から各要素を 2 乗した結果を格納した配列を返す関数を、reduce を使用して実装してください。

```typescript
const array = [1, 2, 3, 4, 5];

function square(numbers: number[]) {
  // 配列の数値を 2 乗する処理を実装する
}

console.log(square(array)); //
```

## 実行環境

以下のリンクから実行環境に遷移できます。

- [数値を 2 乗する:コード](https://www.typescriptlang.org/ja/play?#code/MYewdgzgLgBAhgJwXAnjAvDA2gRgDQwBMBAzAQCwECsAugNwBQDAZgK5jBQCW4MEAjq0QBTABRhWAWwBGwhBABcMCTLlYaAShgBvBjBgB6AzECyiYHQlQHYMgB1NAJAqAkhiIxA6nKBNBkDRDIDPFQGAudwPnagUYj3BgBfJlBIEAAbYQA6SJAAc1EBIQQxRGQUDQ06Q2NsfBhKGABOAhwANgJCWhggA)

皆さんはコメントが書かれてるところに自由に書き込んで、コンソールログから結果を見てみましょう。

「実行」または「Run」ボタンを押してみてください。

## 回答例

以下の通りです。

- [数値を 2 乗する:回答](https://www.typescriptlang.org/ja/play?#code/MYewdgzgLgBAhgJwXAnjAvDA2gRgDQwBMBAzAQCwECsAugNwBQDAZgK5jBQCW4MEAjq0QBTABRhWAWwBGwhBABcMCTLlYaAShgBvBjBgB6AzECyiYHQlQHYMgB1NAJAqAkhiIxA6nKBNBkDRDIDPFQGAudwPnagUYj3PRgEYShWBDBlKVl5ADpQgBNWYDFROGBgKVYAGzgoEAQFFVj1AiykYTAoADU4HNZhYpi5LQwAPh1g-QysyVz8wriAB1YIAAtRCtDquobhGAAqGGmq2vrGjW6QsIio3uy8goQmfQBfPHUts6ZQSBAc4TickABzUQEhUPSkVA0NOiGYzYfAwSgwACcBBwADYCIRaDAgA)

こちらも reduce を使った例です。
reduce より、Mapのほうが楽そうですね。

- [数値を 2 乗する(map 使用):回答](https://www.typescriptlang.org/ja/play?#code/MYewdgzgLgBAhgJwXAnjAvDA2gRgDQwBMBAzAQCwECsAugNwBQDAZgK5jBQCW4MEAjq0QBTABRhWAWwBGwhBABcMCTLlYaAShgBvBjBgB6AzECyiYHQlQHYMgB1NAJAqAkhiIxA6nKBNBkDRDIDPFQGAudwPnagUYj3PRgEYShWBDBlKVl5ADpJOAAHcSkMAD5oyRgAKiyNBgBfJlBIEAAbYTjykABzUQEhUNFEZBQNDTpDY2x8GEoYAE4CHAA2AkJaGCA)
