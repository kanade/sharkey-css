# Sharkey用カスタムCSS

## お知らせ

## 更新履歴
<details><summary>クリックで展開できます</summary><div>

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
Misskeyユーザーはリアクションを使うことが多いので、いいねボタンを非表示にします
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
### テンプレ
```css
/**
 * 
 */

```

---

# 欲しいものリスト
[お役に立てましたらぜひ](https://www.amazon.jp/hz/wishlist/ls/2ZO0R36GVTG6M)  
