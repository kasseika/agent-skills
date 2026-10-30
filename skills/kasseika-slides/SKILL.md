---
name: kasseika-slides
description: 地活研（地域活性化総合研究所、kasseika.club）名義のスライド・発表資料を作るときのブランド規約（ロゴ・色・フォント・レイアウト・出典の書き方。画面用（paper 背景）と印刷用（白背景）の2版がある）。「地活研のスライド」「地活研名義で発表資料」「kasseika のデッキ」などの依頼や、地活研のロゴ・配色をスライドに入れる依頼で必ず使う。
---

# 地活研名義のスライド

地活研（地域活性化総合研究所）名義のスライドを作るときの規約である。ブランドの正本は kasseika.club（リポジトリ `kasseika/kasseika-svelte`、private）にあり、本スキルはそれをスライド向けにまとめたものである。正本と食い違う場合は正本を優先し、本スキルを直す。

## 1. ブランド要素

### 名称
- 略称: 地活研
- 正式名: 地域活性化総合研究所（表紙ではロゴの横に「地域活性化／総合研究所」の2行で添える）

### ロゴ
「地活研」のロゴタイプ（LINE Seed JP ExtraBold をアウトライン化した図形）と、右肩の椿色の角印でできている。図形を作り直したり、文字で代用したりしない。

- **正本**: `kasseika/kasseika-svelte` の `src/lib/brand/logo.ts`（`LOGO_TYPE_PATH`・`LOGO_SEAL`・`LOGO_COLORS`、viewBox は `21 82 3261 939`）
- **入手の順序**（上から試し、取れた時点で止める）
  1. `https://kasseika.club/brand/logo.svg`（墨色）・`logo-white.svg`（白抜き）・`logo.png`・`logo-white.png`（2400px幅の透過PNG）。2026-10-14 に4つとも200で配信されていることを確認した（PNG は 2400×691 の透過）。取得時は `curl -sL -o x -w '%{http_code}'` で200を確認し、`file` で中身がSVG/PNGであることを確かめる
  2. `gh api repos/kasseika/kasseika-svelte/contents/src/lib/brand/logo.ts -H "Accept: application/vnd.github.raw"` で正本を読む（`kasseika-svelte` は private なので、読む権限がない・`gh` に未ログインのときは次へ進む）
  3. 上の2つがどちらも取れないときだけ、本スキル同梱の `assets/logo.svg`・`assets/logo-white.svg` を使う。2026-10-14 に `logo.ts` と同じパスであることを確認した写しなので、使った場合は「同梱の写しを使った」とユーザーに伝える
- **色**: ロゴタイプは明るい背景では墨色 `#1b1e25`、濃い背景では白 `#ffffff`。角印は常に椿色 `#b3172b`
- 周囲に余白をとり、ロゴを変形・回転・着色しない

### 色（kasseika.club の CSS トークン）

| トークン | 値 | スライドでの用途 |
|---|---|---|
| paper | `#f3f4f2` | 全スライドの背景 |
| sheet | `#fbfbfa` | カード・表の地 |
| muted | `#e9ebe9` | サブの面（補足パネル） |
| ink | `#1b1e25` | 見出し・強い文字・ロゴタイプ |
| ink-soft | `#4b515c` | 本文 |
| grain | `#646b76` | 出典・注記など24pxの補足 |
| grain-soft | `#b6bcc4` | 区切り記号など弱い要素 |
| tsubaki | `#b3172b` | アクセント（番号・eyebrow・矢印・強調枠・表紙の帯） |
| tsubaki-deep | `#8e0f20` | 椿色の上に重ねる濃い色が必要なとき |
| sea | `#2f7482` | 2つ目のアクセント。椿色だけでは区別がつかない時に限って使う |

- 強調行・ピルの淡い地は椿色の淡色 `#f3dcdf`、罫線・弱い矢印は `#d3d6d3` を使う
- **すべてライト調にする**。黒・濃紺の全面背景は見づらいので使わない（表紙・区切り・まとめのスライドも、その版の背景色にする）
- 強調したい帯やカードは、濃い地ではなく「sheet の地（印刷用は白の地）＋椿色の枠（`border:2px solid #b3172b`、見出しカードは `border-top:8px solid #b3172b`）」で表す

### 版（画面用・印刷用）
スライドには2つの版がある。違いは背景・カードの地・出典行の書き方だけで、文字色・アクセント・フォント・ロゴは共通である。

| 項目 | 画面用（既定） | 印刷用 |
|---|---|---|
| 用途 | プロジェクター・画面共有・PDF配布 | 紙に印刷して配る・掲示する |
| スライドの背景 | paper `#f3f4f2` | 白 `#ffffff` |
| カード・表の地 | sheet `#fbfbfa` | 白 `#ffffff`＋罫線 `border:1px solid #d3d6d3`（白地の上では sheet が見分けられないため） |

- 印刷用でも、椿色の枠・帯・淡色 `#f3dcdf`・muted `#e9ebe9` はそのまま使う
- 印刷用で白 `#ffffff` を使うのは、背景とカードの地だけにする
- 印刷用では紙の上でリンクを押せないため、出典行の `<a href>` は残したまま、リンク文字の後ろに URL を文字でも書く（例: `出典：<a href="https://www.example.go.jp/report">資料名</a>（https://www.example.go.jp/report、日付）`）。URL が長く1行に収まらない場合は、ドメインと資料名で探せる程度まで短くしてよい

### フォント
- 見出し・本文・数字ともに **LINE Seed JP**（Google Fonts）。kasseika.club と同じ
- Google Fonts の指定: `https://fonts.googleapis.com/css2?family=LINE+Seed+JP:wght@400;700;800&display=swap`
- 太さは 400（本文）・700（見出し・強調）・800（大きな数字）だけを使う。600 は存在しないので指定しない
- LINE Seed JP は数字の字幅が広い。大きな数字を3列のカードに並べるときは 112px 程度までに抑える

## 2. Slides アーティファクトでの実装

デッキは Artifact の Slides 型で作る（`quickstart` → 型の指示に従う）。デザインシステムは使わず、本スキルの色とフォントを自前で指定する。

### 作成前に版を確かめる
スライドを書き始める前に、画面用と印刷用のどちらで作るかをユーザーに聞く（`AskUserQuestion` が使えるならそれで、選択肢は「画面用（既定）」「印刷用（白背景）」）。依頼文に「印刷」「紙で配る」「白背景」などがあれば印刷用、「投影」「画面共有」などがあれば画面用と決めてよく、その場合は聞かずに、どちらで作るかを返答で知らせる。

### deck.json の faces
```json
"faces": {"line-seed-jp": {"family": "LINE Seed JP", "href": "https://fonts.googleapis.com/css2?family=LINE+Seed+JP:wght@400;700;800&display=swap"}}
```

### セクションの基本形
```html
<section id="…" data-transition="fade" style="position:relative;background:#F3F4F2;color:#1B1E25;font-family:'LINE Seed JP', sans-serif;padding:128px 128px 160px;display:flex;flex-direction:column;gap:48px">
<div style="display:flex;flex-direction:column;gap:16px">
<p style="font-size:24px;font-weight:700;color:#B3172B;letter-spacing:4px">01 パート名</p>
<h2 style="font-size:64px;font-weight:700;line-height:1.2">見出し</h2>
</div>
…本文…
<p style="position:absolute;left:128px;bottom:64px;width:1600px;font-size:24px;color:#646B76">出典：<a href="https://…">資料名</a>（日付）</p>
（ロゴ）
<aside>スピーカーノート</aside>
</section>
```
- 印刷用では `background:#F3F4F2` を `background:#FFFFFF` に替える
- 文字の大きさは 96（表紙）／64（見出し）／40前後（カード見出し）／26〜32（本文）／24（補足・出典）の段階で使う
- 見出しは ink（`#1B1E25`）、本文の段落は ink-soft（`color:#4B515C`）にする
- カードは `background:#FBFBFA;border-radius:8px`（印刷用は `background:#FFFFFF;border:1px solid #D3D6D3;border-radius:8px`）、番号は `color:#B3172B;font-weight:800`

### ロゴの置き方
Slides 型は外部URLの画像を使えないため、ロゴは **インライン `<svg>`** で入れる（SVG は viewBox の原点を0にずらして埋め込む）。`{PATH}` は入手したロゴの `<path>` の `d` 属性（`logo.svg` はロゴタイプの `<path>` 1つと角印の `<rect>` 1つでできている。`logo.ts` から取った場合は `LOGO_TYPE_PATH`）、`{FILL}` は明るい背景なら `#1B1E25`。角印の `<rect>` の位置と大きさは入手したロゴ（`logo.ts` なら `LOGO_SEAL`）に合わせ、下の雛形の値と違えば書き換える。

- **表紙**（左上、ロゴ＋正式名）
```html
<div style="position:absolute;left:128px;top:96px;width:720px;display:flex;align-items:center;gap:28px"><svg role="img" aria-label="地活研 ロゴ" width="3261" height="939" viewBox="0 0 3261 939" style="width:250px;height:72px"><g transform="translate(-21 -82)"><path fill="{FILL}" d="{PATH}"></path><rect fill="#B3172B" x="2982" y="82" width="300" height="300"></rect></g></svg><div style="display:flex;flex-direction:column;gap:6px;padding-left:28px;border-left:2px solid #4B515C"><p style="font-size:24px;font-weight:700;letter-spacing:2px;line-height:1.2">地域活性化</p><p style="font-size:24px;font-weight:700;letter-spacing:2px;line-height:1.2">総合研究所</p></div></div>
```
- **本文スライド**（右上、ロゴのみ）
```html
<div style="position:absolute;right:128px;top:52px;width:146px;height:42px"><svg role="img" aria-label="地活研 ロゴ" width="3261" height="939" viewBox="0 0 3261 939" style="width:146px;height:42px"><g transform="translate(-21 -82)"><path fill="{FILL}" d="{PATH}"></path><rect fill="#B3172B" x="2982" y="82" width="300" height="300"></rect></g></svg></div>
```
- 長いパスを各スライドに手で書き写さない。スライドには `@@LOGO@@` のような目印を置き、ロゴの行を1か所で作って差し込む（写し間違いを防ぐ）
- PPTX など別形式で画像のロゴが必要な場合は、`logo.png`（または SVG を PNG に変換したもの）を Artifact の asset としてアップロードし、返ってきた `/_blob/…` を `<img src>` に使う

### 表紙
- 左端に椿色の帯（`position:absolute;left:0;top:0;width:24px;height:1080px;background:#B3172B`）、左上にロゴ＋正式名
- 下部に「YYYY年M月 ／ 発表者名」。発表者名が分からなければユーザーに確認する（未確定なら `[発表者名]` を置き、返答で知らせる）

## 3. 内容の規約
- 事実・数字には出典を付け、**リンクできる出典は `<a href>` でリンクする**（スライド下部の出典行）。リンク先は実際に確認したページにする
- 数字は一次情報（論文・公式発表）で確かめる。報道や二次情報しかない場合は、その旨を出典に書く
- 推測や講演者の提案は、出典行かノートに「本講演の提案」「（推測）」と明記する
- 攻撃者の帰属や原因が未確定の事案は、断定せず「公的な特定はない」等と書く
- 各スライドにスピーカーノート（`<aside>`）を付け、話す内容と根拠の補足を書く
- 対象者に合わせて用語をかみ砕く（例: 中小企業のDX担当者向けなら専門用語に一言の説明を添える）

## 4. 公開前のチェック
- [ ] 作成前に版（画面用・印刷用）を確かめた
- [ ] 全スライドの背景が、画面用なら paper（`#F3F4F2`）、印刷用なら白（`#FFFFFF`）にそろっていて、黒・濃紺の全面背景がない
- [ ] 印刷用では、カードが白地＋罫線（`#D3D6D3`）で、sheet（`#FBFBFA`）が残っていない
- [ ] 色は第1節の値（色の表、その下の淡色・罫線の2色、印刷用の白）だけを使っている
- [ ] faces は LINE Seed JP の1件で、`font-weight:600` が残っていない
- [ ] 表紙にロゴ＋正式名、本文スライドの右上にロゴがある。角印が椿色である
- [ ] 出典行のリンクが張られている（印刷用では URL も文字で書いてある）
- [ ] 発表者名・日付が入っている（未確定のものはユーザーに伝えた）
- [ ] `[発表者名]` などの角括弧の仮置きが残っていない（残す場合は、そのまま公開してよいかユーザーの了承を得た）
