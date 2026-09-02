# mahiro-site

砂鉄ホバーのヒーローだけを持った、最小構成の Astro サイト。

## ローカルで動かす

```
npm install
npm run dev
```

http://localhost:4321 が開く。

## 公開して URL を得る

1. GitHub で空のリポジトリを作る（例: `mahiro-site`）。README は入れない
2. このフォルダで:

```
git init
git add .
git commit -m "hero: 砂鉄ホバー"
git branch -M main
git remote add origin https://github.com/<ユーザー名>/mahiro-site.git
git push -u origin main
```

3. vercel.com にログイン → Add New → Project → 上のリポジトリを選ぶ
   フレームワークは Astro が自動検出される。設定はそのままで Deploy
4. `https://mahiro-site-xxxx.vercel.app` が発行される

以後 `git push` するたびに自動で再デプロイされる。

## 調整するところ

`src/pages/index.astro` の `<FilingsHero />` の props。

| prop | 既定値 | 意味 |
|---|---|---|
| `name` | mahiro kobayashi | 中央に出す名前。h1 として DOM にも存在する |
| `meta` | visual design — tokyo | 左上の小さい行 |
| `count` | 4200 | 砂鉄の粒の数 |
| `grain` | 0.9 | 粒の一辺（px） |
| `speed` | 0.6 | 集まりきるまでの体感秒数 |
| `range` | 520 | 引力が届く距離（px） |
| `mode` | edge | `edge` = 文字のふちに溜まる / `fill` = 文字の内側も埋める |

## 決まっていること

- 地 `#F0F5FA`（N100）、粒と文字 `#232332`（N800）
- 文字はカンバスに描いているが、`h1` は DOM 上に実在する（SEO・読み上げ用）
- `prefers-reduced-motion: reduce` のときはアニメーションを止め、素のテキストとして表示する
- JS が動かない環境でも名前は読める

## まだ決まっていないこと

- 書体（いまはシステムフォント）
- リロードのたびに粒の配置が変わる。これを許容するかどうか
- 粒が多いと低スペック機で重い。将来的には WebGL に寄せる
