# AIR SPEED

回線速度を測るだけの自分用アプリ。開くと自動で測り始める。

- Download / Upload / Ping / Jitter / Idle latency の 5 つ
- 測定先は Cloudflare の公開測定サーバ
- 画面は index.html 1枚。GitHub Pages で配信
- 黒地に白。AIR HOME・AIR LAB と同じ系統

## 測り方

- **Download / Upload** … 下りは 4 本、上りは 3 本を同時に流して合計の流量で測る。
  1 本だけだと速い回線で本来の速度が出ない。回線は出だしが遅い（slow start）ので、
  立ち上がりの 2 秒を除いた区間の平均を結果にする。
  **測定中に出ている数字も同じ計算**なので、見ていた数字がそのまま結果になる。
- **Ping** … 小さいデータを 14 回往復させた中央値。1 回目は接続の準備が乗るので捨てる。
  サーバ側の処理時間（Server-Timing）は引いてある。
- **Jitter** … 測った順のまま、隣どうしの差の平均。往復の速さがどれだけバラつくか。
  通話やゲームの引っかかりはここに出る。
- **Idle latency** … Cloudflare のエッジが実測した TCP の最小往復（min_rtt）。
  混雑待ちや処理の上乗せが無かったときの値。**Ping との差が上乗せ分**として読める。

Built by iller with Claude — 2026
