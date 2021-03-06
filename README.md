# ASP.NET Core と Azure Web Apps でできる！簡単 Web サイト作成＆公開デモ
 LTで紹介した ASP.NET Core  Web アプリ公開デモの手順書です。</br>
 実際に手を動かしてみたい方向けの手順書になります。

# 手順の概要
ASP.NET Core のプロジェクトテンプレートを使用して Web ページを作成し、Azure Web Apps で公開します。必要な手順は大まかに分けて 3 ステップになります。

1. ASP.NET Core のプロジェクト作成
2. GitHub リポジトリへのプッシュ
3. Azure Web Apps のインスタンス作成

たったこれだけで Web ページを公開できます。所要時間は5分ほど（GitHub ワークフローで2分弱）です。

## STEP1 ASP.NET Core プロジェクト作成

まず、プロジェクトを作成するには Visual Studio の機能で「ASP.NET と Web 開発」が必要です。導入できていない方は Visual Studio Installer からセットアップしてください。

![](Images/00.png)

1. Visual Studio にて「新しいプロジェクトの作成」を選択

![](Images/01.png)

2. 「ASP.NET Core Web アプリ」を選択

![](Images/02.png)

3. プロジェクト名を適当に決めて次へ

![](Images/03.png)

4. フレームワークは最新のものを選択して作成

![](Images/04.png)

5. `Page` ディレクトリ内にある `Index.cshtml` を開いて、一部プログラムを追記してみる。

![](Images/05.png)

これでプロジェクトの作成は完了です。

## STEP2 GitHub リポジトリへのプッシュ

1. 上部のタブから「Git」を選択し、「Gitリポジトリの作成」をクリック

![](Images/11.png)

2. 「作成とプッシュ」をクリック（プライベートリポジトリでもOK）

![](Images/12.png)

3. タスクが完了していることを確認

![](Images/13.png)

## STEP3 Azure Web Apps のインスタンス作成

1. Azure ポータルを開く

2. リソースの作成をクリック

3. Web アプリを選択（一覧になければ検索してください）

![](Images/21.png)

4. 必要事項へ記入する

名前はアドレスになります。 ランタイムは先程作成した ASP.NET Core のフレームワークに合わせてください。

|項目|記入例|
|--|--|
|サブスクリプション|Azure for Students|
|リソースグループ|rg-mstechcamp|
|名前|takunology-web|
|公開|コード|
|ランタイムスタック|.NET 6|
|オペレーティングシステム|Windows|
|地域|Japan East|
|Windows プラン|そのまま|
|SKUとサイズ|Free F1|

![](Images/22.png)

SKU とサイズに関しては `サイズを変更します` のリンクから選択することができます。

![](Images/23.png)

「開発/ワークロード」から無料プランを選択し、適用をクリックすると無料で作ることができます。

1. 「次:デプロイ」をクリック

2. 継続的デプロイを有効化し、GitHub と連携する

3. 先程プッシュしたリポジトリを選択して「確認および作成」をクリック

![](Images/24.png)

8. 内容を確認して「作成」をクリック

![](Images/25.png)

9. 「リソースに移動」をクリック

![](Images/26.png)

これでリソースの作成と GitHub との連携は完了です！

## Web ページの確認

インスタンス作成時に、GitHub のワークフローが動いていますので、リポジトリに移動して確認してみます。プッシュしたリポジトリから `Actions` をクリックすると、実行中のワークフローが表示されます。

![](Images/27.png)

画像のように、チェックマークが入っていればデプロイが完了し、Webサイトが公開されています。</br>

Azure のリソースから、「参照」をクリックしてみてください。

![](Images/28.png)

先程作成した Web ページが公開されています。URLは `azurewebsites` ドメインとなります。

![](Images/29.png)

これで、Web ページの作成&デプロイは完了です！</br>

Web ページを更新したらリポジトリにコミットして GitHub にプッシュするだけで即座に Azure Web Apps へデプロイされます。

## リソースの削除
Web ページを運用する必要がなくなった場合は Azure のリソースを削除しましょう。</br>

Azure ポータルから「リソースグループ」を選択し、今回作成したリソースグループ名を選択します。（この例では `rg-mstechcamp` です。）

![](Images/31.png)

「リソースグループの削除」をクリックすると、確認のダイアログが表示されるので、リソースグループ名を入力してから「削除」をクリックします。

![](Images/32.png)
