---
title: テレプレゼンスロボット要求分析
subtitle: 「SysRS-09:充電ステーションを検出する」のL2要求抽出
author: 株式会社 豆蔵
date: 2022年3月22日
---

<!-- 表紙ページのための改ページ -->
<div style="page-break-before:always"></div>


# はじめに

## 本書の目的

本書の目的は、USDMによる要求記述のため、テレプレゼンスロボット本体のL0要求「SysRS-09:充電ステーションを検出する」のL1要求分析結果に基づき、HGLCが担当するL1要求に対してL2要求を抽出することである。

## 適用

本要件の適用対象は、テレプレゼンスロボット とする。

## 用語の定義

|用語|説明|
|:---|:---|
|特に無し|---|

## 関連資料

|資料名|説明|
|:---|:---|
|テレプレゼンスロボット要求一覧&USDM.xlsx|本文書の要求分析結果をまとめ、USDMの形式で記述したファイル|
|機能干渉マトリクス.xlsx|本文書の要求分析および今後の仕様化を進める際に検討が必要な機能干渉についてマトリクス表で整理を行ったファイル|
|テレプレゼンスロボット要求分析_L0L1要求抽出.docx|テレプレゼンスロボット本体のL0/L1要求分析についての検討過程を記述したファイル|


<div style="page-break-before:always"></div>

# L2要求分析

「SysRS-09:充電ステーションを検出する」のアクティビティ図を以下に示す。

![](.images/activity/station_detection.png)  
modelID:{SysRM-act09}

上記L0のアクティビティ図のアクション/デシジョン等から導出された胴体部・走行部のL1要求に対するL2要求分析を行う。  
※頭部に対してはavatarin側の責務のため、本書では対象外とする。

<div style="page-break-before:always"></div>

## 頭部は走行部からステーション検出値（内外判定、強度）を受信する

avatarin側の責務のため、対象外とする。

<div style="page-break-before:always"></div>

## 頭部はステーション検出の設定を確認し、ステーション検出設定が有効な場合のみステーション検出を行う

avatarin側の責務のため、対象外とする。

<div style="page-break-before:always"></div>

## 頭部はステーション検出値の強度に応じてステーション近傍およびステーションワイヤに対する減速・停止距離を判断する

avatarin側の責務のため、対象外とする。

<div style="page-break-before:always"></div>

## 頭部は減速距離に近づいたら、それをアバタークラウドに通知する

avatarin側の責務のため、対象外とする。

<div style="page-break-before:always"></div>

## 頭部は減速距離に近づいたら、走行コマンドの速度を制限する

avatarin側の責務のため、対象外とする。

<div style="page-break-before:always"></div>

## 頭部は停止距離に近づいたら、それをアバタークラウドに通知する

avatarin側の責務のため、対象外とする。

<div style="page-break-before:always"></div>

## 頭部は停止距離に近づいたら、走行コマンドの速度を0にする

avatarin側の責務のため、対象外とする。

<div style="page-break-before:always"></div>

## 走行部はステーションワイヤとの間に生じるステーション信号からステーション検出を行いステーション検出値を送信する

![](.images/activity/station_detection/act01.png)  
modelID:{SysRM-act09-01}

**L2要求抽出**

|要求|備考|
|:---|:---|
|Miimo Main ECUはステーション信号をステーション検出値に変換し送信する|ステーション検出値：ステーション信号値をCAN通信に則した形態（内外判定・信号強度）に変換したもの|
|エリアセンサはステーションワイヤ/ドッキングワイヤとの距離や向きを検出しアナログ信号として出力する||

<div style="page-break-before:always"></div>

## 走行部は頭部からの走行コマンドの速度制限指示にしたがい走行速度を落とす

![](.images/activity/station_detection/act02.png)  
modelID:{SysRM-act09-02}

**L2要求抽出**

|要求|備考|
|:---|:---|
|Miimo Main ECUは走行操作コマンドから左右モータ駆動信号に変換する|・走行操作コマンドはCAN通信（並進速度とヨーレート指令）<br/>・走行操作コマンドの変換の際、エリア信号/ステーション信号は考慮しない（エリア外への逸脱/ステーションとの衝突回避は頭部責務）|
|右走行モータはモータ駆動信号によりモータを駆動する|機能干渉マトリクスより、右走行モータ駆動中に別のモータ駆動信号が入力された場合、その信号に従って動作する|
|左走行モータはモータ駆動信号によりモータを駆動する|機能干渉マトリクスより、左走行モータ駆動中に別のモータ駆動信号が入力された場合、その信号に従って動作する|

<div style="page-break-before:always"></div>

## 走行部は頭部からの走行コマンドの速度0指示にしたがい走行を停止する

![](.images/activity/station_detection/act03.png)  
modelID:{SysRM-act09-03}

**L2要求抽出**

|要求|備考|
|:---|:---|
|→L2要求としては「走行部は頭部からの走行コマンドの速度制限指示にしたがい走行速度を落とす」の速度=0のケースと同様||
