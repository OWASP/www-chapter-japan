---
title: 脆弱性診断士スキルマッププロジェクト
layout:  null
tab: true
order: 1
tags: 脆弱性診断士スキルマッププロジェクト
---
# 脆弱性診断士スキルマッププロジェクト
[特定非営利活動法人日本ネットワークセキュリティ協会](https://www.jnsa.org/)の[日本セキュリティオペレーション事業者協議会](https://isog-j.org/)のセキュリティオペレーションガイドラインWG（WG1）と、OWASP Japan主催の共同ワーキンググループである 「脆弱性診断士スキルマッププロジェクト （代表 上野宣）」では、脆弱性診断を行う個人の技術的な能力を具体的にすべく、脆弱性診断を行う技術者（以下、脆弱性診断士）のスキルマップと学習の指針となるシラバス、脆弱性診断を行うためのガイドライン、Webアプリケーションを安全に構築するために必要な要件定義書などを整備しています。

本ワーキンググループに関心のある方は Project leader: [Sen UENO](mailto:sen.ueno@owasp.org) まで

# ペネトレーションテストについて
コンピュータシステムに対して実施するセキュリティテストの1つとして「脆弱性診断」がよく知られています。「脆弱性診断」は本プロジェクトでも紹介しているような脆弱性を発見するためのセキュリティテストの手法です。

一方で最近は「ペネトレーションテスト」を採用する組織や、ペネトレーションテストサービスを提供する事業者（テストベンダー）が増えてきました。
ただ、現状では「ペネトレーションテスト」という名称に共通認識がなく、テストベンダーによっては「脆弱性診断」のことを「ペネトレーションテスト」と呼んでいることもあり、テストを採用する組織が目的に合ったサービスを見分けることが難しくなっています。

本ドキュメントは「ペネトレーションテスト」の位置づけを明確にし、セキュリティテストを活用する組織が実施目的に合うサービスを選択できることを目的としています。

* [ペネトレーションテストについて（2019年12月8日版）](https://github.com/ueno1000/about_PenetrationTest)

# Webシステム／Webアプリケーションセキュリティ要件書
本ワーキンググループが公開する『Webシステム／Webアプリケーションセキュリティ要件書 』ドキュメントは、Webシステム／Webアプリケーションに関して一般的に盛り込むべきと考えられるセキュリティ要件について記載しています。また、開発言語やフレームワークなどに依存することなくご利用いただけます。ただし、ネットワークやホストレベル、運用などに関するセキュリティ要件については記載していません。

Ver.3.0からはチェックリストとして活用しやすい「Webシステム／Webアプリケーションセキュリティ要件書チェックリスト」も公開しています。

## Download
### 2019年1月15日リリース版
* [Webシステム／Webアプリケーションセキュリティ要件書 Ver.3.0（GitHub）](https://github.com/ueno1000/secreq)
* [Webシステム／Webアプリケーションセキュリティ要件書（WORD版）](https://github.com/ueno1000/secreq/blob/master/OWASP_WebApplicationSecurityRequirements3.0.docx)
* [Webシステム／Webアプリケーションセキュリティ要件書（PDF版）](https://github.com/ueno1000/secreq/blob/master/OWASP_WebApplicationSecurityRequirements3.0.pdf)
* [Webシステム／Webアプリケーションセキュリティ要件書チェックリスト（EXCEL版）](https://github.com/ueno1000/secreq/blob/master/OWASP_WebApplicationSecurityRequirements3.0_CheckList.xlsx)
* [Webシステム／Webアプリケーションセキュリティ要件書チェックリスト（PDF版）](https://github.com/ueno1000/secreq/blob/master/OWASP_WebApplicationSecurityRequirements3.0_CheckList.pdf)

# Webアプリケーション脆弱性診断ガイドライン
Webアプリケーションの脆弱性診断は、自動診断ツールを使った脆弱性診断だけでは十分な診断結果が得られないと本プロジェクトでは考えており、そのため手動診断補助ツールを使った手動診断を併用することが望ましいとしています。しかし、手動診断は脆弱性診断士の経験やスキルによる診断能力の差違があります。そこで本プロジェクトでは、最低限必要な診断項目や手順を定義することで、一定レベルの手動診断による脆弱性診断を行うことができる「Webアプリケーション脆弱性診断ガイドライン」（以下、本ガイドライン）を作成し公開します。

本ガイドラインは「脆弱性診断士」における「脆弱性診断士（Webアプリケーション）」区分における「Silver」ランクで要求される内容としています。

## Download
### 2018年5月18日リリース版
* [Webアプリケーション脆弱性診断ガイドライン（EXCEL版）](https://github.com/ueno1000/WebAppPentestGuidelines/blob/master/WebAppPentestGuidelines.xlsx)
* [Webアプリケーション脆弱性診断ガイドライン（PDF版）](https://github.com/ueno1000/WebAppPentestGuidelines/blob/master/WebAppPentestGuidelines.pdf)
* [Webアプリケーション脆弱性診断ガイドラインについて](https://github.com/ueno1000/WebAppPentestGuidelines/blob/master/about_WebAppPentestGuidelines.pdf)
* [Webアプリケーション脆弱性診断ガイドライン利用のためのドキュメント](https://docs.google.com/document/d/1-eZqWf2TqfEwc9f-OZr6bY24VjvNMUwS9zzAejpZQ64/)
* [ガイドラインを使いこなすためのリンク集](https://github.com/ueno1000/WebAppPentestGuidelines)

# 脆弱性診断士スキルマップ＆シラバス

## 作成方針
スキルマップとシラバスの作成を下記の方針に基づいて行っています。
* 脆弱性診断業務に必要な技術的な能力を対象とする
* マネージメントスキルやコミュニケーションスキルは対象外とする
* 脆弱性診断士に必要なスキルを明確化する
* 特定の脆弱性診断ツールや環境に依存しないようにする
* 現在必要だと考えられる技術水準を基に作成する
* 脆弱性診断士が持つべきスキルの指標とするものであり、各社が提供する脆弱性診断サービスの品質については対象外とする

## 「脆弱性診断士」ランク
脆弱性診断士のランクを定義するにあたっては、脆弱性診断業務に従事する者が全員知っておくべき技能（ Silver ランク）と、単独で診断業務を行うために必要な技能（ Gold ランク）を定義した２つのランクに分けています。

### Silver ランク
Gold ランクの者から指導を受けた上で診断サービスを提供する、もしくは、自社向けに脆弱性診断を実施するための必要スキルとして設定しています。

* 対象者像
    * 自社のWebアプリケーション／システムの脆弱性診断（受入れ検査）を行う方
    * 脆弱性診断業務の従事を目指す方（学生など）
* 業務と役割
    * Goldランクの者の指示の下、脆弱性診断を行う
    * 自社ITシステムの脆弱性診断を行う
* 期待する技術水準
    * ITシステムを診断する上で（最低限）必要な技術や知識を保有

### Gold ランク
業務としての脆弱性診断サービスを提供するチームにおいて、最低限1名以上メンバーに加えるべきスキルとして設定しています。

* 対象者像
    * Webアプリケーション／システムの脆弱性診断（受入れ検査）を行う方
    * 脆弱性診断をサービスとして提供する業務に従事する方
* 業務と役割
    * 脆弱性診断業務を管理し、診断方針の決定、作業指示の実施、診断結果の精査および評価を行うことができる
    * 脆弱性診断の報告書を作成し、技術的な説明ができる
* 期待する技術水準
    * 脆弱性診断サービスを提供するのに必要十分な技術や知識を保有

# 脆弱性診断士（Webアプリケーション）スキルマップ＆シラバス
Webアプリケーション/Webシステムに対する脆弱性診断を行う者が対象です。対象者像としては、Webアプリケーション/Webシステムの脆弱性診断を必要とする者、Webアプリケーション/Webシステムの開発者、運用者を想定しています。

## Download
### 2018年5月18日リリース版
* [スキルマップ＆シラバスについて(PDF)](https://github.com/ueno1000/WebAppPentestGuidelines/blob/master/About-Pentester-Web-Skillmap_and_Syllabus.pdf)
* [スキルマップ＆シラバス(PDF)](https://github.com/ueno1000/WebAppPentestGuidelines/blob/master/Pentester-Web-Skillmap_and_Syllabus.pdf)

# 脆弱性診断士（プラットフォーム）スキルマップ＆シラバス
システムのプラットフォーム部分に対する脆弱性診断を行う者が対象です。対象者像としては、システムのプラットフォーム部分の脆弱性診断を必要とする者、システムのプラットフォームの構築者、運用者を想定しています。

## Download
### 2016年4月19日リリース版
* [スキルマップ＆シラバスについて(PDF)](https://www.owasp.org/images/9/90/About-Pentester-Platform-Skillmap_and_Syllabus-201604.pdf)
* [スキルマップ＆シラバス(PDF)](https://www.owasp.org/images/4/41/Pentester-Platform-Skillmap_and_Syllabus-201604.pdf)
