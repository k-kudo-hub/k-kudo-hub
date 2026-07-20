# GitHubプロフィールREADMEへの追加パーツ導入

## 概要

前回の刷新でミニマルにしすぎたため、著名なOSSコミッターのプロフィール事例（[awesome-github-profile-readme](https://github.com/abhisheknaiidu/awesome-github-profile-readme)等）を参考に、外部の壊れやすい動的サービスに依存しない追加パーツを導入する。

## TODO

- [x] 「Currently working on」セクションをREADME.mdに追加する（SRE・オブザーバビリティ中心、職種・経験年数は記載するが実名・会社名は伏せる）
- [x] 「Connect」セクションをREADME.mdに追加する（X: https://x.com/Cut_kf、shields.io新規バッジ生成が失敗するためMarkdownリンクを採用）
- [x] `.github/workflows/snake.yml` を作成する（Platane/snkでcontribution snakeアニメーションを生成しoutputブランチへpush）
- [x] README.mdにcontribution snakeアニメーションの埋め込み（ダークモード対応の`<picture>`タグ）を追加する
- [x] ワークフローファイルのYAML構文が正しいことを確認する
- [x] README.md内の新規追加リンク・バッジURLが正常にレンダリングされることをcurlで確認する
- [ ] コミットする

## 完了条件

- README.mdに「Currently working on」「Connect」「Contribution snake animation」セクションが追加されている
- 実名・会社名がREADMEに含まれていない
- 追加した全てのバッジ・リンクURLがHTTP 200を返す
- snake.ymlのYAML構文が妥当である

## 備考

- ハイライトプロジェクト紹介セクションはユーザー判断により今回は見送り
- LAPRAS（https://lapras.com/public/k）は内容取得不可（タイトルのみ）だったため、Wantedly（https://www.wantedly.com/id/k_kudo）から得た情報を採用した
  - Wantedlyから判明した事実: フルスタックエンジニア3年 + SRE3年、計6年のWebエンジニアリング経験。SREとして監視ツール導入・SLI/SLO設定・パフォーマンス改善・New Relic活用の実績あり
  - 実名「藤森和人」・勤務先「株式会社エアークローゼット」はユーザー判断によりREADMEに含めない
  - 「Currently working on」の具体的な文言はWantedly情報からの推測であり、ユーザーが後から自由記述で修正可能
- snake.ymlはPawdroid/Pawdroidリポジトリの実例（GitHub Code Search経由で実在を確認済み）をベースに、ブランチ名を本リポジトリのデフォルトブランチ`main`に合わせて作成する
- contribution snakeのSVGはGitHub Actions実行後に`output`ブランチへ生成されるため、マージ・ワークフロー実行前はREADME上の画像がリンク切れになる。これはユーザーに事前共有済みの制約とする
