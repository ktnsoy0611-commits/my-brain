パーソナルデータおよびAIコンテキスト共有用リポジトリ

# 構造

```
me/          私という人。少数・恒久
  taste.md       興味・好み
  patterns.md    手配漏れ・物忘れ・後回しの傾向
  goals.md       ゴールとチェックイン
days/YYYY-MM/  日付で増えるものは全部この下（種類は4つに固定）
  facts.md       アプリが書くその日の事実
  voice.md       声のメモの文字起こし
  summary.md     その日のまとめ（あなたが書く）
  feedback.md    カードへの反応ログ
inbox/candidates.md   タスク・ウィッシュの候補
sources/       list.md（巡回する情報源） / stats.md（打率） / proposed.md / dismissed.md
analysis/taste.md     嗜好の分析レポート
```

# 規約

- 恒久的なものは主題ごとに1ファイル（`me/` `sources/` `analysis/` `inbox/`）。
- 日付で増えるものは `days/YYYY-MM/` の中だけに置く。種類は上記の4つで増やさない。
- owner の違うファイルは互いに上書きしない。
- 1ファイルを共同編集するのは `me/taste.md` と `sources/list.md` だけ。
  アプリはファイル内の `<!-- BEGIN app-managed:... -->` と `<!-- END app-managed:... -->` で囲まれたゾーンの内側だけを書き換える。ゾーンの外側は他の owner が自由に編集してよい。
- owner が `app` のファイルはアプリが毎回まるごと書き直すので、手で編集しない。

## front matter

Coworkが書く（または書き足す）ファイルの先頭だけに、次の front matter を付ける。

```
---
owner: cowork
updated: YYYY-MM-DD
---
```

対象は `me/taste.md`・`me/patterns.md`・`analysis/taste.md`・`days/*/summary.md`・`inbox/candidates.md` の5つ。

それ以外（`me/goals.md`、`sources/list.md` 以外の `sources/*`、`days/*/facts.md`・`days/*/feedback.md`・`days/*/voice.md`）はアプリが毎回まるごと書き直すファイルなので、front matter を付けても次の同期で消える。付けない。`sources/list.md` はアプリがゾーンの外を残すので、付けたければ付けてよい。

## ファイル → 所有者

| ファイル | owner |
| --- | --- |
| `me/taste.md` | cowork（app-managedゾーンあり） |
| `me/patterns.md` | cowork |
| `me/goals.md` | app |
| `days/YYYY-MM/facts.md` | app |
| `days/YYYY-MM/voice.md` | app |
| `days/YYYY-MM/summary.md` | cowork |
| `days/YYYY-MM/feedback.md` | app |
| `inbox/candidates.md` | cowork |
| `sources/list.md` | app（app-managedゾーンあり） |
| `sources/stats.md` | app |
| `sources/proposed.md` | app |
| `sources/dismissed.md` | app |
| `analysis/taste.md` | cowork |
| `cowork/rejected.md` | cowork（移動しない） |
