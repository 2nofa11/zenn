---
title: "Double Bangについて"
---

## Double Bangとは

TypeScriptでよく使われる`!!`の事です。  
この演算子は、変数がnull、またはundefinedであるかどうかを判断するときに使います。

具体例を挙げると、変数の先頭にDouble Bangをつけることで2度評価を行い、変数がtrueであるかを判断します。

```typescript
let variable = "notNull";
if (!!variable) {
	console.log('variable is true');
}
```

## 一問一答

1. 変数が真偽値であるかどうかを判断するにはどのように記述するか？
   ⇒解答: `!!変数`

   





