# wrpocket-videos-runner

[Wild Rift Pocket](https://wrpocket.app) の 「新着動画」 を 3 時間ごとに取り込むためだけのリポジトリです。
ここには workflow しか置いていません。 取り込みのコードは非公開のリポジトリから読み込みます。

- 起動: Cloudflare Worker (wrpocket-rank-watcher) が 3 時間ごとに repository_dispatch (`videos-live`) を送る。
  手動なら Actions の 「Run workflow」
- 処理: YouTube の RSS と Data API (videos.list) で新着を取り、 振り分けた一覧を Cloudflare KV に書く
- 公開リポジトリにしている理由: 非公開リポジトリの Actions の無料枠 (月 2,000 分) が足りないため。
  公開リポジトリの Actions は実行時間の制限が無い

secret (値はここには書かない): `PRIVATE_REPO_TOKEN` (非公開リポジトリの読み取り専用)、 `YOUTUBE_API_KEY`、
`CLOUDFLARE_API_TOKEN`、 `CLOUDFLARE_ACCOUNT_ID`
