---
title: ディストリビューション
description: フォークと混同されがちですが、ディストリビューションは、OpenTelemetryコンポーネントのカスタマイズバージョンです。
weight: 190
default_lang_commit: 21d6bf0
---

OpenTelemetryプロジェクトは、複数の[シグナル](../signals)をサポートする複数の[コンポーネント](../components)から構成されています。
OpenTelemetryの参照実装は以下の通りです。

- [言語固有の計装ライブラリ](../instrumentation)
- [コレクターのバイナリ](/docs/concepts/components/#collector)

どの参照実装も、ディストリビューションとしてカスタマイズできます。

## ディストリビューションとは何か

ディストリビューションとは、OpenTelemetryコンポーネントのカスタマイズバージョンです。
ディストリビューションは、アップストリームのOpenTelemetryリポジトリに、いくつかのカスタマイズを施したラッパーです。
ディストリビューションをフォークと混同しないでください。

ディストリビューションのカスタマイズには、以下のようなものがあります。

- 特定のバックエンドやベンダーの使用を容易にしたり、カスタマイズしたりするスクリプト
- バックエンド、ベンダー、エンドユーザーに必要なデフォルト設定の変更
- ベンダーまたはエンドユーザー固有の追加パッケージングオプション
- OpenTelemetryが提供する以上のテスト、パフォーマンス、セキュリティカバレッジ
- OpenTelemetryが提供する以上の追加機能
- OpenTelemetryが提供するより少ない機能

ディストリビューションは大まかに以下のカテゴリーに分類されます。

- **"ピュア（Pure）":** これらのディストリビューションは、アップストリームと同じ機能を提供し、100％互換性があります。
  カスタマイズは通常、使いやすさやパッケージングを向上させる形で行われます。
  これらのカスタマイズは、バックエンド、ベンダー、またはエンドユーザー固有のものです。
- **"プラス（Plus）":** これらのディストリビューションは、アップストリームの上に、追加コンポーネントによって追加機能を提供します。
  例としては、OpenTelemetryプロジェクトにアップストリームで提供して計装ライブラリやベンダーのエクスポーターなどがあります。
- **"マイナス（Minus）":** これらのディストリビューションは、アップストリームからの機能のサブセットを提供します。
  この例としては、OpenTelemetryコレクタープロジェクトにある計装ライブラリやレシーバー、プロセッサー、エクスポーター、拡張機能の削除などがあります。
  このようなディストリビューションは、サポートとセキュリティへの配慮を高めるために提供されることがあります。

## 誰がディストリビューションを作成できますか

誰でもディストリビューションを作成できます。
今日、いくつかの[ベンダー](/ecosystem/vendors/)が[ディストリビューション](/ecosystem/distributions/)を提供しています。
くわえて、エンドユーザーは[レジストリ](/ecosystem/registry/)にあるコンポーネントのうち、OpenTelemetryプロジェクトにアップストリームされていないものを使いたい場合、ディストリビューションの作成を検討できます。

## コントリビューターかディストリビューションか

この先を読み、あなた自身のディストリビューションを作成する方法を学ぶ前に、OpenTelemetryコンポーネントにあなたが追加しようと思うものが、誰にとっても有益で、それゆえ、参照実装に含まれるべきかどうか、検討してみてください。

- 「使いやすさ」のためのスクリプトは一般化できるか
- デフォルト設定への変更は、すべての人にとってより良い選択肢となり得るのか
- 追加のパッケージングのオプションは本当に特別なものか
- テスト、パフォーマンス、セキュリティのカバレッジは、参照実装でもうまくいくか
- あなたの追加機能が標準の一部となり得るかどうか、コミュニティに確認したか

## 独自のディストリビューションを作成する

### コレクター

独自のディストリビューションを作成する方法については、[『独自のOpenTelemetryコレクターディストリビューションの構築』](https://medium.com/p/42337e994b63)のブログ記事を参照してください。

独自のディストリビューションを構築する場合、[OpenTelemetry Collector Builder](https://github.com/open-telemetry/opentelemetry-collector/tree/main/cmd/builder)が良い出発点になるかもしれません。

### 言語固有の計装ライブラリ

計装ライブラリをカスタマイズするための言語固有の拡張メカニズムがあります。

- [Javaエージェント](/docs/zero-code/java/agent/extensions)

## ガイドラインを守ろう

ロゴや名称といったOpenTelemetryプロジェクトの付随物を配布物に使用する際は、[OpenTelemetry Marketing Guidelines for Contributing Organizations][guidelines]に沿っていることを確認してください。

OpenTelemetryプロジェクトは現時点ではディストリビューションを認証していません。
将来、OpenTelemetryはKubernetesプロジェクトと同様にディストリビューションやパートナーを認証するかもしれません。
ディストリビューションを評価する際には、そのディストリビューションを使用することがベンダーロックインにならないことを確認してください。

> ディストリビューションのサポートは、OpenTelemetryの作者ではなく、ディストリビューションの作者から提供されます。

[guidelines]: https://github.com/open-telemetry/community/blob/main/marketing-guidelines.md