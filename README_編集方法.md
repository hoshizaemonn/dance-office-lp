# Dance Office LP 編集方法

スマホ1カラムのLPです。ファイル構成は次のとおりです。

```
dance-office-LP/
├── index.html        … ページ本体（デザイン・文章）
├── schedule.js       … レッスンスケジュール（ここだけ書き換えればOK）
├── assets/           … 写真・画像・動画
└── README_編集方法.md … この説明書
```

編集は「メモ帳」「テキストエディット」などのテキストエディタで行えます。
保存するときの文字コードは **UTF-8** のままにしてください。

---

## 1. レッスンスケジュールを打ち替える（schedule.js）

`schedule.js` を開くと、校舎ごとにスケジュールが並んでいます。

```js
{
  id: "tagawa",
  name: "田川校",
  days: [
    { day: "MON", classes: [
        ["MAOジュニア中級", "18：50〜19：50"],
        ["MAOジュニア上級", "20：00〜21：00"],
    ] },
    ...
  ],
},
```

| やりたいこと | 方法 |
|---|---|
| クラス名・時間を変える | `["クラス名", "時間"]` の中の文字を書き換える |
| クラスを増やす | `["クラス名", "時間"],` の行をコピーして追加する |
| クラスを減らす | その行を削除する |
| 曜日を増やす | `{ day: "SUN", classes: [ ... ] },` のブロックを追加する |
| 休みの曜日 | その曜日のブロックごと削除する |
| 最初に開く校舎を変える | 上のほうの `initial: "iizuka"` を `tagawa` / `nogata` / `miyawaka` に変える |

注意点

- クラス名と時間の間の「・・・」は **自動で入ります**。データには書かないでください。
- `"`（ダブルクォーテーション）と `,`（カンマ）を消さないようにしてください。消えると表が表示されなくなります。
- 行数が増減しても、枠の高さとその下のレイアウトは自動で追従します。
- 4校ともデザインデータ(.ai)に記載の時間割を原文のまま入れています（2026-09-29）。

---

## 2. 動画を差し替える

TOPの「無料体験受付中」ボタンのすぐ下に、16:9 の動画枠があります。

1. 動画を **MP4形式（H.264）・横長16:9** で書き出す
2. ファイル名を **`top.mp4`** にする
3. `assets/` フォルダに入れる

これだけで再生されます（音なし・自動再生・ループ・再生ボタン付き）。

- `top.mp4` が無い間は、`assets/video-poster.jpg`（ステージ写真）が表示されます。
- 動画の最初に表示する画像を変えたい場合は、`assets/video-poster.jpg` を同じ名前で上書きしてください（1280×720px 推奨）。
- 容量の目安は **10MB以下**。重いとスマホでの表示が遅くなります。
- 100MBを超えるファイルは置けません。

---

## 3. インストラクター写真を差し替える

インストラクターは横スライド（9名・自動送り3.5秒・指で左右にスワイプ可）です。
**SHOICHI / YUAN / MIKOTO / YUA / HANA の5名は、デザインデータと同じく他の方の写真を仮で入れています。** 必ず本人の写真に差し替えてください。
Instagram枠の画像は `assets/instagram-tagawa-nogata.jpg` / `instagram-iizuka.jpg` / `instagram-miyawaka.jpg`（2026-09-29時点のプロフィール画面）。同名で上書きすると差し替わります。

`assets/` の中の次のファイルを、**同じファイル名で上書き** してください。

| インストラクター | ファイル名 | 推奨サイズ（縦長） |
|---|---|---|
| HARUKA | `assets/instructor-haruka.jpg` | 518 × 1021 px |
| SUKE | `assets/instructor-suke.jpg` | 424 × 1224 px |
| MAO | `assets/instructor-mao.jpg` | 518 × 1196 px |
| TOGO | `assets/instructor-togo.jpg` | 298 × 861 px（650 × 1870 px 程度まで大きくしてOK） |
| SHOICHI（★仮の写真） | `assets/instructor-shoichi.jpg` | 520 × 1200 px 程度 |
| YUAN（★仮の写真） | `assets/instructor-yuan.jpg` | 520 × 1200 px 程度 |
| MIKOTO（★仮の写真） | `assets/instructor-mikoto.jpg` | 520 × 1200 px 程度 |
| YUA（★仮の写真） | `assets/instructor-yua.jpg` | 520 × 1200 px 程度 |
| HANA（★仮の写真） | `assets/instructor-hana.jpg` | 520 × 1200 px 程度 |
| SHOICHI | `assets/instructor-shoichi.jpg` | 298 × 861 px（650 × 1870 px 程度まで大きくしてOK） |
| YUAN | `assets/instructor-yuan.jpg` | 298 × 861 px（650 × 1870 px 程度まで大きくしてOK） |
| MIKOTO | `assets/instructor-mikoto.jpg` | 298 × 861 px（650 × 1870 px 程度まで大きくしてOK） |
| YUA | `assets/instructor-yua.jpg` | 298 × 861 px（650 × 1870 px 程度まで大きくしてOK） |
| HANA | `assets/instructor-hana.jpg` | 298 × 861 px（650 × 1870 px 程度まで大きくしてOK） |
| D.D（ゲスト） | `assets/guest-dd.jpg` | 600 × 700 px 程度 |

- 形式は JPG。縦横の比率が違っても、枠に合わせて自動で中央を切り抜いて表示します（顔が上寄りに来る写真が収まりやすいです）。
- 1枚あたり **300KB以下** を目安に、書き出し時に圧縮してください。
- **名前の文字（HARUKA / HIPHOP / GIRLS など）は画像です**（`assets/name-haruka.png` など）。インストラクターが入れ替わる・ジャンル表記を変える場合は、名札画像の作り直しが必要なので制作側へご連絡ください。
- ゲストインストラクターの右側の白い枠は、2人目用の空き枠です（デザインデータで空欄）。

---

## 4. スタジオ写真を差し替える

現在4校とも同じ写真が入っています（デザインデータの状態のまま）。
各校の写真が用意できたら、次のファイルを同じ名前で上書きしてください（横長 812 × 577 px 推奨）。

- `assets/studio-tagawa.jpg`
- `assets/studio-nogata.jpg`
- `assets/studio-iizuka.jpg`
- `assets/studio-miyawaka.jpg`

---

## 5. まだ決まっていない項目（決まり次第 index.html を書き換え）

| 項目 | 現状 | 書き換える場所 |
|---|---|---|
| Instagram のURL（3アカウント） | 設定済み（田川・直方 dance_office_do ／ 飯塚 danceofficeglow_ ／ 宮若 danceoffice_miyawaka） | `index.html` の `data-instagram=` が付いた行の `href` を書き換え |
| Instagram枠の中の画像 | グレーの空枠 | 同じ行の `<span class="sns-thumb"></span>` を `<span class="sns-thumb" style="background-image:url(assets/ファイル名.jpg)"></span>` に |
| 無料体験・お問い合わせボタンのリンク先 | 仮でページ最下部（`#contact`）へ移動 | `index.html` の `href="#contact"`（3か所）をフォームのURLに |
| 右上の三本線メニュー | 見た目のみ（開閉なし） | ― |

電話番号は `tel:080-3731-8442` でタップ発信できるようになっています。

---

## 6. 補足（制作者向け）

- 寸法はすべてカンプ（幅300pt）基準。CSS変数 `--u` が「カンプの1pt」で、画面幅に比例して拡縮します。PCで見た場合は幅480pxで中央固定、左右は黒です（PC版カンプはありません）。
- 本文は HTMLテキスト（新ゴが端末にあれば新ゴ、無ければ Noto Sans JP）。ロゴ・大見出し・英字見出し・手書き文字・名札は、Web配布できないフォントのためカンプから書き出した透過PNGです。
- 破れ紙の境界・カードの形は、カンプのベクターデータをそのまま SVG にしています。
- URLの末尾に `?parity=1` を付けると動画枠を隠し、カンプと同じ高さで表示します（カンプとの突き合わせ確認用）。
- スケジュール枠内の「曜日ブロック間のアキ」と「曜日バッジの上下位置」はカンプの実測値をそのまま再現しています（カンプ上で不揃い）。揃えたい場合は `index.html` の `.day:nth-child(n)` の指定を削除すると均等になります。
