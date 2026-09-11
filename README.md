# hdbench.github.io

HDBENCH.NET の GitHub Pages サイト。本家は https://www.hdbench.net/

複数のアプリが同居する前提の構成にしている。アプリはそれぞれ専用のフォルダを持つ。

## 構成

```
/                      トップ（ソフトウェア一覧）
/style.css             全ページ共通のスタイル
/app-ads.txt           広告の認証済み販売者リスト（ドメイン全体で共有）
/<アプリ名>/            アプリごとのフォルダ。URL は https://hdbench.github.io/<アプリ名>/
    index.html         紹介・サポートページ
    icon.svg           アプリのアイコン
    privacy/           プライバシーポリシー（新しいアプリはここに置く）
```

- 静的 HTML のみ。Jekyll は使わない（`.nojekyll`）
- リンクと画像は相対パスで書く。ローカルでファイルを開いても表示を確認できるようにするため
- フォルダ名は小文字の英字にする（例: `motroxia`、`wavoxia`）

### 例外: Motroxia のプライバシーポリシー

Motroxia のプライバシーポリシーは別リポジトリ（HDBENCH/motroxia-privacy）にあり、
https://hdbench.github.io/motroxia-privacy/ で公開している。
この URL はストアの掲載情報とアプリ本体に登録済みなので、移動しないこと。

## アプリの配色

共通の `style.css` にはアプリ固有の色を持たせない。
色は各アプリの `index.html` の `<style>` で変数として指定する。

| 変数 | 用途 |
|---|---|
| `--app-hero-bg` | ページ先頭の帯の背景色。文字は白系で固定なので暗い色にする |
| `--app-accent` | キャッチコピーとストアボタンの色 |
| `--app-accent-ink` | ストアボタンの文字色 |

指定しなければシリーズの配色（黒地に #00FF88）になる。
Motroxia と Wavoxia はアイコンの配色をそろえてあり、並べたときにシリーズと分かるようにしている。

## アプリを追加する手順

1. 既存のアプリのフォルダ（例: `motroxia/`）をコピーして `<アプリ名>/` を作る
2. `index.html` の配色の変数、名前、説明、ストアへのリンク、動作環境、FAQ、問い合わせ先を書き換える
3. `icon.svg` を差し替える（アプリの `Resources/AppIcon` の SVG から作る）
4. プライバシーポリシーを `<アプリ名>/privacy/index.html` に置く
5. トップの `index.html` にカードを追加する（「アプリを追加するときは」のコメントの位置）
6. ストアのデベロッパーサイト（App Store はマーケティングURL）を `https://hdbench.github.io/<アプリ名>/` にする
7. 広告を使う場合: 同じ AdMob アカウントなら `app-ads.txt` の変更は不要

## app-ads.txt を消さない・変更しない

`app-ads.txt` は AdMob の「認証済み販売者」の確認に使われている。
ストアのデベロッパーサイトがこのドメインを指すアプリすべてに効くため、
ファイルが無くなったり内容が変わったりすると、そのアプリの広告配信が制限される。
