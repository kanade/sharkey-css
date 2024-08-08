# Sharkey用カスタムCSS

## お知らせ

## 更新履歴
<details><summary>クリックで展開できます</summary><div>

- 2024/08/08
  - いろいろ更新しました
- 2024/05/10
  - 各ノートのいいねボタンを消す（誤爆防止）
- 2024/04/22
  - 投稿日時に絶対時間表記にする
  - 公開範囲によって背景色を変える
  - 通知のポップアップを消す

</div></details>

## 目次
<details><summary>クリックで展開できます</summary><div>

- [Sharkey用カスタムCSS](#sharkey用カスタムcss)
  - [お知らせ](#お知らせ)
  - [更新履歴](#更新履歴)
  - [目次](#目次)
  - [説明](#説明)
  - [カスタムCSSの設定例](#カスタムcssの設定例)
    - [投稿日時に絶対時間表記にする](#投稿日時に絶対時間表記にする)
    - [公開範囲によって背景色を変える](#公開範囲によって背景色を変える)
    - [通知のポップアップを消す](#通知のポップアップを消す)
    - [各ノートのいいねボタンを消す（誤爆防止）](#各ノートのいいねボタンを消す誤爆防止)
    - [ブーストボタンを無効にする](#ブーストボタンを無効にする)
    - [通知インジケータの非表示](#通知インジケータの非表示)
    - [設定 → 絵文字ピッカーの絵文字サイズを拡大](#設定--絵文字ピッカーの絵文字サイズを拡大)
    - [リアクション選択およびノートで絵文字選択時の絵文字サイズを拡大](#リアクション選択およびノートで絵文字選択時の絵文字サイズを拡大)
    - [リアクション検索のボックスを上に固定](#リアクション検索のボックスを上に固定)
    - [返信元ノートをスクロール可能にする](#返信元ノートをスクロール可能にする)
    - [投稿フォームの要素順序並び替え](#投稿フォームの要素順序並び替え)
    - [デッキUI 編集サイドバーの非表示](#デッキui-編集サイドバーの非表示)
    - [デッキUIのポップアップ調整](#デッキuiのポップアップ調整)
    - [テンプレ](#テンプレ)
- [欲しいものリスト](#欲しいものリスト)

</div></details>

## 説明
MisskeyフォークのSharkey用カスタムCSSです。  
本家Misskey向けのカスタムCSSは適用できないものが多いため作りました。  
設定 → 全般 → カスタムCSSより設定することができます。  

Sharkeyはノートデザインを「Sharkey」と「Misskey」で選ぶことができます。（設定 → 全般 → Note Design）  
この関係で「Misskey」デザインでは動作しないカスタムCSSもあるかもしれません。  
その場合はご報告ください。  
動作確認は基本的に「Sharkey」デザインで行っています。  

Sharkeyの最新リリース版にて作成しています。  
動作しない場合はまずお使いのサーバーバージョンが最新かどうか確認してください。  
普段Sharkeyを利用していないため、確認していないページで不都合が生じる可能性があります。  
あくまで自己責任にてご使用くださいませ。

アップデートなどにより予告なく動作しなくなる、または表示が崩れることがあるかもしれません。  
その場合はカスタムCSSをなにも設定していない状態に戻してみてください。  
不具合報告は [`@kanade`](https://mfmf.club/@kanade) までお願いいたします。

さらに快適なMisskeyライフのお供になれれば幸いです。  

Stylusを使うとMisskeyの設定でいちいち変えなくても切り替えられるのでオススメです。  
- Chrome, Edgeなど  
https://chrome.google.com/webstore/detail/stylus/clngdbkpkpeebahjckkjfobafhncgmne?hl=ja  
- Firefox  
https://addons.mozilla.org/ja/firefox/addon/styl-us/  

---

## カスタムCSSの設定例

### 投稿日時に絶対時間表記にする

これについてはMisskey本家と同じCSSが適用できました。

```css
time {
    font-size: 0;
}
time:after {
    content: attr(title);
    font-size: 0.9rem;
}
```

---

### 公開範囲によって背景色を変える

分かりやすいよう極端な色設定になってるので好みで変更してください。

```css
/* 公開範囲によって背景色を変える */
/* 公開範囲がホームの投稿 */
.MkNotes-note-3762:has(.ph-house) {
    border: solid 1px rgba(135, 206, 250, 1);
    background-color: rgba(204, 255, 255, 0.3) !important;
    border-radius: 8px; /* これはお好みで */
}
/* 公開範囲がフォロワー限定の投稿 */
.MkNotes-note-3762:has(.ph-lock) {
    border: solid 1px rgba(221, 106, 221, 1);
    background-color: rgba(229, 204, 255, 0.3) !important;
    border-radius: 8px; /* これはお好みで */
}
/* 公開範囲がダイレクト(DM)の投稿 */
.MkNotes-note-3762:has(.ph-envelope) {
    border: solid 1px rgba(255, 255, 0, 1);
    background-color: rgba(255, 255, 204, 0.3) !important;
    border-radius: 8px; /* これはお好みで */
}
/* 公開範囲がホームの投稿作成時*/
.MkPostForm-modal-xtDg._popup:has(.ph-house) {
    border: solid 5px rgba(135, 206, 250, 1);
    background-color: rgba(204, 255, 255, 0.9) !important;
    border-radius: 8px; /* これはお好みで */
}
/* 公開範囲がフォロワー限定の投稿作成時*/
.MkPostForm-modal-xtDg._popup:has(.ph-lock) {
    border: solid 5px rgba(221, 106, 221, 1);
    background-color: rgba(229, 204, 255, 0.9) !important;
    border-radius: 8px; /* これはお好みで */
}
/* 公開範囲がダイレクトの投稿作成時*/
.MkPostForm-modal-xtDg._popup:has(.ph-envelope) {
    border: solid 5px rgba(255, 255, 0, 1);
    background-color: rgba(255, 255, 204, 0.9) !important;
    border-radius: 8px; /* これはお好みで */
}
```

---
### 通知のポップアップを消す
```css
/**
 * 通知のポップアップを消す
 */
.common-notifications-pjbG {
    display: none !important;
}
```

---
### 各ノートのいいねボタンを消す（誤爆防止）
Misskeyユーザーはリアクションを使うことが多いので、いいねボタンを非表示にしたいという需要に。
```css
/**
 * 各ノートのいいねボタンを消す（誤爆防止）
 */
.SkNote-footerButton-CAEP:has(.ph-heart) {
    display: none;
}
```

設定でデザインをMisskeyにしている人はこちら
```css
/**
 * 各ノートのいいねボタンを消す（誤爆防止）
 */
.MkNote-footerButton-viCy:has(.ph-heart) {
    display: none;
}
```

---
### ブーストボタンを無効にする
一発でブーストできちゃうので無効化する
```css
/**
 * ブーストボタンを無効にする
 */
.SkNote-footer-gqd7 button:has(.ph-rocket-launch) {
    pointer-events: none;
    /* 以下はボタンの親要素に適用しないと効かない */
    /*     cursor: not-allowed; */
}

```

---
### 通知インジケータの非表示
```css
/**
 * 通知インジケータの非表示
 */
.navbar-itemIndicator-xiU7 {
    display: none;
    /* スマホの場合は以下のように !important 付けないと消えないかも */
    /* display: none !important; */
}
```

---
### 設定 → 絵文字ピッカーの絵文字サイズを拡大
```css
/**
 * 設定 → 絵文字ピッカーの絵文字サイズを拡大
 */
.pages-settings-emoji-picker-emojis-iEIM .MkCustomEmoji-normal-5kTm,
.pages-settings-emoji-picker-emojis-iEIM .MkEmoji-root-agin
{
    height: 2.25em;
}
```

---
### リアクション選択およびノートで絵文字選択時の絵文字サイズを拡大
```css
/**
 * 
 */
.emojis .MkCustomEmoji-normal-5kTm {
    height: 2.25em;
}
```

---
### リアクション検索のボックスを上に固定
```css
/**
 * リアクション検索のボックスを上に固定
 */
.omfetrab > .search:not(.filled) {
    order: 0 !important;
}
```

---
### 返信元ノートをスクロール可能にする
スマホで引用やリプライするときに返信元が長すぎて入力できない問題に対処
```css
/**
 * 返信元ノートをスクロール可能にする
 */
.MkPostForm-targetNote-hv1G {
    height: 4em !important;
    overflow: scroll;
}
```

---
### 投稿フォームの要素順序並び替え
順番は好みに合せてください。数字が小さいほど上に来ます。
```css
/**
 * 投稿フォームの要素順序並び替え
 */
.MkPostFormDialog-form-xski {
    display: flex;
    flex-flow: column;
}
/* 添付ファイル */
.MkPostFormAttaches-root-j7LU {
    order: 1;
}
/* header */
.MkPostForm-header-6ccQ {
    order: 2;
}
/* ダイレクトの宛先 */
.MkPostForm-toSpecified-9eP3 {
    order: 3;
}
/* ダイレクトの宛先の警告 */
.MkPostForm-hasNotSpecifiedMentions-eg2G {
    order: 4;
}
/* 返信元 */
.MkPostForm-targetNote-hv1G {
    order: 3;
}
/* ツールバー（画像添付やアンケート、絵文字ピッカーなど） */
.MkPostForm-footer-kr7J {
    order: 6;
}
/* CW注意文の入力欄 */
.MkPostForm-cw-xQx9 {
    order: 7;
}
/* ノート本文の入力欄 */
.MkPostForm-textOuter-nEld {
    order: 9;
}
/* ハッシュタグ */
.MkPostForm-hashtags-qwIh {
    order: 10;
}
/* プレビュー */
.MkPostForm-preview-oGjR {
    order: 11;
}
```

---
### デッキUI 編集サイドバーの非表示
私はデッキ構成が済んだら非表示にしてます。
```css
/**
 * デッキUI 編集サイドバーの非表示
 */
.deck-sideMenu-ECNb {
    display: none;
}
```

---
### デッキUIのポップアップ調整
デフォだとポップアップが小さいので大きくしてます。  
最大化以外のサイズ調整ができなくなる副作用があります。
```css
/**
 * デッキUIのポップアップ調整
 */
/* デッキUIのポップアップ */
.MkWindow-root-pAOc:not(.MkWindow-maximized-wAht), /* 設定 */
.MkPostFormDialog-form-xski /* 投稿 */
{
    width: 40% !important;
    min-width: 480px;
    max-width: 1280px;
    height: 80% !important;
}

/* ノート入力ポップアップ */
.MkPostForm-modal-xtDg._popup {
    width: 40%;
    min-width: 480px;
    max-width: initial;
    height: 70vh;
    max-height: 70vh;
    top: 15%;
    overflow: scroll;
}

/* ノート入力欄 */
.MkPostForm-modal-xtDg._popup .MkPostForm-text-8B0D {
    height: 28vh;
}

/* ノートのプレビュー */
.MkPostForm-modal-xtDg._popup .MkPostForm-preview-oGjR {
    height: 28vh;
    overflow: scroll;
    max-height: initial !important;
}
```

---
### テンプレ
```css
/**
 * 
 */

```

---

# 欲しいものリスト
[お役に立てましたらぜひ](https://www.amazon.jp/hz/wishlist/ls/2ZO0R36GVTG6M)  
