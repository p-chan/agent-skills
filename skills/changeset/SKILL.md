---
name: changeset
description: changeset ファイルを作成する。changeset ファイルを作成するときに使う。
---

# changeset

`changeset` コマンド（`npx changeset` など）は使わない。このコマンドでは、複数段落の説明やコードブロックを渡しにくい。代わりに `.changeset/` にファイルを直接作成する。

## 作成

`.changeset/<ファイル名>.md` に作成する。ファイル名は `happy-bears` のような形容詞と名詞の組み合わせなど、既存の changeset ファイルと重複しない任意の名前にする。

次のテンプレートを使う。

```md
---
"<パッケージ名>": <major|minor|patch>
---

<説明>
```

## パッケージ名

`package.json` を確認してパッケージ名を特定する。モノレポではリリース対象のパッケージをすべて特定し、frontmatter に1行ずつ書く。

## bump type

| 種別    | 目安                                   |
| ------- | -------------------------------------- |
| `major` | 破壊的変更                             |
| `minor` | 新機能の追加、後方互換性のある機能変更 |
| `patch` | バグ修正                               |

バージョンが `0.x.y` の場合、破壊的変更は `major` ではなく `minor` とする。

## 説明

リリースノートに掲載されることを前提に、ユーザー視点で何が変わったのかを書く。

- 1行目に変更の主題だけを、体言止めの1文で書く（「CSV エクスポート機能を追加」）
- 使い方、理由、移行方法など、利用者に伝えたい詳細があれば空行のあとに書く
- 主題が複数あるときは、主題ごとに changeset ファイルを分ける

## 例

### ユーザー視点で書く

NG: 実装視点

```md
---
"my-package": patch
---

リストが空の場合の null チェックを追加
```

OK

```md
---
"my-package": patch
---

空のリストを渡したときにクラッシュする問題を修正
```

### 1行目に主題だけを書く

NG: CSV エクスポート機能を新設したのに、付随するオプションを書いている

```md
---
"my-package": minor
---

--format オプションと --output オプションを追加
```

OK

```md
---
"my-package": minor
---

CSV エクスポート機能を追加
```

### 詳細は空行のあとに書く

NG: 詳細を1行目に続けて書いている

```md
---
"my-package": major
---

`createUser` の引数を options オブジェクト形式に変更。第2引数以降の位置引数は受け付けなくなるので、呼び出し側では引数を options オブジェクトにまとめて渡す
```

OK

````md
---
"my-package": major
---

`createUser` の引数を options オブジェクト形式に変更

第2引数以降の位置引数は受け付けなくなる。呼び出し側では、引数を options オブジェクトにまとめて渡す。

```ts
// Before
createUser("alice", "admin", true);
// After
createUser("alice", { role: "admin", active: true });
```
````
