# Security in Agile Development | Pattern Language

# About this document
The [Vulnerability Assessment Skills Map Project](https://github.com/OWASP/www-chapter-japan/tree/master/skillmap_project) has created this document to provide tips on "**How to Ensure Security in Agile Development**" using pattern language based on past successes and other examples.  
In waterfall development, the project defines security requirements during the requirements definition phase, followed by secure design and implementation, and finally, release after vulnerability assessment. In agile development, however, these phases are not always clear and sometimes neglect security. Developers can use this document to get hints on what to do to ensure security at what stage of agile development. We hope this document will help you to ensure security in agile development.  

本ドキュメントは[脆弱性診断士スキルマッププロジェクト](https://github.com/OWASP/www-chapter-japan/tree/master/skillmap_project)が作成した『**アジャイル開発においてセキュリティをどのように担保するか**』のヒントを過去の成功事例などを基にパターン・ランゲージを使って解説したものです。

ウォーターフォール開発では、要件定義のフェーズではセキュリティ要件があり、それに沿ったセキュアな設計や実装が行われ、脆弱性診断を行ってからリリースされます。しかし、アジャイル開発ではそれらのフェーズが明確でないこともあり、セキュリティを如何に担保するかということが疎かになることもあります。
本ドキュメントを活用して頂くことで、アジャイル開発のどの段階でどういった取り組みをすることでセキュリティを担保できるかといったヒントを得ることができます。
本ドキュメントがアジャイル開発においてセキュリティが担保される一助になればと願います。

# Table of Contents
- **Team Building**
1. [Role definition and appointment of security champions](#1. Role definition and appointment of security champions)
2. [Team building with each person responsible for security](#2-Team building with each person responsible for security)
3. [Establishment of rules to improve security](#3-Establishment of rules to improve security)
4. [Training for developers to improve their security skills](#4-Training for developers to improve their security skills)
- **Development and project planning**
5. [Determine security requirements for sprint deliverables](#5-Determine security requirements for sprint deliverables)
6. [Develop risk-based vulnerability response policies](#6-Develop risk-based vulnerability response policies)
7. [Vulnerability Triage](#7-Vulnerability Triage)
- **Security Testing**
8. [Security testing timing and policy considerations](#8-Security testing timing and policy considerations)
9. [Formulation of test content to be conducted within the sprint](#9-Formulation of test content to be conducted within the sprint)
10. [Vulnerability management for your environment](#10-Vulnerability management for your environment)
11. [Automated security testing](#11-Automated security testing)
- **Security Quality Improvement**
12. [Reflection on Continuous Improvement of Security](#12-Reflection on Continuous Improvement of Security)

- **チームビルディング**
1. セキュリティ・チャンピオンの役割定義と任命
2. 各自がセキュリティに責任を持ったチームビルディング
3. セキュリティ向上のためのルール整備
4. セキュリティスキル底上げのための開発者向けトレーニング
- **開発計画・プロジェクト計画**
5. スプリント成果物に必要なセキュリティ要件の決定
6. リスクに応じた脆弱性対応方針の策定
7. 脆弱性トリアージ
- **セキュリティテスト**
8. セキュリティテストの実施タイミングと方針検討
9. スプリント内で実施するテスト内容の策定
10. 利用環境の脆弱性管理
11. セキュリティテストの自動化
- **セキュリティ品質向上**
12. セキュリティの継続的向上のためのふりかえり

# Team Building
## 1. Role definition and appointment of security champions

### Summary
Create a DevSecOps culture where security is integrated into the development process by having a "Security Champion" on each product team who checks for security issues and acts as a bridge to developers.

各プロダクトチームの中にセキュリティ上の問題をチェックし、開発者との橋渡しの役割を担う『セキュリティ・チャンピオン』を置くことで、セキュリティが開発工程の中に組み込まれるDevSecOpsの文化を創ろう

### Situation
* No culture of security considerations
* None of the members care about security
* No one proactively thinks about security

* セキュリティを考慮する文化がない
* セキュリティのことをメンバーの誰もが気にしていない
* セキュリティを主体的に考える人が誰もいない

### Problem to be solved
* Prioritizing implementation over functionality only results in the release of an insecure product.

* 機能優先のみで実装を行うことによる非セキュアなプロダクトがリリースされてしまう

### Solution
* When determining member roles at project launch, identify one of the development members on the team as the security champion. 
    * The product owner defines specific roles, etc., and appoints the person in charge.
* The Security Champion does not need to be a security expert, but as the person in charge of security on the development team.
    * The Security Champion must take a central leadership role in addressing security issues and threats in the product or service being developed. 
    * The Champion must be able to take the lead in addressing security issues and threats to the products and services being developed. 
    * If the team's internal resources are not available to address the issue, consider using an outside vendor or other resources.
* Examples of specific roles are listed below. It is advisable to assemble a team that can.
    * Conducting security reviews
    * Conducting threat analysis on developments
    * Defining security requirements and coding conventions for development
    * Managing vulnerabilities detected, reporting problems, prioritizing countermeasures, etc.
    * Implementing, conducting, and verifying security testing and vulnerability scanning
    * Promoting standardization of security knowledge and security awareness within the team through education and information sharing
    * Selecting and controlling external security vendors

* プロジェクト立ち上げの際にメンバーの役割を決めるとき、チーム内の開発メンバーの一人にセキュリティ・チャンピオンの役割を担わせる 
    * プロダクトオーナーが具体的な役割などを定義し、担当者を任命
* セキュリティ・チャンピオンはセキュリティの専門家である必要はありませんが、開発チームにおけるセキュリティの担当者として、開発している製品やサービスにおけるセキュリティ上の問題や脅威に対して、中心となってリーダーシップを発揮しながら対処を行わなければなりません。チーム内のリソースで対応できない場合、外部ベンダーなどの利用も検討してください。
* 具体的な役割の例としては以下が挙げられ、実現可能なチームを編成することが望ましいです。
    * セキュリティレビューの実施
    * 開発物に対する脅威分析の実施
    * 開発におけるセキュリティ要件の定義やコーディング規約などの整備
    * 検出した脆弱性の管理や問題の報告、対策の優先順位付けなど
    * セキュリティテスト・脆弱性スキャンの導入・実施・検証
    * 教育や情報の共有などによって、チーム内のセキュリティ知識の標準化やセキュリティ意識の向上を促進
    * 外部セキュリティベンダーの選定やコントロール

### Reference Materials
* [Security Champions 2.0](https://owasp.org/www-pdf-archive/OWASP_Bucharest_2017_Antukh.pdf)
* [security-champions-playbook](https://github.com/c0rdis/security-champions-playbook)
* [「開発者セキュリティチャンピオン」がDevSecOps革命の鍵を握る - リックソフトブログ](https://www.ricksoft.jp/blog/articles/001301.html)
* [Mercari’s Security Champion Program: Gamifying Security Education for a Safe and Secure Service | Mercan ](https://mercan.mercari.com/en/articles/19140/)

## 2. Team building with each person responsible for security

### Summary
Make each person responsible for the security quality of the deliverables they develop.

開発する成果物のセキュリティ面での品質に対して各自が責任を持つようにしよう

### Situation
* Members of the team other than the security champion do not care about security
* Members do not understand the security functions for which they are responsible in their area of responsibility when conducting team building
* None of the members care about security

* セキュリティチャンピオン以外のメンバーがセキュリティのことを気にしていない
* チームビルディングを実施するときに、自分の担当範囲で責任を持つセキュリティ機能を理解していない
* セキュリティのことをメンバーの誰もが気にしていない

### Problem to be solved
* Concentrates the load on security personnel or security champions

* セキュリティ担当者、もしくはセキュリティチャンピオンへの負荷の集中

### Solution  
* Conduct security training to deepen understanding of risks, vulnerabilities, and countermeasures.
* Share information with your teams, such as case studies of bugs introduced during development and the results of code reviews.
* Discuss security at each phase of the project.
    * Identify risks during the requirements phase to minimize the possibility of the team creating vulnerabilities.
    * Consider in advance when to conduct vulnerability validation.
* Avoid blaming individuals for security failures.
    * Value the spirit of HRT (Humility: Humility, Respect: Respect, Trust: Trust) toward your peers.

* セキュリティ教育を実施し、リスクや脆弱性、対策方法に対する理解を深める様にしてください。
* 開発時に混入したバグに関するケーススタディやコードレビューの結果などについて、チーム内で情報の共有を行いましょう。
* セキュリティについての議論を各フェーズで実施しましょう。
    * 要件の段階で事前にリスクの洗い出しを行い、成果物に脆弱性が含まれる可能性を最小限にする。
    * 脆弱性検証を実施するタイミングを事前に検討しておく。
* セキュリティの失敗で個人を責めないようにしましょう。
    * 仲間に対するHRT（Humility：謙虚、Respect：尊敬、信頼：Trust）の精神を大事にしよう。

### Reference Materials
* [Team Geek](https://www.oreilly.co.jp/books/9784873116303/)

## 3. Establishment of rules to improve security

### Summary
Instead of leaving everything to the experts regarding security, let's discuss and develop rules that all developers can implement on the minimum points that need to be taken care of during development.

セキュリティに関して専門家にすべてを任せるのではなく、開発時に気を付けなければならない最低限のポイントについて開発者全員が実施できるルールを話し合って整備しよう

### Situation
* Rely on individuals for security measures within the team

* チーム内でのセキュリティ対策については個人に依存している

### Problem to be solved
* Different developers implement different security qualities.

* 開発者によってセキュリティ面での品質が異なる実装が行われる

### Solution
* Discuss within your team and develop rules to ensure quality in terms of security.
  * Incorporate rules for handling vulnerabilities among those listed below.
    * Coding rules
    * Code review methodology
    * Approval flow
    * Deployment flow
    * Security testing rules
    * Response flow when vulnerabilities are discovered
    * Vulnerability management
    * Configuration management
  * Example:
    * Coding rules that developers should be aware of during development, such as escape processing for input values
    Incorporate into the vulnerability discovery response flow: * When vulnerabilities are detected, when and who responds to them, etc.

* Make the rules known to the team and provide opportunities to review them if possible.

* チーム内で話し合い、セキュリティ面での品質を担保するためのルールを整備しましょう。
  * 以下で列挙されているものの中に脆弱性の扱いに関するルールを組み込みましょう。
    * コーディングルール
    * コードレビュー手法
    * 承認フロー
    * デプロイまでのフロー
    * セキュリティテストのルール
    * 脆弱性発見時の対応フロー
    * 脆弱性管理
    * 構成管理
  * 例:
    * 入力値に対してエスケープ処理を実施するなど開発者が開発時に気を付けるポイントをコーディングルールとして組み込む
    * 脆弱性の検出時に、どのタイミングで誰が対応するかなどについて脆弱性発見時の対応フローに組み込む

* 整備したルールはチーム内に周知し、可能であれば見直しの機会などを設けましょう。

## 4. Training for developers to improve their security skills

### Summary
Instead of leaving everything to the experts regarding security, let's ensure that all developers understand the minimum points they need to be aware of during development through training.

セキュリティに関して専門家にすべてを任せるのではなく、開発時に気を付けなければならない最低限のポイントについてはトレーニングを受けることで開発者全員が理解できるようになろう。

### Situation
* Developers have varying knowledge of security
* Developers lack security knowledge

* 開発者によってセキュリティに対する知識にばらつきがある
* 開発者にセキュリティの知識がない

### Problem to be solved
* Different developers implement security qualities in different ways
* Burden is concentrated on individuals who are knowledgeable about security

* 開発者によってセキュリティ面での品質が異なる実装が行われる
* セキュリティについて詳しい個人に負荷が集中する

### Solution
* Conduct security training that includes the following
    * Incident examples from other companies in your industry
    * Vulnerabilities that are likely to occur
    * About secure requirements definition, design, coding, and testing
    * Types of security testing (SAST, DAST...)
* If you cannot conduct training in-house, use external content or attend training.

* 次のようなセキュリティトレーニングを実施しましょう。
    * 同業他社のインシデント事例
    * 発生しやすい脆弱性について
    * セキュアな要件定義、設計、コーディング、テストについて
    * セキュリティテストの種類（SAST,DAST…）
* 自社でトレーニングを実施できない場合には、外部のコンテンツを利用したり、トレーニングを受講しましょう。

### Reference Materials
* [OWASP Foundation \| Open Source Foundation for Application Security](https://owasp.org/)
* [ISOG\-J Information Security Operation providers Group Japan](https://isog-j.org/e/index.html)
* [Japan Network Security Association](https://www.jnsa.org/en/aboutus/)
* [INFORMATION-TECHNOLOGY PROMOTION AGENCY, JAPAN](https://www.ipa.go.jp/index-e.html)
* [JPCERT Coordination Center](https://www.jpcert.or.jp/english/)

# Development and project planning

## 5. Determine security requirements for sprint deliverables

### Summary
The definition of the completion of the deliverables to be developed within the sprint period should include not only the functional requirements but also the security requirements that teams must implement and their test items!

スプリント期間内に開発する成果物の完成の定義には、機能要件だけでなく、実装しておかなければいけないセキュリティ要件とそのテスト項目についても含めておこう

### Situation
* Sprints begin with unclear requirements for security

* セキュリティについての要件が曖昧なままスプリントが始まる

### Problem to be solved
* Development proceeds without sufficient testing, and vulnerabilities are often discovered during vulnerability assessments, resulting in a lot of rework.
* Insecure products with remaining vulnerabilities are released.

* 十分なテストがされないまま開発が進み、脆弱性診断などで多くの脆弱性が発見され手戻りが多くなる
* 脆弱性が残ったままの非セキュアなプロダクトがリリースされてしまう

### Solution
* When defining deliverable completion in sprint planning, specify the security requirements that the deliverables must implement. The following documents are helpful.
    * [Web システム／Web アプリケーションセキュリティ要件書](https://github.com/OWASP/www-chapter-japan/tree/master/skillmap_project#web%E3%82%B7%E3%82%B9%E3%83%86%E3%83%A0web%E3%82%A2%E3%83%97%E3%83%AA%E3%82%B1%E3%83%BC%E3%82%B7%E3%83%A7%E3%83%B3%E3%82%BB%E3%82%AD%E3%83%A5%E3%83%AA%E3%83%86%E3%82%A3%E8%A6%81%E4%BB%B6%E6%9B%B8)
    * [OWASP Application Security Verification Standard](https://github.com/OWASP/ASVS/tree/v4.0.3)
* These are written general security requirements and include items that may be irrelevant depending on the subject your team is developing in a sprint, so please select the things you need based on the issue you are creating.
* For example, input value validation and output escaping will be necessary in any case. Authentication and session management, for example, will be required only for sprints that implement those functions.
* Once you have determined the security requirements for your sprint, please also consider the corresponding test items. The following documents may be helpful.
    * [Webアプリケーション脆弱性診断ガイドライン](https://github.com/OWASP/www-chapter-japan/tree/master/skillmap_project#web%E3%82%A2%E3%83%97%E3%83%AA%E3%82%B1%E3%83%BC%E3%82%B7%E3%83%A7%E3%83%B3%E8%84%86%E5%BC%B1%E6%80%A7%E8%A8%BA%E6%96%AD%E3%82%AC%E3%82%A4%E3%83%89%E3%83%A9%E3%82%A4%E3%83%B3)

* スプリントプランニングで成果物の完成の定義を検討するとき、[Web システム／Web アプリケーションセキュリティ要件書](https://github.com/OWASP/www-chapter-japan/tree/master/skillmap_project#web%E3%82%B7%E3%82%B9%E3%83%86%E3%83%A0web%E3%82%A2%E3%83%97%E3%83%AA%E3%82%B1%E3%83%BC%E3%82%B7%E3%83%A7%E3%83%B3%E3%82%BB%E3%82%AD%E3%83%A5%E3%83%AA%E3%83%86%E3%82%A3%E8%A6%81%E4%BB%B6%E6%9B%B8)や[OWASP アプリケーションセキュリティ検証標準 4.0](https://www.saj.or.jp/documents/NEWS/pr/20200903_OWASP_ASVS4.0-ja.pdf)を参考に、成果物が実装しておかなければいけないセキュリティ要件を定義してください。
* これらは一般的なセキュリティ要件が書かれており、スプリントで開発する対象によっては無関係な項目も含まれていますので、開発対象に応じて必要な項目を選定してください。
* たとえば、入力値の検証や出力時のエスケープなどは、どのような場合でも必要になるでしょう。認証やセッション管理などは、それらの機能を実装するスプリントの場合にのみ必要になるでしょう。
* スプリントのセキュリティ要件が決まったら、[Webアプリケーション脆弱性診断ガイドライン](https://github.com/OWASP/www-chapter-japan/tree/master/skillmap_project#web%E3%82%A2%E3%83%97%E3%83%AA%E3%82%B1%E3%83%BC%E3%82%B7%E3%83%A7%E3%83%B3%E8%84%86%E5%BC%B1%E6%80%A7%E8%A8%BA%E6%96%AD%E3%82%AC%E3%82%A4%E3%83%89%E3%83%A9%E3%82%A4%E3%83%B3)を参考に、それぞれに対応するテスト項目も併せて検討してください。

### Reference Materials

* [Web システム／Web アプリケーションセキュリティ要件書](https://github.com/OWASP/www-chapter-japan/tree/master/skillmap_project#web%E3%82%B7%E3%82%B9%E3%83%86%E3%83%A0web%E3%82%A2%E3%83%97%E3%83%AA%E3%82%B1%E3%83%BC%E3%82%B7%E3%83%A7%E3%83%B3%E3%82%BB%E3%82%AD%E3%83%A5%E3%83%AA%E3%83%86%E3%82%A3%E8%A6%81%E4%BB%B6%E6%9B%B8)
* [OWASP アプリケーションセキュリティ検証標準 4.0](https://www.saj.or.jp/documents/NEWS/pr/20200903_OWASP_ASVS4.0-ja.pdf)
* [Webアプリケーション脆弱性診断ガイドライン](https://github.com/OWASP/www-chapter-japan/tree/master/skillmap_project#web%E3%82%A2%E3%83%97%E3%83%AA%E3%82%B1%E3%83%BC%E3%82%B7%E3%83%A7%E3%83%B3%E8%84%86%E5%BC%B1%E6%80%A7%E8%A8%BA%E6%96%AD%E3%82%AC%E3%82%A4%E3%83%89%E3%83%A9%E3%82%A4%E3%83%B3)

## 6. Develop risk-based vulnerability response policies

### Summary
Let's decide on a vulnerability response policy based on the system architecture, information handled, cyber-attack trends, and other risks.

システムのアーキテクチャや扱う情報、サイバー攻撃のトレンドなどのリスクに応じて脆弱性の対応方針を決めよう

### Situation
* Unable to determine which vulnerabilities to address

* どの脆弱性に対応するべきか判断できない

### Problem to be solved
* Non-secure products are released with critical vulnerabilities remaining.

* 重大な脆弱性が残ったままの非セキュアなプロダクトがリリースされてしまう

### Solution
* Determine the criteria for determining the magnitude of the risk. Specifically, the following criteria are listed.
    * Set the criteria for judging the magnitude of risk using the CVSS calculation method.
        * Vulnerability risk (CVSS Base Metrics)
        * Whether the attack code is circulating or not (CVSS Temporal Metrics)
        * Whether the threat has a significant impact on the system or not (CVSS Environmental Metrics)
    * Whether countermeasures such as WAF are in place and can mitigate
* Decide on a risk response policy according to the judging criteria.
    * ex. If the vulnerability risk is CVSS 7.0 or higher, make it an immediate response.
    * ex. Decide on a response policy based on the type of vulnerability.

* リスクの大きさの判断基準を決めましょう。具体的には次のような基準が挙げられます。
    * CVSSの算出方法でリスクの大きさの判断基準を設定する
        * 脆弱性の危険度（CVSS基本評価値）
        * 攻撃コードが出回っているかどうか（CVSS現状評価値）
        * システムにとって大きな影響がある脅威かどうかで判断する（CVSS環境評価値）
    * WAFなど緩和策が導入され、緩和可能な状態かどうか
* 判断基準に応じたリスクの対応方針を決めましょう。
    * 例：CVSS7.0以上なら即日対応にする
    * 例：脆弱性の種類で対応方針を決める

## 7. Vulnerability Triage

### Summary
Let's manage tickets for discovered vulnerabilities and prioritize responses

発見した脆弱性をチケット管理し、対応の優先順位を決めよう

### Situation
* When we started vulnerability assessment, we found a large number of vulnerabilities that we could not handle within the sprint.

* 脆弱性診断を始めたところ、スプリント内で捌ききれないほどの大量の脆弱性が発見される

### Problem to be solved
* Too many vulnerabilities found to address
* Not sure which vulnerabilities to address first
* Unable to prioritize vulnerabilities found
* Unable to sort out vulnerabilities that we need to address

* 発見した脆弱性が多く対応しきれない
* 発見した脆弱性をどれから対応したら良いのかわからない
* 発見した脆弱性が多すぎて優先度付けできない
* 発見した脆弱性の内、対処が必要なものの選別ができない

### Solution
* Analyze the risk of vulnerabilities.
    * Reference: Decide on a risk-based vulnerability response policy.
* Manage tickets for vulnerabilities.
* Analyze the cost of fixing it.

* 脆弱性のリスクを分析しましょう。
    * 参考：リスクに応じた脆弱性の対応方針を決めよう
* 脆弱性をチケット管理しましょう。
* 修正のためのコストを分析しましょう。

### Reference Materials
* [セキュリティ対応組織の教科書（ISOG-J）](https://isog-j.org/output/2016/Textbook_soc-csirt_v1.0.pdf)

# Security Testing

## 8. Security testing timing and policy considerations

### Summary
Considering the characteristics of the project, let's plan the timing and content of testing so that we can adequately check the safety of the developed apps and functions!

プロジェクトの特性を考慮し、テストの実施タイミングや内容を計画しておき、開発したアプリや機能の安全性を適切に確認できるようにしよう

### Situation
* Not knowing when to conduct security testing within a project

* プロジェクト内でいつセキュリティテストを実施したら良いのかわからない

### Problem to be solved
* Inefficient development due to testing at inappropriate times.
* Security testing plans are not built-in or are inadequate. 
* Failure to meet the schedule when we perform security testing in batches before release.
* Unable to determine if we need to perform security tests case by case.

* 適切ではないタイミングでテストを行ってしまい非効率な開発が行われる
* セキュリティテストの計画が組み込まれていない。あるいは不十分である。
* リリース前にまとめて実施となった場合にスケジュールに間に合わない
* セキュリティテストを都度実施しなくていいか判断できない

### Solution
* Discuss with developers and testers and specify a security testing plan. The plan should include a schedule and outline the types and content of tests.
* Some tests may be better integrated into design and production or run automatically by CI/CD tools, while others may perform better just before release.
* Here is an example of a security testing strategy within a project.
    * Pre-development
        * Planning security diagnostics that fit the release cycle of the product
        * Decide whether to outsource pre-release vulnerability testing
    * During a sprint
        * Ensure that we implement the sprint deliverables as per the security requirements.
            * Use tools such as DAST
            * Manually diagnose areas not covered by DAST
    * Before release
        * Perform vulnerability assessment by a vulnerability assessor
    * After the start of operation
        * Scan for known vulnerabilities in the environment

* 開発者、テスターと話し合い、セキュリティテストのタイミングや実施するテストの種類、内容の概要を計画として明記します。
* テストによっては設計・製造に組み込んだり、CI/CDツールで自動実行されるようにするほうが良いものもあれば、リリース直前に実施するほうが望ましいテストもあるため、これらを抽出します。
* プロジェクト内でのセキュリティテスト戦略の一例
    * 開発前
        * プロダクトのリリースサイクルにあったセキュリティ診断の計画を立てる
        * リリース前の脆弱性診断を外注するかどうかを決める

    * スプリント中
        * スプリントの成果物が満たすべきセキュリティ要件通り実装されているか確認
            * DAST等のツールを用いる
            * DASTがカバーできない箇所を手動で診断する
    * リリース前
        * 脆弱性診断士による診断を実施する
    * 運用開始後
        * 環境の既知の脆弱性のスキャンを実施する

## 9. Formulation of test content to be conducted within the sprint

### Summary
Let's eliminate omissions from security testing by deciding which tests to perform for each sprint!

スプリントごとに行うテストを決めることで、セキュリティテストの実施漏れをなくす

### Situation
* Not sure what security tests to run within a sprint

* スプリント内でどのようなセキュリティテストを実施したら良いのかわからない

### Problem to be solved
* Necessary security tests are not being performed.
* Unnecessary security tests are being performed, resulting in high costs.

* 本来必要なセキュリティテストが行われていない
* 不要なセキュリティテストが行われていてコストがかさんでいる

### Solution
* Decide on a test to be performed for each sprint. Implement security tests that are performed automatically, such as using a scanner. The goal at this stage is not to reduce vulnerabilities to zero but to reduce them.
* Decide which tests to perform depending on the functionality you have added or modified in each sprint. Test authorization controls and business logic are not covered by the scanner manually. After identifying the security test items related to the objects created in the sprint, consider which we performed in the sprint.
* Ideally, security testing should be completed on a per-sprint basis for tests we can run on modules alone.

* 毎回のスプリントごとに実施するテストを決めましょう。スキャナーを使用するなど自動的に実施されるセキュリティテストを導入しましょう。この段階では、脆弱性をゼロにするのが目的ではなく、低減することが目的です。
* スプリントで追加・修正した機能に応じて実施するテストを決めましょう。スキャナーがカバーしない認可制御やビジネスロジックのテストは手動で行ってください。脆弱性診断ガイドラインで、スプリントで作成項目に関連したセキュリテイテストの項目を明らかにした上で、スプリント内でどのテストを行うかを考えましょう。
* モジュール単体で実行できるテストについては、スプリント単位でセキュリティテストが完了していることが理想的です。

### Reference Materials
* https://owasp.org/www-pdf-archive/Owasp_stuttgart_agile_secure_20150803.pdf

## 10. Vulnerability management for your environment

### Summary
Let's check our environment (OS, frameworks, databases, applications, libraries, etc.) for vulnerabilities that we should manage and check the status of our response!

自分たちが管理すべき環境（OS、フレームワーク、データベース、アプリケーション、ライブラリなど）に脆弱性がないかを確認し、対応状況を確認しよう

### Situation
* The state of the environment currently in use is not being managed
* No acquisition and management of the latest information on vulnerabilities after the start of operation
* Not centrally managed and kept up-to-date on vulnerabilities

* 現在利用している環境の状態が管理できていない
* 運用開始後に脆弱性の最新情報の取得と管理が行われていない
* 脆弱性の最新情報の取得と管理が一元化できていない

### Problem to be solved
* Known vulnerabilities remain in the release.

* 既知の脆弱性が残ったままリリースされている

### Solution
* Check information sources regularly.
    * JVN, JPCERT/CC, IPA, Mitre, various vendors
* Use vulnerability scanners regularly.
    * Create and maintain configuration information.
    * Software Composition Analysis (SCA)
        * Black Duck, Fortify SCA, CodeSentry, CAST Highlight, Contrast OSS, Checkmarx SCA, FlexNet Code Insight, Synk, VeraCode, ASoC
    * Vulnerability Scanners
        * Vuls, Nessus, yamory, OpenVAS (GVM)
    * Container vulnerability management
        * Trivy, Tenable.io

* 情報源を定期チェックしましょう。
    * JVN, JPCERT/CC, IPA、Mitre、各ベンダー
* 脆弱性スキャナを定期的に利用しましょう。
    * 構成情報を作成、管理する
    * ソフトウェア・コンポジション解析（SCA）
        * Black Duck、Fortify SCA、CodeSentry、CAST Highlight、Contrast OSS、Checkmarx SCA、FlexNet Code Insight、Synk、VeraCode、ASoC
    * 脆弱性スキャナ
        * Vuls、Nessus、yamory、OpenVAS(GVM)
    * コンテナの脆弱性管理
        * Trivy、Tenable.io

## 11. Automated security testing

### Summary
It is necessary to introduce automation tools for executing security testing efficiently. Let's select the best automation tool appropriate for your development environment and system and implement it efficiently!

セキュリティテストを効率よく実施するためには自動化ツールの導入が必要となります。開発環境、体制にとって適切な最適な自動化ツールを選択し、効率的に実施しよう

### Situation
* Security testing is time-consuming
* All security testing is done manually
* Security testing is not done efficiently

* セキュリティテストに時間が掛かる
* セキュリティテストをすべて手動で行っている
* セキュリティテストを効率的に行えていない

### Problem to be solved
* Web application vulnerabilities are not found efficiently within a sprint
* Required security tests are not completed within a sprint
* Security testing quality is inconsistent

* スプリント内でWebアプリケーションの脆弱性が効率よく見つからない
* スプリント内で必要なセキュリティテストが終わらない
* セキュリティテストの品質にばらつきがでる

### Solution
* Scanners can find not all vulnerabilities, but scanners can improve efficiency in finding some vulnerabilities.
* The best automation tool depends on the development environment, system, and operation method. The following considerations should be taken into account when determining the appropriate tool.
    * Is it easy to integrate into your development process?
    * Fewer false positives in vulnerability detection.
    * Ease of triage of vulnerabilities
    * Can it diagnose the target you want to diagnose?
    * Is it easy to operate and use?
    * Is it cost-effective?
    * Support system of the tool
* DAST: Use a vulnerability scanner
    * Open source: OWASP ZAP
    * Commercial: Vex (UBsecure), AeyeScan (Aeye Security Lab), AppScan（HCL)
    * Efficient if performed on functions that were added or modified during the sprint
* Let's use SAST.

* すべての脆弱性がスキャナーで発見できる訳ではありませんが、スキャナーを利用することで一部の脆弱性発見について効率化が図れます。
* 開発環境、体制、運用方法によって最適な自動化ツールは異なります。以下の観点で適切なツールを決定しましょう。
    * 自分たちの開発工程に組み込みやすいか
    * 脆弱性の誤検出が少ないか
    * 脆弱性のトリアージがしやすいか
    * 診断したい対象を診断できるか
    * 運用しやすいか・使いやすいか
    * 費用対効果に見合うか
    * ツールのサポート体制
* DAST：脆弱性スキャナを利用しよう
    * オープンソース: OWASP ZAP
    * 商用:Vex(ユービーセキュア社)、AeyeScan(エーアイセキュリティラボ)、AppScan（HCL)
    * スプリント内で追加・修正があった機能に対して実施すると効率が良い
* SASTを利用しよう

### Reference Materials
* [OWASP ZAP](https://www.zaproxy.org/)
* [Vex](https://www.ubsecure.jp/vex)
* [AeyeScan](https://www.aeyescan.jp/)
* [AppScan](https://www.hcljapan.co.jp/software/products/appscan/)
* [Burp Enterprise](https://portswigger.net/burp/enterprise)

# Security Quality Improvement

## 12. Reflection on Continuous Improvement of Security

### Summary
In the iterative development process, let's also review the process of implementing security using retrospectives to improve the security of services and products!

反復的に繰り返される開発の中で、レトロスペクティブなどを活用し、セキュリティを実装するプロセスも見直しを行い、サービス・プロダクトのセキュリティを向上させよう

### Situation
* The same vulnerabilities are repeatedly created in each sprint.

* スプリントごとに同じような脆弱性が繰り返し作り込まれてしまう

### Problem to be solved
* Want to reduce the number of vulnerabilities detected by security tests
* Cost of vulnerability response not decreasing or increasing
* Prevent rework

* セキュリティテストで検出される脆弱性を減らしたい
* 脆弱性対応にかかるコストが減らない、あるいは増大していく
* 手戻りの防止

### Solution
* Utilizing the Sprint Retrospective, review the security implementation and security tests conducted during the sprint.
    * The developers will take the lead, and the Scrum Master will assist.
* The team will also discuss security-related aspects and identify and implement items to be improved in the next sprint and beyond. Here is an example.
    * Review of coding rules
    * Review of testing methods
    * Review of member awareness
    * Review of vulnerability handling criteria
    * Review of resource allocation

* スプリントレトロスペクティブを活用し、スプリント内で実施されたセキュリティ実装・セキュリティテストを振り返ります。
    * 開発者が中心となって行い、スクラムマスターは支援します。
* 例えば以下のテーマで、セキュリティに関係する部分も話し合い、次のスプリント以降で改善すべき項目を抽出し、実行していきます。
    * コーディングルールの見直し
    * テスト方法の見直し
    * メンバーの意識の見直し
    * 脆弱性対処基準の見直し
    * リソース配分の見直し

