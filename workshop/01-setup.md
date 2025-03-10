![Amazon Q Developer header](/images/q-vscode-header.png)

## セットアップとAmazon Q Developerの利用開始

私たちは今、このワークショップの最初のハンズオンの準備ができました。
Amazon Q Developerを使用します。
Amazon Q Developerは次世代の開発者ツールで、インラインでのコード提案やチャットインターフェースを提供し、開発フローを支援します。
Amazon Q Developerはプラグインを介してIDE（VSCodeとIntelliJがサポートされています）にインストールされます。
プラグインをインストールしたら、Builder IDアカウントと呼ばれるものを使用してログインする必要があります。
これにより、AWSアカウントなしでAmazon Q DeveloperのFree Tierにアクセスできるようになります。
そのため、まずBuilder IDを設定し、Amazon Q Developerプラグインをインストールする必要があります。

**Builder IDの作成**

(すでにBuilder IDを持っている場合、この手順はスキップできます)

[Builder ID の作成](https://s12d.com/builder-id) は、Amazon Q Developer プラグインを使用できるようにするための最初のステップです。
Builder IDを作成するために必要なのは、有効なメールアドレスだけです。
[Builder IDページ](https://s12d.com/builder-id)に移動し、[Sign in with Builder ID]をクリックします。
ブラウザウィンドウが表示され、メールアドレスを使用して Builder ID を作成できます。

以下のスクリーンショットを参考に手順を確認してください。
Builder IDページにアクセスした後、電子メールアドレスを入力し(1)、エイリアス（Your Name）を作成する必要があります(2)。
確認メールが送信されるので、それを入力する必要があります(3)。
メールは数分で届くはずです（ただし、念のためSPAMフォルダをチェックしてください）(4)

![Builder IDの作成手順](/images/q-vscode-builderid-1.png)

このコードを受け取ったら、それを入力してアカウントを検証し(5)、確認が行われます(6)。
初期画面に戻り、Eメールアドレス(7)とパスワード(8)を入力すると、ビルダープロフィールのページ(9)が表示されます。

![Builder ID取得完了](/images/q-vscode-builderid-2.png)

AWSのサービスを利用する際にBuilder IDという言葉を耳にすることがあると思いますが、これはそこで言及されているアカウントです。
AWSアカウントとは別のものですが、AWSのフルアカウントを必要とせずにAWSを試したい人にアクセスを提供するために、多くのサービスで使われています。

> **Builder IDからログアウトする** ビルダー ID からログアウトする必要がある場合があります。そのためには、[Buildr ID プロフィールページ](https://profile.aws.amazon.com/#/profile/details) に移動し、左上の **Sign Out** ボタンを使用してください。これをクリックすると、サインオンページに戻ります。

**Amazon Q Developerのインストール**

Builder ID プロファイルができたので、Amazon Q Developer プラグインをインストールしましょう。
Extensionsのサイドバーから、アイコンをクリックしてExtensions Marketplaceを表示します。
「Amazon Q Developer」で検索すると、Amazon Q Developerプラグインが見つかるはずです(1)。
執筆時点での最新バージョンはv1.37.0です。
このプラグインは非常に定期的にアップデートされるので、自動アップデートを利用するか、定期的にチェックインして週単位で行われている改善を利用するようにしてください。

![Amazon Q Developerプラグインのインストール](/images/q-vscode-install-1.png)

インストールが正常に完了すると、いくつかのものが表示されます。
まず、左側のサイドバーに新しいQのアイコンが表示され(1)、下にはAmazon Qのステータスバーが×印で表示されます(2)

![Amazon Q Developerが無事にインストールされた](/images/q-vscode-install-2.png)

この×印をクリックすると、現在サインインしていないことを示すメニューがポップアップ表示されるはずです。次にそれを実行します。

**Amazon Q Developerにサインインする**

さて、[Builder ID](https://s12d.com/builder-id) を作成し、Amazon Q Developer プラグインをインストールしたので、最後のステップとして、その [Builder ID](https://s12d.com/builder-id) を使ってログインします。

先ほどのスクリーンショットから、QアイコンをクリックするとAmazon Qメニューが表示されます(3)。
それをクリックすると、Amazon Q Developerのログインオプションが表示されます(4)。
2つの選択肢がありますが、「Use with Pro Licence」は無視して、「Use for Free」のボックスをクリックし、「Continue」をクリックします。
ポップアップボックスが表示されます(5)。
参照コードをメモし、「ブラウザに進む」をクリックすると(6)が表示されます。
前のステップと同じコードであることを確認し、「Confirm and Continue」をクリックします。
問題がなければ、「Allow Access」をクリックし、成功すれば最後の画面(8)が表示されます。

> **Note!** VSCodeの左下に、Amazon Qプラグインがあなたのウェブページを開いたという情報パネルがあることにお気づきかもしれません。ログインが完了すると自動的に閉じます。

![Amazon Q DeveloperにBuilder IDを使ってログインする](/images/q-vscode-signin-1.png)

ログインすると、いくつかのことがわかります。
まず、左側のQパネルがチャットウィンドウに変わります。
また、下部にあるAmazon Qのステータスバーが "X Amazon Q "から"|> Amazon Q "に変わっていることに気づくでしょう。
これをクリックすると、AWS Builder IDを使ってAmazon Qにログインしていることがわかります。

![サインインの完了](/images/q-vscode-signin-2.png)

これでセットアップはすべて完了し、準備は整いました。

> **ログアウト** ログアウトしたい場合は、Amazon Qのステータスバーのリンクをクリックしてメニューを表示し、「サインアウト」オプションを選択するだけです。その後、上記のプロセスを繰り返して、必要に応じてサインインし直すことができます。

**Amazon Q Developerの設定**

ワークショップを進める前に、Amazon Q Developerをどのように設定し、あなたの要件に合わせることができるかを説明する価値があります。
左のアイコンバーの拡張機能アイコンから、Amazon Q Developerプラグインの横にある歯車をクリックすると、設定できる項目が表示されます。
これは、後で変更したい場合に便利です。
当面はこのままにしておきましょう。

![Amazon Q Developerの設定](/images/q-vscode-settings-1.png)
![Amazon Q Developerの設定](/images/q-vscode-settings-1b.png)

これですべてのセットアップが完了したので、次のステップに進みます。
次は「[Amazon Qの始め方を調べる](02-getting-started-with-q.md)」です。

