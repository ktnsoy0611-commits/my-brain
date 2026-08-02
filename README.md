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
- 各ファイルの先頭に front matter を付ける。

  ```
  ---
  owner: app / cowork / human
  updated: YYYY-MM-DD
  ---
  ```

  - `app`：アプリが書く
  - `cowork`：Coworkが書く
  - `human`：私が手で書く

  owner の違うファイルは互いに上書きしない。

- 1ファイルを共同編集するのは `me/taste.md` と `sources/list.md` だけ。
  アプリはファイル内の `<!-- BEGIN app-managed:... -->` と `<!-- END app-managed:... -->` で囲まれたゾーンの内側だけを書き換える。ゾーンの外側は他の owner が自由に編集してよい。
