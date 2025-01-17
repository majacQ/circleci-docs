---
layout: classic-docs
title: "ワークフロー"
short-title: "ワークフロー"
description: "ワークフローの説明"
categories:
  - workflows
order: 2
version:
  - Cloud
  - Server v2.x
---

CircleCI [Workflows]({{ site.baseurl }}/2.0/workflows/) enable you to introduce concurrency and sequence your job runs with great flexibility for faster feedback when jobs fail.

<hr />

| ジョブの手動承認                                                                                                     | フィルターの使用                                                                                                                                                                                                                            |
| ------------------------------------------------------------------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [承認ジョブ]({{ site.baseurl }}/2.0/workflows/#手動承認後に処理を続行するワークフロー)を追加して手動ゲートをセットアップします。 &nbsp;&nbsp;&nbsp;&nbsp; | [正規表現]({{ site.baseurl }}/ja/2.0/workflows/#正規表現を使用してタグとブランチをフィルタリングする)を使用して、[ブランチでフィルタリング]({{ site.baseurl }}/2.0/workflows/#ブランチレベルブランチの配下でジョブを実行する)または[タグでフィルタリング]({{ site.baseurl }}/2.0/workflows/#git-タグに対応するワークフローを実行する)します。 |

<hr />

| ワークフローのスケジュール実行                                                                                                      | ワークスペースの使用                                                                             |
| -------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------- |
| `cron` で設定された[スケジュールに基づいてワークフローをトリガー]({{ site.baseurl }}/2.0/workflows/#ワークフローのスケジュール実行)します。&nbsp;&nbsp;&nbsp;&nbsp; | [ワークスペース]({{ site.baseurl }}/2.0/workflows/#ワークスペースによるジョブ間のデータ共有)を使用して、ジョブ間でデータを共有します。 |

<hr />

## ビデオ: ワークフローに複数のジョブを構成する

以下のビデオでは、`.circleci/config.yml` ファイルでワークフローを構成する方法を説明しています。

<div class="video-wrapper">
<iframe width="560" height="315" src="https://www.youtube.com/embed/3V84yEz6HwA" frameborder="0" allow="autoplay; encrypted-media" allowfullscreen mark="crwd-mark"></iframe>
</div>

## Possible Workflow States

ワークフローのステータスには以下の種類があります。

- RUNNING: ワークフローが実行中
- NOT RUN: ワークフローが起動されていない
- CANCELLED: ワークフローが終了前にキャンセルされた
- FAILING: ワークフロー内の 1 つのジョブが失敗
- FAILED: ワークフロー内の 1 つ以上のジョブが失敗
- SUCCESS: ワークフロー内のすべてのジョブが正常に完了
- ON HOLD: ワークフロー内のジョブが承認を待機中
- NEEDS SETUP: このプロジェクトの `config.yml` ファイル内に workflow スタンザが含まれていない、または正しくない