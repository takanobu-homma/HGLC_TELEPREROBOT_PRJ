---
title: テレプレゼンスロボット要求分析
subtitle: 「SysRS-20:運転履歴をクリアする」のL2要求抽出
author: 株式会社 豆蔵
date: 2022年3月22日
---
<!-- ↑表紙ページのための情報 -->

<div style="page-break-before:always"></div>

# はじめに

## 本書の目的

本書の目的は、USDMによる要求記述のため、テレプレゼンスロボット本体のL0要求「SysRS-20:運転履歴をクリアする」のL1要求分析結果に基づき、HGLCが担当するL1要求に対してL2要求を抽出することである。

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

「SysRS-20:運転履歴をクリアする」のアクティビティ図を以下に示す。



![](.images/activity/clear_drive_history.png)  
modelID:{SysRM-act20}

上記L0のアクティビティ図のアクション/デシジョン等から導出された胴体部・走行部のL1要求に対するL2要求分析を行う。  
※頭部に対してはavatarin側の責務のため、本書では対象外とする。

<div style="page-break-before:always"></div>

## 走行部は診断PCからのログインに応じて通信を確立し、車体情報を送信する

![](.images/activity/clear_drive_history/act01.png)  
modelID:{SysRM-act20-01}

**L2要求抽出**

|要求|備考|
|:---|:---|
|Miimo Main ECUは診断PCとの通信を確立する|※1※2|
|Miimo Main ECUはEEPROMに車体番号の読み出しを依頼する||
|Miimo Main ECUはEEPROMから受けた車体番号を診断PCに送信する|※1|
|EEPROMはMiimo Main ECUの依頼を受けて車体番号を返す|※3|
※1:診断PCとの通信はリプロ用コネクタを経由する想定  
※2:テストモードの起動/通信確立手順の詳細は状態分析とともに要QA  
※3:車体番号の保存先をEEPROMと想定  

<div style="page-break-before:always"></div>

## 走行部は診断PCからの指示で運転履歴をクリアする

![](.images/activity/clear_drive_history/act02.png)  
modelID:{SysRM-act20-02}

**L2要求抽出**

|要求|備考|
|:---|:---|
|Miimo Main ECUは診断PCから運転履歴クリア指示を受ける|※1|
|Miimo Main ECUはEEPROMに運転履歴クリアを依頼する||
|Miimo Main ECUはEEPROMから受けた運転履歴クリア結果を診断PCに送信する|※1|
|EEPROMはMiimo Main ECUからの依頼を受けて運転履歴をクリアし結果を返す|※2※3|
※1:診断PCとの通信はリプロ用コネクタを経由する想定  
※2:運転履歴の保存先をEEPROMと想定  
※3:運転履歴のクリアは工場でのリペア時に利用される(通常のテスト時には利用されない)想定  