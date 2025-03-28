# Windows Serverシステム管理

# Webアクセス手順

## ラボ シナリオ

この手順は「Windows Server システム管理」の演習へWebブラウザを使用してアクセスする場合に使用する手順です。

講師より入手したアカウントを使用して、演習環境へアクセスしてください。

※演習環境はMicrosoft Azureの「Virtual Machine」サービスを使用しています

<br>

## 目標

+ タスク1：Azure Portalへサインインする
+ タスク2：演習環境にアクセスする

<br>

予想時間: 5分

### Azure Bastion(演習環境）のアクセス手順

1.以下のURLにアクセスしてください。
https://bst-3492a27e-eb2e-4c2b-bce4-d19ccc8025d7.bastion.azure.com/api/shareable-url/accd250a-0299-4f1b-ba28-383dc212e414

<img src="./media/image14.png" alt="rdp1" width="200" style="float:left; margin-right: 10px;">



2.Azure Bastion画面が表示されます。以下の内容を入力し「login」をクリックします・
　

| 項目              | 値             |
| ----------------- | -------------- |
| Protocol          | `RDP`          |
| Username          | `ctct`         |
| Password          | `Pa55w.rd1234` |
| keyboard Language | `Japanese`     |

<img src="./media/image15.png" alt="rdp1" width="200" style="float:left; margin-right: 10px;">

3.演習環境（Windoes Server)の画面が表示されます。

<img src="./media/image15.png" alt="rdp1" width="200" style="float:left; margin-right: 10px;">

※注意点※
 パスワードが違うと「Connection Error」になります。
 演習環境のアクセスするパスワードは[Pa55w.rd1234]です。
 SV01などの仮想マシンのパスワードは[Pa55w.rd]と異なります。

これで演習環境へのアクセスが完了しました。

以降は講師の指示に従い、テキストの演習手順を実施してください。

------

**【参考】Microsoft Azureにご興味のある方向け**

本研修で使用する演習環境はMicrosoftのクラウドプラットフォーム「Microsoft Azure」を使用しています。

Azureサービスの「Virtual Machine (仮想マシン)」を使用してクラウド上 (Microsoftのデータセンター)にWindows Serverを構築しています。

> Azure での仮想マシン： https://learn.microsoft.com/ja-jp/azure/virtual-machines/overview

<br>

この仮想マシンへアクセスする場合、Windowsではリモートデスクトップ接続を行います。

ネットワークはパブリックインターネット経由、VPN経由、専用線接続(閉域網)でアクセスを行います。

パブリックインターネットで接続する場合、リモートデスクトップ接続(RDP：3389ポート)を解放する必要があります。

ですが、第三者からの攻撃によりRDPポートを攻撃され仮想マシンが乗っ取られる可能性もあります。

> リモート管理の脅威：https://learn.microsoft.com/ja-jp/azure/security/fundamentals/management#remote-management-threats

<br>

そのため、RDPポートはファイヤーウォールなどによりブロックすることが一般的です。

> この演習環境においてはRDPポートは解放しています。

あるいは、社内ネットワークからデータの不正流出を防ぐために、ネットワーク自体でRDPポートを遮断(ファイヤーウォールなど)することがあります。

<br>

その場合、メンテナンスや操作などにおいて、RDP接続が出来ない状態になります。

そこで使用するのが、RDP(3359)の接続ではなく、Webブラウザ経由のTLS(443)を使用したアクセス方法があります。

それが、今回操作して頂いた「Azure Bastion」というサービスになります。

> Azure Bastion とは：https://learn.microsoft.com/ja-jp/azure/bastion/bastion-overview

![architecture](./media/architecture.png)

<br>このサービスは、Bastionが踏み台コンピュータとなります。

インターネット上に仮想マシンのグローバルIPアドレスを公開することなく且つ、Webブラウザ経由でセキュアに通信を行うことが可能です。



