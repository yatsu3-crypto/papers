# papers — やまもと皮膚科・漢方クリニック 論文ダイジェスト

姫路・やまもと皮膚科・漢方クリニック（皮膚科＋漢方・鍼灸）の医師が朝の診療前に iPhone で読む、PubMed 新着の日本語ダイジェスト。
院内アプリ本体（生活指導アシスタント等）は別リポジトリ `yatsu3-crypto/staff` にあり、ここは論文ダイジェストだけを置く。

## ファイル

- `papers.html` — ダイジェスト本体（単一 HTML）。GitHub Pages で `https://yatsu3-crypto.github.io/papers/papers.html` として公開。`index.html` はそこへのリダイレクト。
- `.claude/skills/paper-digest/SKILL.md` — 毎朝の更新手順書（正本）。PubMed E-utilities で検索し、`papers.html` の `DIGEST` 配列に追記する。補助スクリプトと検索式も同梱。
- 毎朝 6 時（日本時間）にクラウドルーティンが SKILL.md の手順を実行し、`papers.html` だけをコミットして `main` に push する。

## 技術ルール

1. `papers.html` は **単一 HTML ファイル**で完結させる（CSS・JS 内包、ビルドなし、npm なし）。
2. 外部依存は Google Fonts の `<link>` と PubMed へのリンクだけ。CDN・外部 API・fetch は禁止。
3. 保存は localStorage のみ（`papers_read_v1` / `papers_later_v1` / `papers_state_v1`）。`try/catch` で囲む。
4. iPhone 表示優先（390px 基準、375〜430px で崩れない）。見た目は `staff` リポジトリの washi-design スキル（和紙デザインシステム）に従う。
5. `papers.html` の HTML/CSS/JS 本体は変えない。日々の更新で触るのは `DIGEST` 配列と `DIGEST_UPDATED` だけ。
6. 対話中の git commit / push はユーザーに言われたときだけ。クラウドルーティン実行時は SKILL.md 手順 7 に従って `papers.html` のみコミット・push する。

## 患者個人情報の取り扱い（絶対禁止）

患者個人情報を含むファイルは絶対に読み書きしない。見つけても開かず、ユーザーに伝えて指示を待つ。このリポジトリに患者情報を置かない。

## 医療コンテンツ

要約は抄録に書かれている範囲のみ。Claude が独自に医学的判断を追加・変更しない。抄録のない論文はタイトルの範囲にとどめ「抄録なし・原著確認が必要」と注記する。丁寧語で、免責（最終判断は医師が行う）を保つ。
