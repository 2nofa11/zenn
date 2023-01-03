---
title: "ユーティリティ型を使ってみる"
---

## 問題

① User 型の定義を変えることなく filterUsers 関数の定義を修正し、必要な条件のみを渡せるようにしましょう。
②filterUsers 関数の 2 つ目の引数`criterias`で、プロパティ`type`は不要なため引数設定で、フィルターをかけましょう。
（参考元：[Marat Dulin](https://github.com/mdevils)さんの [TypeScriptExercises](https://typescript-exercises.github.io/)）

```typescript
interface User {
  type: "user";
  name: string;
  age: number;
  occupation: string;
}

interface Admin {
  type: "admin";
  name: string;
  age: number;
  role: string;
}

type Person = User | Admin;

const persons: Person[] = [
  {
    type: "user",
    name: "Max Mustermann",
    age: 25,
    occupation: "Chimney sweep",
  },
  {
    type: "admin",
    name: "Jane Doe",
    age: 32,
    role: "Administrator",
  },
  {
    type: "user",
    name: "Kate Müller",
    age: 23,
    occupation: "Astronaut",
  },
  {
    type: "admin",
    name: "Bruce Willis",
    age: 64,
    role: "World saver",
  },
  {
    type: "user",
    name: "Wilson",
    age: 23,
    occupation: "Ball",
  },
  {
    type: "admin",
    name: "Agent Smith",
    age: 23,
    role: "Administrator",
  },
];

const isAdmin = (person: Person): person is Admin => person.type === "admin";
const isUser = (person: Person): person is User => person.type === "user";

function logPerson(person: Person) {
  let additionalInformation = "";
  if (isAdmin(person)) {
    additionalInformation = person.role;
  }
  if (isUser(person)) {
    additionalInformation = person.occupation;
  }
  console.log(` - ${person.name}, ${person.age}, ${additionalInformation}`);
}

function filterUsers(persons: Person[], criteria: User): User[] {
  // ①必要な条件のみを渡せるように
  // ②プロパティ`type`が入らないように
  return persons.filter(isUser).filter((user) => {
    const criteriaKeys = Object.keys(criteria) as (keyof User)[];
    return criteriaKeys.every((fieldName) => {
      return user[fieldName] === criteria[fieldName];
    });
  });
}

console.log("Users of age 23:");

filterUsers(persons, {
  age: 23, //例：引数をageだけにしたい（現状だとUser型のオブジェクトを渡す必要がある）
}).forEach(logPerson);
```

## 実行環境

以下のリンクから実行環境に遷移できます。

- [型プログラミング:コード](https://www.typescriptlang.org/ja/play?#code/JYOwLgpgTgZghgYwgAgKoGdrIN4ChkHJgCeADhAFzIDkArplNQNz6EhwC2ly6YUoAcxaFkcAdxC0OAI2jDCAewQJapOGGAKQVXvxBDcAX1y5QkWIhQBBACYdQOVgRLkq1OHdDMnydlx18gvIEYhJSslDByFAKADbcukFGJi4oAArQ6FrIALxoDMgAPsi29iAsuAhavMjkUFkg6FQZ9VoA2gC6uchtPthEZNx0DNQANL6cQwCycAAeyFP05hxwICBjouJUAEwArONKKmoaWm4AwgAWwBwgEMQ8AO4QEKTUyIajfT4iqW4eZWNvmxJm4AFKrFAAEQUEEBIhEoSoAGZtp94YQYvE3KVQMBdOoFIwfB8vujnIM3PRoHCyX4hgBpdQoKYAH9i8UYaLJiOQ2yRXPRh1U6k02hoVl0WjgtDA1GJAscZIGrho-y8CpEdLcACEoLQkMgAOrAdl4mnonkANgALBqMXEhobCbEbDw4AA3any0lk340KmcoEELU0Y2xBrm+E8vl2ghC46inVwdlykQkkR4JV+9yedaxib+cXicDIADK9jAF0jCK2vP5QeiDuxubxfAJRLTuA6FSqjTAyDxOJA3QAFHUGs1MloAJRUcfZPElXO5AB8tSnIAAdKlcjk8jmASxezU8RgsHkxxvJ60QLP1zeB+h8ue1-Otzu9-uA95cDBaCAEBOYdYgUAQWgaS8b2vBpp0VQh4n7DwbGAIDkwASRAGBCRWIDumobwRGAGBkBHQdc0gmDYMzbkbGQ1DYgwrCoBw0VujfTdMQgKJjEI4jSPQM8oAomcqIbJCUNFdDMOwkVsjydj41k8piR8Y8HU3ECBBHAADZAAFpkAAEmwdi6Q+IyTI3TdQnM4zxPoxiZKAwxtOnFhjF-f9ANYmATXMQT0GExpoPaDpxgQfhzGAOAqEEu9BM6RwAHokuQQADEkAUf1AEDIwArBkAQ3NADe5QA7BkAfwZACSGQBCO0AbQZAGiGQAIhkAMQZAGsGXAUuQQBDEkAdYZAFuGQBFhkAMYZAGKGbTUm0wAZBkAU0VAEiGHLABEGRqWpEKAIDAWgoGHN90E3XzYnMfi4u2vzoBHEcA1gnI12o9Fj37CKUOgaL6TuJ88gAeWkAArCBAM3ABrZ6RzuqK4FguAnxHf7iAUYi4s6KIlpWtbhyBh64Ce4gtogT0oGIE7fIgF0ADlJnOy6GwR1b1uQAM2nxonJi6T9kBR-g4Fp4ACZsYmuG7BtDDc4kBY8tT4g00CR2oALkGhzYUD5ChqAF38jqgAKRx8TaFSuqNaz5ZAUsAaPlACx-wBUfUAB1MytCQADBkARQYmsAdQZAH0GWbAAh-wA-50ANqcrcACwZBMAaPUisAKoZADWGQAOhkAcoZAHqGQAJhkqwBNBmysbACEGGrAEh-lTp22wkAFFEAuEdNPAmcmCAA)

皆さんはコメントが書かれてるところに自由に書き込んで、コンソールログから結果を見てみましょう。  
「実行」または「Run」ボタンを押してみてください。

ヒントとしては以下を参考にしてください。

- ① についてのヒント：[partialt の型引数](https://typescriptbook.jp/reference/type-reuse/utility-types/partial#partialt%E3%81%AE%E5%9E%8B%E5%BC%95%E6%95%B0)
- ② についてのヒント：[Omit<T, Keys>](https://typescriptbook.jp/reference/type-reuse/utility-types/omit)

## 回答例

TypeScript の型を理解していないと、難易度が高いです。
① についての回答は以下の通りです。

- [型プログラミング(① について):回答](https://www.typescriptlang.org/ja/play?#code/JYOwLgpgTgZghgYwgAgKoGdrIN4ChkHJgCeADhAFzIDkArplNQNz6EhwC2ly6YUoAcxaFkcAdxC0OAI2jDCAewQJapOGGAKQVXvxBDcAX1y5QkWIhQBBACYdQOVgRLkq1OHdDMnydlx18gvIEYhJSslDByFAKADbcukFGJi4oAArQ6FrIALxoDMgAPsi29iAsuAhavMjkUFkg6FQZ9VoA2gC6uchtPthEZNx0DNQANL6cQwCycAAeyFP05hxwICBjouJUAEwArONKKmoaWm4AwgAWwBwgEMQ8AO4QEKTUyIajfT4iqW4eZWNvmxJm4AFKrFAAEQUEEBIhEoSoAGZtp94YQYvE3KVQMBdOoFIwfB8vujnIM3PRoHCyX4hgBpdQoKYAH9i8UYaLJiOQ2yRXPRh1U6k02hoVl0WjgtDA1GJAscZIGrho-y8CpEdLcACEoLQkMgAOrAdl4mnonkANgALBqMXEhobCbEbDw4AA3any0lk340KmcoEELU0Y2xBrm+E8vl2ghC46inVwdlykQkkR4JV+9yedaxib+cXicDIADK9jAF0jCK2vP5QeiDuxubxfAJRLTuA6FSqjTAyDxOJA3QAFHUGs1MloAJRUcfZPElXO5AB8tSnIAAdKlcjk8jmASxezU8RgsHkxxvJ60QLP1zeB+h8ue1-Otzu9-uA95cDBaCAEBOYdYgUAQWgaS8b2vBpp0VQh4n7DwbGAIDkwASRAGBCRWIDumobwRGAGBkBHQdc0gmDYMzbkbGQ1DYgwrCoBw0VujfTdMQgKJjEI4jSPQM8oAomcqIbJCUNFdDMOwkVsjydj41k8piR8Y8HU3ECBBHAADZAAFpkAAEmwdi6Q+IyTI3TdQnM4zxPoxiZKAwxtOnFhjF-f9ANYmATXMQT0GExpoPaDpxgQfhzGAOBmjgKANGTAAeQSVzvQTOjgggoAgMBaCgYc33QTdfNicx+ME6dir86ARxHANYJyNdqPRY9+wilDoGi+k7ifPIAHlpAAKwgQDNwAax6kd2qiuBYLgJ8Rwm4gFGIirOiiERsty-LkGmzq4G64giogT0oGIWrfIgF0ADlJgapqG02nK8uHAM2kum7Ji6T9dsi-b3uAK6bFurhuwbQw3OJSGPLU+INNAkdqAC5AVs2FA+QoahId-aqoACkcfEKhVmqjWs+RUyqmIAUUQC4R008CZyYIA)

こちらはヒントに記載した、Partial を使用しています。
使用すると、オブジェクト型 T のすべてのプロパティをオプションプロパティにすることができます。
今回は、引数を`Partial<User>`とすることで、`name`や`age`をオプショナルな引数として設定しています。

つづいて、② についての回答は以下の通りです。

- [型プログラミング(② について):回答](https://www.typescriptlang.org/ja/play?#code/JYOwLgpgTgZghgYwgAgKoGdrIN4ChkHJgCeADhAFzIDkArplNQNz6EhwC2ly6YUoAcxaFkcAdxC0OAI2jDCAewQJapOGGAKQVXvxBDcAX1y5QkWIhQBBACYdQOVgRLkq1OHdDMnydlx18gvIEYhJSslDByFAKADbcukFGJi4oAArQ6FrIALxoDMgAPsi29iAsuAhavMjkUFkg6FQZ9VoA2gC6uchtPthEZNx0DNQANL6cQwCycAAeyFP05hxwICBjouJUAEwArONKKmoaWm4AwgAWwBwgEMQ8AO4QEKTUyIajfT4iqW4eZWNvmxJm4AFKrFAAEQUEEBIhEoSoAGZtp94YQYvE3KVQMBdOoFIwfB8vujnIM3PRoHCyX4hgBpdQoKYAH9i8UYaLJiOQ2yRXPRh1U6k02hoVl0WjgtDA1GJAscZIGrho-y8CpEdLcACEoLQkMgAOrAdl4mnonkANgALBqMXEhobCbEbDw4AA3any0lk340KmcoEELU0Y2xBrm+E8vl2ghC46inVwdlykQkkR4JV+9yedaxib+cXicDIADK9jAF0jCK2vP5QeiDuxubxfAJRLTuA6FSqjTAyDxOJA3QAFHUGs1MloAJRUcfZPElXO5AB8tSnIAAdKlcjk8jmASxezU8RgsHkxxvJ60QLP1zeB+h8ue1-Otzu9-uA95cDBaCAEBOYdYgUAQWgaS8b2vBpp0VQh4n7DwbGAIDkwASRAGBCRWIDumobwRGAGBkBHQdc0gmDYMzbkbGQ1DYgwrCoBw0VujfTdMQgKJjEI4jSPQM8oAomcqIbJCUNFdDMOwkVsjydj41k8piR8Y8HU3ECBBHAADZAAFpkAAEmwdi6Q+IyTI3TdQnM4zxPoxiZKAwxtOnFhjF-f9ANYmATXMQT0GExpoPaDpxgQfhzGAOBmjgKANGTAAeAB5CtEsE0YACJUkylcVzvQTOjgggoAgMBaCgYc33QTdfNicx+ME6dar86ARxHANYJyNdqPRY9+wilDoGi+k7ifPJkukAArCBAM3ABrMaR0GqK4FguAnxHRbiAUYjUpQ9KGCynL8s6KIRFK8rKuQFbhrgUbiBqiBPSgYh2t8iAXQAOUmLqeobC6yoq4cAzaD7vsmLpPxuyK7rB4BPpsH6uG7BtDDc4kMY8tT4g00CR2oALkF2zYUD5ChqAx39WqgAKRx8aqFV6qNaz5FTmqYgBRRALhHTTwJnJggA)

ヒントに記載した、`Omit<T, Keys>`を使うと解決できます。
使用すると、T からプロパティ名`Key`を除いたオブジェクトを再生成できます。
今回は、引数を`Omit<User,"type">`としていることで、"type"のプロパティが入ってくるのをガードしています。
試しに`filterUsers`の第二引数に`type`を設定すると、以下のコンパイルエラーが発生します。

`Object literal may only specify known properties, and 'type' does not exist in type 'Partial<Omit<User, "type">>'`

今回はユーティリティ型を使って、型によるプログラミングを行いました。
