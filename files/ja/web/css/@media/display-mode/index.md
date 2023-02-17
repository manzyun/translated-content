---
title: display-mode
slug: Web/CSS/@media/display-mode
---

{{CSSRef}}

[CSS](/ja/docs/Web/CSS) の **`display-mode`** [メディア特性](/ja/docs/Web/CSS/@media#メディア特性)は、アプリケーションの表示モードに基づいて選択的に CSS を適用するために使います。これは、サイトを URL から起動した場合とデスクトップアイコンから実行した場合の使い勝手に一貫性を持たせるために使用することができます。

この特性は、ウェブアプリマニフェストの [`display`](/ja/docs/Web/Manifest#display) メンバーに対応しています。これは、最上位の閲覧コンテキストと子の閲覧コンテキストの両方に適用されます。このクエリーは、ウェブアプリマニフェストの有無にかかわらず適用されます。

## 構文

`display-mode` 特性は、以下の一覧のうち一つのキーワード値で指定します。

| 表示モード | 説明                                                                                                                                                                                                                                                                                                            | 代替表示モード |
| ------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------- |
| `fullscreen` | 利用可能な表示領域がすべて使用され、ユーザーエージェントの{{Glossary("chrome", "クローム")}}は表示されません。   | `standalone`          |
| `standalone` | アプリケーションはスタンドアロンアプリケーションのような外観や操作感になります。これは、アプリケーションが個別のウィンドウを持ったり、アプリケーションランチャーに独自のアイコンを持ったりすることを含みます。このモードでは、ユーザーエージェントはナビゲーション制御のための UI 要素を除外しますが、ステータスバーなどその他の UI を含めることができます。 | `minimal-ui`          |
| `minimal-ui` | アプリケーションはスタンドアロンアプリケーションのような外観や操作感になりますが、ナビゲーション制御のための最小限の UI 要素を持ちます。要素はブラウザーによって異なります。                                                                                                                                            | `browser`             |
| `browser`    | アプリケーションは、ブラウザーとプラットフォームに応じて、従来のブラウザータブまたは新しいウィンドウで開きます。                                                                                                                                                                                                              | (なし)                |

## 例

### 端末が全画面モード時に使用される CSS

```css
@media all and (display-mode: fullscreen) {
  body {
    margin: 0;
    border: 5px solid black;
  }
}
```

## 仕様書

{{Specifications}}

## ブラウザーの互換性

{{Compat}}

## 関連情報

- [メディアクエリーの使用](/ja/docs/Web/CSS/Media_Queries/Using_media_queries)
- [@media](/ja/docs/Web/CSS/@media)