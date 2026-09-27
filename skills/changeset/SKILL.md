---
name: changeset
description: リリースノートに掲載する変更内容を changeset ファイルとして記録する。changeset を作成するときに使う。
---

# changeset

`npx changeset` などの `changeset` コマンドは使わない。インタラクティブモードで起動するため、エージェントが操作を進められない。代わりに `.changeset/` にファイルを直接作成する。

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

`package.json` を確認してパッケージ名を特定する。モノレポでは変更対象のパッケージを特定する。

## bump type

| 種別    | 目安                                   |
| ------- | -------------------------------------- |
| `major` | 破壊的変更                             |
| `minor` | 新機能の追加、後方互換性のある機能変更 |
| `patch` | バグ修正                               |

バージョンが `0.x.y` の場合、破壊的変更は `major` ではなく `minor` とする。

## 説明

`release-notes` スキルに従って書く。

## 例

```md
---
"my-package": minor
---

CSV エクスポート機能を追加する
```
