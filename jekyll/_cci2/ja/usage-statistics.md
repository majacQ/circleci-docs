---
layout: classic-docs
title: "使用状況統計の利用"
category:
  - administration
order: 1
description: "CircleCI 2.0 の静的インストール スクリプトの使用"
hide: true
---

システム管理者を対象に、使用状況統計の集計結果を CircleCI に自動送信する方法について、以下のセクションに沿って説明します。

* 目次
{:toc}

使用状況統計データを活用すれば、CircleCI Server の可視性が向上するだけでなく、サポートが強化され、CircleCI 1.0 から CircleCI 2.0 への移行がスムーズに行えます。

Replicated の管理コンソールで [Settings (設定)] > [Usage Statistics (使用状況統計)] に移動し、この機能をオプトインします。 次に、以下のスクリーンショットに示すように、[Automatically send some usage statistics to CircleCI (使用状況統計を自動的に CircleCI に送信)] チェックボックスをオンにします。

![]({{ site.baseurl }}/assets/img/docs/usage-statistics-setting.png)

## Detailed usage statistics

以下のセクションでは、この設定を有効にした場合に CircleCI が収集する使用状況統計に関する情報を提供します。

### Weekly account usage

| **名前**                | **タイプ** | **目的**                                |
| --------------------- | ------- | ------------------------------------- |
| account_id            | UUID    | *各 vcs アカウントを一意に識別します。*               |
| usage_current_macos | 分       | *各アカウントについて、1 週間で実行されたビルドを分単位で記録します。* |
| usage_legacy_macos  | 分       |                                       |
| usage_current_linux | 分       |                                       |
| usage_legacy_linux  | 分       |                                       | 
{: class="table table-striped"}

### Weekly job activity

| **名前**                                 | **タイプ** | **目的**                                                            |
| -------------------------------------- | ------- | ----------------------------------------------------------------- |
| utc_week                               | 日付      | *以下のデータが適用される週を識別します。*                                            |
| usage_oss_macos_legacy               | 分       | *1 週間で実行されたビルドを記録します。*                                            |
| usage_oss_macos_current              | 分       |                                                                   |
| usage_oss_linux_legacy               | 分       |                                                                   |
| usage_oss_linux_current              | 分       |                                                                   |
| usage_private_macos_legacy           | 分       |                                                                   |
| usage_private_macos_current          | 分       |                                                                   |
| usage_private_linux_legacy           | 分       |                                                                   |
| usage_private_linux_current          | 分       |                                                                   |
| new_projects_oss_macos_legacy      | 合計      | *1.0 で実行された新しいビルドを捕捉します。1.0 で新しいプロジェクトを開始しているユーザーがいるかどうかを確認できます。* |
| new_projects_oss_macos_current     | 合計      |                                                                   |
| new_projects_oss_linux_legacy      | 合計      |                                                                   |
| new_projects_oss_linux_current     | 合計      |                                                                   |
| new_projects_private_macos_legacy  | 合計      |                                                                   |
| new_projects_private_macos_current | 合計      |                                                                   |
| new_projects_private_linux_legacy  | 合計      |                                                                   |
| new_projects_private_linux_current | 合計      |                                                                   |
| projects_oss_macos_legacy            | 合計      | *1.0 および 2.0 で実行されたビルドを捕捉します。ユーザーが 2.0 に移行しているか、1.0 のままかを確認できます。* |
| projects_oss_macos_current           | 合計      |                                                                   |
| projects_oss_linux_legacy            | 合計      |                                                                   |
| projects_oss_linux_current           | 合計      |                                                                   |
| projects_private_macos_legacy        | 合計      |                                                                   |
| projects_private_macos_current       | 合計      |                                                                   |
| projects_private_linux_legacy        | 合計      |                                                                   |
| projects_private_linux_current       | 合計      |                                                                   | 
{: class="table table-striped"}

## Accessing usage data

このデータにプログラムでアクセスして、組織内の使用状況をさらに詳しく把握したいときには、Services VM からこのコマンドを実行します。

`docker exec usage-stats /src/builds/extract`

### Security and privacy

Please reference exhibit C within your terms of contract and our [standard license agreement](https://circleci.com/legal/enterprise-license-agreement/) for our complete security and privacy disclosures.