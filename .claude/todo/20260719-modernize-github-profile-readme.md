# GitHubプロフィールREADMEのモダン化

## 概要

`github-readme-stats.vercel.app`（503 Service Unavailable / DEPLOYMENT_PAUSED）、`github-profile-trophy.vercel.app`（402 Payment Required）、後継の`github-stats-extended.vercel.app`（リソース制限エラー）と、公開インスタンス依存の動的ウィジェットが軒並み機能停止しており表示が崩れている。2026年のトレンド（シグナル重視のミニマル構成、壊れやすい外部動的SVGへの依存を避ける）に沿ってREADMEを刷新する。

## TODO

- [x] 現状のバッジ・動的ウィジェットのURL動作確認結果を記録する（確認済み、備考参照）
- [x] 新しい技術スタックバッジ（TypeScript, JavaScript, Ruby, Next.js, Nest.js, MySQL, Redis）をshields.ioのモダンなスタイル（flat-square）で作成する
- [x] 壊れている`github-readme-stats`セクションを削除する
- [x] 壊れている`github-profile-trophy`セクションを削除する
- [x] 自己紹介文をミニマルな構成に見直す（1行の自己紹介＋技術スタック＋連絡先程度に整理）
- [x] 新しいREADME.md内の全ての画像URL・リンクURLが正常にレンダリングされることをWebFetch/curlで確認する
- [ ] README.mdをコミットする

## 完了条件

- README.mdに含まれる全ての画像URLが正常なレスポンス（SVG/PNG）を返し、リンク切れがない
- `github-readme-stats`・`github-profile-trophy`など壊れている公開インスタンスへの依存が存在しない
- バッジがTypeScript, JavaScript, Ruby, Next.js, Nest.js, MySQL, Redisの技術スタックを反映している

## 備考

- 動的統計・トロフィーセクションはユーザー承認により「ミニマルに刷新」する方針（自己ホストはしない）
- 事前調査で判明した実際のHTTPステータス:
  - `github-readme-stats.vercel.app` → 503 (DEPLOYMENT_PAUSED)
  - `github-profile-trophy.vercel.app` → 402 (Payment Required)
  - `github-stats-extended.vercel.app`（後継） → 200だがリソース制限エラーのSVGを返す
- PostgreSQLバッジはshields.ioで新規（未キャッシュ）生成が最大60秒待っても完了しないことを複数回確認したため、ユーザー承認によりREADMEに含めず保留する
- README.mdは単一Markdownファイルのためテストコードは存在せず、TDDの代わりに画像URLの実HTTP確認を検証ステップとする
- 最終確認: README.md内の全画像URL・リンクURLがHTTP 200を返すことをcurlで確認済み（TypeScript, JavaScript, Ruby, Next.js, NestJS, MySQL, Redisバッジ、GitHubプロフィールリンク）
