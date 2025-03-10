![Amazon Q Developer header](/images/q-vscode-header.png)

## Amazon Q Developerを使ってみる

すべての開発者ツールと同様に、生産性を最大化するために、少し時間を費やしていろいろと試してみて、どのように機能するかを確認ことには価値があります。
この節では、Amazon Q Developerが提供するものを大まかに説明しますが、ぜひみなさんもいろいろと試してみてください。

**Amazon Q Developerメニューのオプション**

VSCodeの下部にあるAmazon Qステータスバーのリンクをクリックすると、以下のポップアップが表示されます。
このポップアップではAmazon Q開発者オプションにアクセスできます。
それぞれのオプションが提供するものを見ていきましょう。

![Amazon Q Developerメニューのオプション](/images/amazon-q-developer-plugin-menu.png)

* 自動提案を一時停止する（現在実行中） - Amazon Q Developerは、あなたのコードで直接作業している間、提案されたコードブロックとスニペットを提供します。このリンクをクリックすることで、この動作をオフにできます（その後、「自動提案を再開する」、「現在停止中」に変わり、下のステータスバーのAmazon Qアイコンも変わります）。開発者によって、このオプションを無効にした方がいい人もいれば、有効にした方がいい人もいます。一時停止中でも、VSCodeショートカット（OPTION + C）を使うことで、Amazon Q Developerを呼び出してインライン コード サジェストを提供できます。キーボードのショートカットについては、次の節で紹介します。
* オープンコードリファレンスログ - Amazon Q Developerを動かすために使用される基礎モデルは、Apache 2.0とMITライセンスのソースファイルを使用して、いくつかのオープンソースコードリポジトリを使用しています。コードの提案にこれらのプロジェクトからの部分が含まれる場合、Amazon Q Developerは、このメニューオプションをクリックして開くことができる「コード参照ログ」に出力することであなたに知らせます。これをクリックすると、「Don't want suggestions that include code with references? Amazon Q: Settings」でこのオプションのチェックを外してください。Builder IDを使用している場合、この設定を変更することはできず、デフォルトのオプションは常にコード参照を含む提案を含むようになっています。Amazon Q Developerを使用する際には、オープンソースリポジトリからのコードを使用しているかどうかを確認するために、ときどきここをチェックしてください。
* インラインサジェスト例を試す - Amazon Q Developerのインラインサジェストの使い方の基本を説明する簡単なチュートリアルです。
* フルプロジェクトスキャンが /review になりました - これは現在のプロジェクトの /review をキックオフします。このチュートリアルの後半で詳しく説明します。
* チャットパネルを開く - Amazon Q Developerのチャットパネルを閉じている場合に開きます。
* フィードバックの送信 / GitHubを確認する / ドキュメンテーションの表示 - これらのオプションは、Amazon Q Developerが思うように動作しない場合にフィードバックを提供するための追加の方法を提供します。
* 設定を開く - Amazon Q Developerプラグインの設定オプションを開きます。
* サインアウト (AWS Builder IDで接続中) - IDを表示したまま、現在のセッションからログアウトできます。このワークショップでは、常に AWS Builder ID となります。

---

**キーボードショートカット**

さまざまなショートカットキーを使って、Amazon Q Developerの起動方法や動作をコントロールできます。

![Amazon Q Developerのショートカット](/images/q-vscode-view-keyboard.png)

インラインエディターで作業している時に知っておくべき重要なショートカットの一つは、 < と > （左右）の矢印です。これらは、Amazon Q Developerによってプロンプトが表示されたときに、候補を循環させることができます。

---

**チャットインターフェイス**

下の Amazon Q ステータスバーのリンクをクリックすることでチャットパネルを開くことができ、デフォルトでは他のアプリケーションの成果物（開いているファイル、Git ファイルなど）と一緒に左側に表示されます。
下のスクリーンショットのように、チャットパネルを右側にドラッグすると、プロジェクト内のファイルや編集中のファイルを見つつチャットインターフェイスが見られて、個人的には便利だと思います。

![Amazon Q Developerチャットインターフェイス](/images/q-vscode-screen-layout.png)

`+` をクリックすると複数のチャットセッションを開くことができます。
Amazon Q Developerを使用する場合、プラグインは会話を記憶し、その後の応答でそれを使用します。
これは、Amazon Qを使用して問題の解決やトラブルシューティングを行う際に非常に便利です。
このワークショップでは、これをずっと見ていきます。
これらの異なるタブや会話を10個まで開くことができます。

Amazon Q Developerには、`/` を使った以下のような強力な機能もあります。

* **/** 利用可能なコマンドのリストが表示されます。Amazon Q Developerの機能が増えるにつれて、ここに追加で表示されるようになります。
* **/clear** 現在のチャットウィンドウの会話履歴をクリアします。応答が回りくどくなったり、会話のコンテキストをリセットしたい場合に便利です。
* **/dev** これで、ファイルの作成、新機能の追加、テストの追加、ドキュメントの作成などができます。これはAmazon Q Developerのもっとも強力な機能の1つで、あなたのプロンプトを受け取り、タスクに分解し、リアルタイムでさまざまなタスクを通して作業を開始します。あなたのプロジェクトを理解するためにワークスペース内のファイルを探索し、どのファイルを確認し使用したか、変更したいファイル、新しく作成したファイルを共有します。終了すると、これらの更新を確認、チェックし、必要に応じて承認できます。
* **/transform** は、Java 8プロジェクトをJava 17に移行し、アプリケーションを最新化する手間を省くのに役立つ、Amazon Q Developer Agent for transformation を呼び出します。このワークショップでは使用しませんが、古いJavaアプリケーションを使用している場合は知っておく価値があります。
* **/review** Amazon Q Developer Agentを呼び出し、現在のプロジェクトのレビューを実行します。これは Amazon Q Developer プラグインにあったセキュリティスキャン機能を置き換えるものです。
* **/doc** プロジェクトのREADMEを生成するAmazon Q Developer Agentを起動し、READMEファイルを作成または更新することができます。
* **/test** 関数に対する単体テストを生成する Amazon Q Developer Agent を起動します。これは現在JavaとPythonのコードでのみ動作します。

**Note!** Builder IDで /dev と /transform を使用する場合、クォータに制限があります。詳しくは公式の[Amazon Q Developer pricing page](https://aws.amazon.com/q/developer/pricing/)をご覧ください。下へ半分ほどスクロールすると、制限の概要が書かれた表があります。

---

**メニューバーへの統合**

Amazon Q Developerは、エディタ内でコードを作業しているときに、Amazon Qを呼び出して多くの機能を実行する便利な方法を提供します。
ファイル上で作業している時、コードの一部分、もしくは全体を選択し、右クリックすると「Send to Amazon Q」メニューオプションが表示され、選択するとさまざまなオプションが表示されます。

![Amazon Q Developerエディタメニュー](/images/q-vscode-editor-menu.png)

* Explain - ハイライトした内容をAmazon Qのチャットパネルに送信し、Amazon Qにこのコードが何をするのかを説明するよう依頼します。
* Refactor - スニペットをレビューし、コードの可読性や効率性を改善する方法を提案します。
* Fix - あなたのコードにlintエラーがあったり、コードの他の問題を解決しようとしている場合に便利です。
* Optimise - 選択したコードのパフォーマンスを最適化できるかどうかを確認します。
* Generate Tests - 現在の関数やクラスをハイライトし、チャットインターフェースから /test を呼び出します。そして、その関数やクラスのユニットテストを生成するための手順を説明します。
* Send to Prompt - 選択した部分をコピーし、Amazon Q Developer Chatパネルに移動します。その後、Amazon Q Developer に何をさせたいか、あなた自身のプロンプトを提供できます。これは自分でコードスニペットをコピー/ペーストするよりも簡単な方法です。
* Inline Chat - 編集中のファイル内に小さなダイアログボックスが表示され、プロンプトを入力できます。Amazon Qはコードを生成し、それを受け入れるか拒否するかを尋ねます（受け入れるにはEnterを、拒否するにはESCを押してください）。

![インラインチャットウィンドウの例](/images/q-vscode-inline-chat.png)
![インラインチャットの応答の例](/images/q-vscode-inline-chat-example.png)

---

**Amazon Q Developerのログ**

Amazon Q Developerプラグインはログを生成し、VSCodeのターミナル節で表示されるOUTPUTメニューオプションからアクセスできます。
プルダウンメニューを選択すると、**Amazon Q Logs** が表示されます。
これは、プラグインがどのように動作し、Amazon Bedrockによって提供されるバックエンドの生成AIサービスと相互作用しているかについての詳細な情報を提供します。
ここで取得される重要な情報の1つは**ConversationID**で、プラグインのインタラクションを追跡し、Amazon Web Servicesのサポートとやりとりする場合に役立ちます。

---

**ワークスペース インデックス**

Amazon Q Developerでは、ローカルのワークスペースのインデックスを作成でき、それをチャットインターフェイスを使用する際のコンテキストの一部として使用できます。
これは非常に強力な機能で、Amazon Q Developerからのアウトプットの方向性を決めるのに役立つ追加情報を持ち込むことができます。
たとえば、Amazon Qによって生成されるコードに影響を与えたい既存のコーディング標準があるかもしれません。
`.qdeveloper` フォルダにいくつかの例があります。
2つのファイルがあり、1つは "java-expert.md"、もう1つは "opensource.md "です。
これらには出力のフォーマットを決める追加のプロンプトが含まれています。
これを使う一般的な方法は、より短い出力を作成することで、おそらく説明よりもコードだけを出力することです。

この機能はAmazon Q Developerのチャットインターフェイスから使用します。
`@` で呼び出すと、利用可能なオプションが表示されます。
現在は `@workspace` のみです。

![ワークスペース インデックスを有効にするAmazon Q Developerプラグインの設定オプション](/images/q-workspace-settings.png)

有効にしたら、VSCode を再起動する必要があります。
再起動すると、OUTPUT タブから、Amazon Q Logs をチェックすることで、ワークスペース インデックスからの出力を確認できます。

```
2025-02-13 18:05:35.784 [info] LspController: LSP already installed
2025-02-13 18:05:36.022 [info] [Info  - 18:05:36] LSP server starts
2025-02-13 18:05:36.214 [info] [Info  - 18:05:36] Loaded model from /Users/ricsue/.vscode/extensions/amazonwebservices.amazon-q-vscode-1.46.0/resources/qserver
2025-02-13 18:05:36.357 [info] [Warn  - 18:05:36] Unknown tokenizer class "CodeSageTokenizer", attempting to construct from base class.
2025-02-13 18:05:36.415 [info] [Info  - 18:05:36] Device is not connected to power source. Set thread to 1.
2025-02-13 18:05:36.415 [info] [Info  - 18:05:36] Using number of intra-op threads: 1
2025-02-13 18:05:36.663 [info] [Info  - 18:05:36] Embedding provider initialized.
2025-02-13 18:05:36.668 [info] LspController: LSP activated
2025-02-13 18:05:36.668 [info] LspController: Starting to build index of project
2025-02-13 18:05:36.758 [info] LspController: Found 18 files in current project /Users/ricsue/Projects/amazon-q/workshop-2025/amazon-q-developer-hands-on
2025-02-13 18:05:36.768 [info] [Info  - 18:05:36] start building bm25 index
```

プロジェクトの規模によっては、時間がかかるかもしれません。
終了すると、ログにメッセージが表示されます。

```
2025-02-13 18:05:57.838 [info] [Info  - 18:05:57] Vector indexing done for 15/18 files
2025-02-13 18:05:58.842 [info] [Info  - 18:05:58] Vector indexing done for 16/18 files
2025-02-13 18:06:02.106 [info] [Info  - 18:06:02] Vector indexing done for 17/18 files
2025-02-13 18:06:02.106 [info] [Info  - 18:06:02] Vector index complete! Take 25.156545917s. Total 18 files, 63 chunks
2025-02-13 18:06:02.106 [info] [Info  - 18:06:02] Vector index saved to /Users/ricsue/.aws/amazonq/cache/cache/b34d763123948282822a796f54a637adac670c8b30f241c6a4c21195679dde96-0.9-VSCode.index
```

インデックス作成が完了すれば、 `@worksplace` はすぐに使えるようになります。

ファイルを更新/削除すると、インデックスが自動的に更新されます。

```
2025-02-13 18:01:24.084 [info] Refreshing indexes...
2025-02-13 18:01:24.085 [info] [Info  - 18:01:24] Finished parsing 9 python files. Time 30.98ms
```

---

## Amazon Q Developer

Amazon Q Developerには便利なツールがたくさんありますが、どれを使えばいいのか迷ってしまいますよね。
答えは、あなたが行っている作業の種類によります。
ここでは、ある作業に対して何が適切なツールかを判断するのに役立つ、考慮すべき点をいくつか紹介します。

**Amazon Q Developerのどのツールを使うべきか**

どのツールを使うかは、さまざまな要因によります。

* 各ツールがどのようなコンテキストで使用できるか（ファイルかプロジェクトか）
* インライン編集は開発者にとってより速く、より直感的です
* Amazon Qの開発者向け機能には制限とクォータがあるため、もっとも効果的なときに使用すること
* タスクが必要とする労力は考慮しなければなりません。たとえば、プロジェクトに大きな変更を加えたい場合、手作業で行うには多大な労力がかかります。
* あなたは何かを学んでいますか。チャットは新しい分野を学ぶのに適しており、インラインは生産性を高めるのに適しています。

これについては、次のステップで詳しく説明します。

---

### Amazon Q Developer - ガードレール

この最後の節では、Amazon Q Developerを使用する際におそらく遭遇することになるであろう、[AWS 責任ある AI ポリシー](https://aws.amazon.com/machine-learning/responsible-ai/policy/)について見ていきます。

Amazon Q Developerをさまざまなモダリティ（チャット、/dev、@workspace、またはインライン）で使用し、やりとりしていると、出力が停止し、メッセージが表示されることがあります。

![Guardrailのメッセージ](/images/q-vscode-guardrail.png)

メッセージの内容は異なるかもしれません。たとえば、VSCodeの右下に表示されるエラーポップアップなどです。

![Guardrail tripping](/images/q-vscode-error.png)

もしこのようなことに遭遇したら、以下を試してみてください。

* プロンプトを調整する - 別の単語を使ったり、順番を変えたりする。
* リポジトリ内の異なるファイルに対してテストする - ときにはガードレールに引っかかるのは1つのファイルだけということもあるので、Amazon Qが引っかかる場所を絞り込むことができます。
* Amazon Qのログを確認し、根本的な問題の特定に役立つ情報がないか確認する。

ガードレールはAmazon Qのユーザーにとって重要な保護手段であり、何が有効で何がつまずくかの関係は常に変化しています。

### サンドボックスで手を動かす

次のステップでは、これらがどのように機能するかを詳しく説明します。
[Amazon Q Developerの練習](03-sandbox.md)へ進んでください。


