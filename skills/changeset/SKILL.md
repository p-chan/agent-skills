---
name: changeset
description: changeset を追加する。changeset を追加するときに使う。
---

# changeset

`changeset` コマンド（`npx changeset` など）は使わない。このコマンドはインタラクティブモードで起動するため、エージェントからは操作を進められない。代わりに `.changeset/` にファイルを直接作成する。

## 追加

`.changeset/<ファイル名>.md` として追加する。ファイル名は `happy-bears` のような形容詞と名詞の組み合わせなど、既存の changeset のファイル名と重複しない任意の名前にする。

次のテンプレートを使う。

```md
---
"<パッケージ名>": <major|minor|patch>
---

<説明>
```

## パッケージ名

`package.json` を確認してパッケージ名を特定する。モノレポでは変更対象のパッケージを特定する。

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
- 使い方や理由など、利用者に伝えたい詳細があれば空行のあとに書く。破壊的変更など利用者の対応が必要な変更では、移行方法を必ず書く

## 例

### 機能追加（minor）

NG: 過去形で、1行目が主題ではなく詳細になっている

```md
---
"my-package": minor
---

--format オプションと --output オプションを追加した
```

OK

```md
---
"my-package": minor
---

CSV エクスポート機能を追加
```

### バグ修正（patch）

NG: 実装視点で、過去形

```md
---
"my-package": patch
---

リストが空の場合の null チェックを追加した
```

OK

```md
---
"my-package": patch
---

空のリストを渡したときにクラッシュする問題を修正
```

### 破壊的変更（major）

NG: 過去形で、主題と移行方法が1行に混ざっている

```md
---
"my-package": major
---

createUser 関数のシグネチャを変更しました。第2引数以降を options オブジェクトにまとめました
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
