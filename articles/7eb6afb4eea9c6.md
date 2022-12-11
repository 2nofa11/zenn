---
title: "簡単なOptionsAPIとCompositionAPIの比較（状態データ編）"
emoji: "📢"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: ["vue", "vue3", "JavaScript"]
published: true
---

# 状態データについて

## OptionsAPI

- data オプションにて状態データを管理します。
- data オプションは、以下役割を一度に行います。
  - コンポーネントに状態データを登録
  - Vue.js のリアクティブシステムに登録
- 例

```vue
<script>
export default {
  data() {
    return { count: 0 };
  },
};
</script>
```

皆さんが普段見ているデータの宣言方法ですね。

## CompositionAPI

- 振る舞いを setup 関数を使って定義するという考え方です。
- setup 関数の状態データは、データのリアクティブを行わないため、明示的にリアクティブ化を行う必要があります。
- 例

```vue
<script>
import { ref } from "vue";
export default {
  setup() {
    const count = ref(0); // リアクティブシステムに登録
    return {
      count, // コンポーネントに状態データを登録
    };
  },
};
</script>
```

# コンポーネントの派生データ(算出)について

## OptionsAPI

- computed オプションにて算出プロパティを管理します。
- computed からリアクティブなデータに依存させることで、再計算を行っています。
- 例

```vue
<template>
  <span>{{ message }}</span>
</template>

<script>
export default {
  data() {
    return {
      count: 0,
    };
  },
  computed: {
    message() {
      return `Clicked ${this.count} times!`;
    },
  },
};
</script>
```

実際に動かしたい場合は
https://sfc.vuejs.org/#eNp9kNtqwzAMhl/FM7vYoIl3HUJh7DV8US9R23TxAUnpBsHvPjkNoWxQY2xJlj/p16zfU6qvE+hGtww+jY5hb4PllpIL+3n2QOROkHNrlogNrblPDC11OCQWG35SRFY9HN008lwovWP38rqYlhF4wqBWz3IXp8DN283N5cq7cnbRp4mhb9bMtYWNs5EOH+PQfUGvnmc+D1QvwKx4kB9Ph3uuDbJFwa1VvdODL71W3qX6QjGIfIErZdcHsropjSpZVst8im/1mTlRYwwduzK0C9URT0asGqWylK2BfPWJ8ZsABWy1CNoYRoJXwAoh9ICAj5h/Uv9xC7ao0vkXAr+ltA==

にてさわってみてください。
`data`の値を変えるとそれに紐づいて表示メッセージが変わります。

## CompositionAPI

- computed 関数を使用します。
- computed 関数は、第一引数に派生データを算出するための関数をとる高階関数です。
- データに変更が行われた差にリアクティブシステムで算出を行います。
- なお、data と同様 return にて値を コンポーネント に登録します。
- 例

```vue
<template>
  <span>{{ message }}</span>
</template>

<script>
export default {
  setup() {
    const count = ref(0);
    const message = computed(() => `Clicked ${count.value} times!`);
    return {
      count,
      message,
    };
  },
};
</script>
```

こちらも実際に動かしたい場合は

https://sfc.vuejs.org/#eNp9kN1qhEAMhV9lOvTCBX96La5Q+hpzsVbj1q3zQxJtQXz3ZtTS0sIOomFy/E5OFv0cQj5PoEtdMdgwNgy1cYYrCo2rl8UCUXOFda2K7ca4qvgtdBW1OASWerDBI6sFoU9bb8PE0K2qR2+V0eJhtHHwuWk66JtpFG20IuApJKetNtx6R6xaPzlWZyWs5OlknDrO3j2Gkv63T5Kc1LlWl5dxaN+hU4/LRsjnZpxgVTzILw8XAUULFEN0h190FGX64xHP4bBL1viRlzyyhT2uTvWeN7NNyG/knaxQkEqy7g0yuowBI+7IX0rxxhyoLArq27j4G+Uer4VUOcoYMmcOZLNX9B8EKGCjj9E2RiGXM2CG4DpAwHvMP9J/3IiNqfT6BTYvt38=

を参照してください。

## CompositionAPI における注意点

### this を使用しなくなる。

OptionsAPI では、script 内で コンポーネント に登録されたデータを`this.count`として取得します。  
一方、CompositionAPI では`count.value`としてデータを取得します。  
template 内は今まで通り、`count`のみで利用できます。
