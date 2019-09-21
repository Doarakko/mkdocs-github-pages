# React
- 内容が変更された箇所のみ更新される
  - DOM 全体が再構成されないのではやい
- レンダリングする前にすべての値をエスケープしている
    - インジェクション攻撃やクロスサイトスクリプティングを防ぐ

- Logical && Operator
    - `true` の場合のみメッセージが返される
```
return (
    <div>
      <h1>Hello!</h1>
      {unreadMessages.length > 0 &&
        <h2>
          You have {unreadMessages.length} unread messages.
        </h2>
      }
    </div>
  );
```

## Component
- 関数のようなもの
- ネストが深くなったらコンポーネントを分ける
- コンポーネントは一つのことをするべき
    - 再利用しやすくなる 
    - [Single responsibility principle](https://en.wikipedia.org/wiki/Single_responsibility_principle)

## event
- キャメルケースのプロパティ名を使用
    - JSX は HTML よりも JavaScript に近いため
- W3C の仕様に則って定義されている
    - ブラウザ間の互換性を考慮する必要ない
- `handleChange`
    - 何かしらのキー入力がされた場合に発動
```
// 入力を大文字に変換して表示
handleChange(event) {
  this.setState({value: event.target.value.toUpperCase()});
}
```
- `handleSubmit`
    - サブミット処理時に起動

## `state` と `props`
### `state`
- そのコンポーネント内で管理
- 更新する際は `setState()` を使用する
    - コンストラクタ以外では直接代入しない
- 下にいるコンポーネントにのみ反映

### `props`
- 親のコンポーネントのプロパティ
- いじらない
- コンポーネントの props は [Pure function](https://en.wikipedia.org/wiki/Pure_function) にするべき
  - 入力（引数）を更新しない
```
[Bad]
function withdraw(account, amount) {
  account.total -= amount;
}
```

## Inheritance
- いまいち継承との違いがわからない
- Facebook 内で継承を使うケースはなかった
- [Composition vs Inheritance](https://reactjs.org/docs/composition-vs-inheritance.html)


## list and key
- `key` に `index` を使うとパフォーマンスが下がるのでよくない
    - 指定しなかった場合はデフォルトで `index` が入る
```
[Bad]
const todoItems = todos.map((todo, index) =>
  // Only do this if items have no stable IDs
  <li key={index}>
    {todo.text}
  </li>
);

[Good]
const todoItems = todos.map((todo) =>
  <li key={todo.id}>
    {todo.text}
  </li>
);
```

## Thinking in React
1. UI を階層構造に落とし込む
2. 静的なものを最初に作成
    - 動的なものとは切り分けておいた方が良い
    - 静的なものを作成する場合は絶対に state を使わない
    - コンポーネントの作成はボトムアップでもトップダウンでも OK
3. なにが state か決める
4. state を置く場所を決める
    - どのコンポーネントに配置するべきか
5. 逆方向のデータをフローを追加

## プロジェクト構成
- 長い時間悩むくらいなら全て1つのフォルダに入れる
  - 開発していく中で変えていく
  - 一般的にはよく一緒に編集されるファイルを同じディレクトリに入れる
- [File Structure](https://ja.reactjs.org/docs/faq-structure.html)
 

## JavaScript
- `=>`
    - `function` を省略
    - 宣言された時点での this が使用される
```
let normalFunc = function(x){
    console.log(x);
}

let arrowFunc = (y) => {
    console.log(y);
}
```
```
param = 'global param';

let printParam = () => {
  console.log(this.param);
}

let object = {
  param: 'object param',
  func: printParam
}
let object2 = {
  param: 'object2 param',
  func: printParam
}

object.func();
object2.func();

[Output]
global param
global param
```

- `parseFloat`
    - 数字以外の場合は `NaN` になる
  
- `==` と `===`
    - 2 == "2": true
    - 2 === "2": false
    - 2 === 2: false

- `String.indexOf()`
  - 引数の文字列が含まれている場合はインデックスを返す
  - 含まれていない場合は -1 を返す
  - [String​.prototype​.indexOf()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/String/indexOf)

- Babel
    - 新しい記法で書いた JavaScript を古い記法に自動で変換
    - 新しい記法でブラウザが対応していないものや実行環境のバージョンが古い場合に使用


## Research
- `bind`

## Reference 
- [step-by-step guide](https://reactjs.org/docs/hello-world.html)
- [【JavaScript】アロー関数式を学ぶついでにthisも復習する話](https://qiita.com/mejileben/items/69e5facdb60781927929)
- [Index as a key is an anti-pattern](https://medium.com/@robinpokorny/index-as-a-key-is-an-anti-pattern-e0349aece318)
- [React における State と Props の違い](https://qiita.com/kyrieleison/items/78b3295ff3f37969ab50)
- [JavaScript 忘れがちな　=== と == の違い](https://qiita.com/PianoScoreJP/items/e43d70ec188c6fed73ed)
