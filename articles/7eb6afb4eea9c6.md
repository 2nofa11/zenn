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
- data オプションは、以下役割を一度に行ないます。
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
- setup 関数の状態データは、データのリアクティブを行なわないため、明示的にリアクティブ化を行なう必要があります。
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
- computed からリアクティブなデータに依存させることで、再計算を行なっています。
- 例

```vue
<template>
  <span>{{ message }}</span>
  <br />
  <button @click="count++">Click me</button>
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
https://play.vuejs.org/#eNp9UkFOwzAQ/IqxOICoGqTeolABVQ9wAAQcfWhwtqlbx7bsdYkU5e/YTgg9oEZRsp4Zj2c36eiDMfOjB5rTAqExskRYMsWwcKZUy65rwLmyhr4vsoQk7stmY+ERtSL3XAp+uGOUa6/w5obR5SoipIEiGzRBX2SnJ6jCcSsMhhpaoy2SCrall9hF56rE8uo6lQwtoLeKjCuG6ZT8dlj28dXP4pPrxniEKh+VY/bJZ3LapHRQkcsOd8LNk2FPUIQdF5tTX6bCHVofotIZRce12op6vndahakFa0Ji440REuyrQaGVYzSPcUm4GC2l1N/PCUPrIUQdcL4DfvgH37s2Yoy+WXBgj8DoxGFpa8CBXn+8QBvqiWx05WVQnyHfwWnpY8ZB9uhVFWKf6FLapyZ+EaHqT7duEZT7bSoGjco48KgOv87qTOt/cRfzRdoXBkr7H1Gk3E8=

にてさわってみてください。
`data`の値を変えるとそれに紐づいて表示メッセージが変わります。

## CompositionAPI

- computed 関数を使用します。
- computed 関数は、第一引数に派生データを算出するための関数をとる高階関数です。
- データに変更が行なわれた差にリアクティブシステムで算出を行ないます。
- なお、data と同様 return にて値をコンポーネントに登録します。
- 例

```vue
<template>
  <span>{{ message }}</span>
  <br />
  <button @click="count++">Click me</button>
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

https://play.vuejs.org/#eNp9UU1PwzAM/Ssh4rCJaUPabeomYNoBDoCAYw4rrVu6pUmUOKNS1f+Ok3YfB7Soaiy/Z79np+WPxkwPHviCJwi1kSnCSiiBiTOpWrVtDc6lJXRdMouZiH3b2RB4RK3YQyarbL8UPNNe4d2d4Kt1yLAaklnPIX4yu1RQictsZZDiqjbaImstFJNM18Yj5B0rrK6Z4GROcKGgiZwcitRL4gZ5B+jNaBxjgZlWDll0wJaMeo3ux0Kx4fToMA3hR53RaMyWK7aNfiFnt23sMD2k0kPHsKKSmy01ChKWBK0a9IIiMSdnjXAGhZ7ShYt+9NH6+nH5hKMjN0VVTndOK9o8NWQ0abBUSbBvBityK/gijBmaCp5KqX9fYg6th0GUan4g2/+T37km5AR/t+DAHmiHJwxTWwL28ObzFRqKT2Ctcy+JfQX8AKelDx572pNXOdm+4EW3z/FVK1V+uU2DoNxxqGA0MLvIjy+8vjL62e58Oo91tFDe/QFi9+4a

を参照してください。

## CompositionAPI における注意点

### this を使用しなくなる。

OptionsAPI では、script 内でコンポーネントに登録されたデータを`this.count`として取得します。  
一方、CompositionAPI では`count.value`としてデータを取得します。  
template 内は今まで通り、`count`のみで利用できます。
