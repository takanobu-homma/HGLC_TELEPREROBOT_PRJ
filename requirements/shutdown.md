---
title: テレプレゼンスロボット要求分析
subtitle: 「SysRS-15:シャットダウンする」の要求詳細化
author: 株式会社 豆蔵
date: 2021年12月10日
---
<!-- ↑表紙ページのための情報 -->

<div style="page-break-before:always"></div>

# はじめに

## 本書の目的

本書の目的は、USDMによる要求記述のため、テレプレゼンスロボット本体のL0要求「SysRS-15:シャットダウンする」のL1要求分析結果に基づき、HGLCが担当するL1要求に対してL2要求を抽出することである。

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
|テレプレゼンスロボット要求分析.docx|テレプレゼンスロボット本体のL0/L1要求分析についての検討過程を記述したファイル|


<div style="page-break-before:always"></div>

# L2要求分析

「SysRS-15:シャットダウンする」のアクティビティ図を以下に示す。

![](.images/activity/shutdown.png)

上記L0のアクティビティ図のアクション/デシジョン等から導出された胴体部・走行部のL1要求に対するL2要求分析を行う。  
※頭部に対してはavatarin側の責務のため、本書では対象外とする。

<div style="page-break-before:always"></div>

## 頭部は頭部のシャットダウン操作を走行部に通知する

avatarin側の責務のため、対象外とする。

<div style="page-break-before:always"></div>

## 頭部は頭部のシャットダウン操作または、走行部からのシャットダウン開始を受信し終了処理を開始する

avatarin側の責務のため、対象外とする。

<div style="page-break-before:always"></div>

## 頭部はアバタークラウドを切断する

avatarin側の責務のため、対象外とする。

<div style="page-break-before:always"></div>

## 頭部は自己診断を行う

avatarin側の責務のため、対象外とする。

<div style="page-break-before:always"></div>

## 頭部は終了する

avatarin側の責務のため、対象外とする。

<div style="page-break-before:always"></div>

## 頭部は走行部へ終了処理完了通知を送信する

avatarin側の責務のため、対象外とする。

<div style="page-break-before:always"></div>

## 胴体部はシャットダウンしていることを表示する

![](.images/activity/shutdown/body-act01.png)

**L2要求抽出**

|要求|備考|
|:---|:---|
|||

<div style="page-break-before:always"></div>

## 胴体部は頭部による自己診断を受ける

![](.images/activity/shutdown/body-act02.png)

**L2要求抽出**

|要求|備考|
|:---|:---|
|||

<div style="page-break-before:always"></div>

## 胴体部は電源OFFにより状態表示をOFFにする

![](.images/activity/shutdown/body-act03.png)

**L2要求抽出**

|要求|備考|
|:---|:---|
|||

<div style="page-break-before:always"></div>

## 走行部はシャットダウン開始を受信する

![](.images/activity/shutdown/act01.png)


**L2要求抽出**

|要求|備考|
|:---|:---|
|||

<div style="page-break-before:always"></div>

## 走行部は頭部へシャットダウン開始を通知する

![](.images/activity/shutdown/act01.png)


**L2要求抽出**

|要求|備考|
|:---|:---|
|||

<div style="page-break-before:always"></div>

## 走行部は頭部への電源をOFFする

![](.images/activity/shutdown/act01.png)


**L2要求抽出**

|要求|備考|
|:---|:---|
|||

<div style="page-break-before:always"></div>

## 走行部は自己診断を行う

![](.images/activity/shutdown/act01.png)


**L2要求抽出**

|要求|備考|
|:---|:---|
|||

<div style="page-break-before:always"></div>

## 走行部は自己診断が正常に完了した場合、走行履歴を保存する

![](.images/activity/shutdown/act01.png)


**L2要求抽出**

|要求|備考|
|:---|:---|
|||

<div style="page-break-before:always"></div>

## 走行部は自己診断で異常があった場合、走行履歴および診断結果を保存する

![](.images/activity/shutdown/act01.png)


**L2要求抽出**

|要求|備考|
|:---|:---|
|||

## 走行部は走行部を終了する

![](.images/activity/shutdown/act01.png)


**L2要求抽出**

|要求|備考|
|:---|:---|
|||

## 走行部は走行部の電源をOFFにする

![](.images/activity/shutdown/act01.png)


**L2要求抽出**

|要求|備考|
|:---|:---|
|||