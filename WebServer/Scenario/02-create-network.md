## ネットワークの設定

### リージョンの選択
画面右上の「サポート」の左隣にあるドロップダウンリストから、環境を構築するリージョンを選択出来ます。  
本シナリオでは東京リージョンを使用いたしますので、「アジアパシフィック(東京)」を選択してください。

[![https://gyazo.com/06a9f329d0fbd99aa00a8b99bd632a06](https://i.gyazo.com/06a9f329d0fbd99aa00a8b99bd632a06.gif)](https://gyazo.com/06a9f329d0fbd99aa00a8b99bd632a06)

### VIrtual Private Cloud(VPC)の作成
以降の手順によって、仮想的なプライベートクラウド環境を作成します。

AWSマネジメントコンソールのトップ画面左下のVPCアイコンをクリックし、VPCダッシュボード画面に移動します。

[![https://gyazo.com/29ec4d1d3c4136a6d3c9acb019ac9078](https://i.gyazo.com/29ec4d1d3c4136a6d3c9acb019ac9078.png)](https://gyazo.com/29ec4d1d3c4136a6d3c9acb019ac9078)

*VPCダッシュボード画面*

VPCダッシュボード画面では、VPCに関連するサービスの設定を行うことができます

[![https://gyazo.com/3a74285d879569dd35ea7d88be0fcc29](https://i.gyazo.com/3a74285d879569dd35ea7d88be0fcc29.png)](https://gyazo.com/3a74285d879569dd35ea7d88be0fcc29)


### VPCネットワークの作成
VPCで使用するプライベートネットワークアドレスの範囲を設定します。  
**(注意)** VPCネットワークアドレスは一度設定すると後から変更できないので、後々のシステム拡張等も踏まえて余裕を持った範囲を設定してください。

まず、左側のリストにある「VPC」をクリックし、VPC一覧画面を表示します。
[![https://gyazo.com/b5f1d621292b5de3cbc0a60d44963a4d](https://i.gyazo.com/b5f1d621292b5de3cbc0a60d44963a4d.png)](https://gyazo.com/b5f1d621292b5de3cbc0a60d44963a4d)

左上の「VPCの作成」ボタンをクリックすると、「VPCの作成」ウィザードが表示されます。  
ウィザードにて、下記情報を入力します。  
※本シナリオでは、XXの部分は自身のユーザ名の下二ケタを設定してください。  
（なお、入力値は任意のものであっても問題ありません。）

| 項目 | 設定値 
|:-----------|:------------|
| ネームタグ  | vpc-userXX 
| CIDRブロック  | 192.168.XX.0/24 
| テナンシー | デフォルト

[![https://gyazo.com/4d57d7b9ab7582e1d70d577948e97a75](https://i.gyazo.com/4d57d7b9ab7582e1d70d577948e97a75.png)](https://gyazo.com/4d57d7b9ab7582e1d70d577948e97a75)


入力が完了したら、「作成」ボタンをクリックしVPCを作成します。

一覧に作成したVPCが表示され、状態が「available」になっていれば、作成完了になります。

[![https://gyazo.com/b2a275a1cc4b6e787ddfa544fd95956a](https://i.gyazo.com/b2a275a1cc4b6e787ddfa544fd95956a.png)](https://gyazo.com/b2a275a1cc4b6e787ddfa544fd95956a)

### サブネットの作成
左側のリストにある「サブネット」をクリックし、サブネット一覧画面を表示します。

[![https://gyazo.com/d2b4bbf57578602d8c804b719ea4add9](https://i.gyazo.com/d2b4bbf57578602d8c804b719ea4add9.png)](https://gyazo.com/d2b4bbf57578602d8c804b719ea4add9)

左上の「サブネットの作成」ボタンをクリックすると、「サブネットの作成」ウィザードが表示されます。  
ウィザードにて、下記情報を入力します。  
※本シナリオでは、XXの部分は自身のユーザ名の下二ケタを設定してください。  
（なお、入力値は任意のものであっても問題ありません。）

| 項目 | 設定値 
|:-----------|:------------|
| ネームタブ  | subnet-userXX  
| VPC  | 先ほど作成したVPCを選択 
| アベイラビリティゾーン  | ap-northeast-1a
| CIDRブロック | 192.168.XX.0/26 

[![https://gyazo.com/339b57fde0866810d25ae6967c92dbed](https://i.gyazo.com/339b57fde0866810d25ae6967c92dbed.png)](https://gyazo.com/339b57fde0866810d25ae6967c92dbed)

入力が完了したら、「作成」ボタンをクリックしサブネットを作成します。

一覧に作成したサブネットが表示され、状態が「available」になっていれば、作成完了になります。

[![https://gyazo.com/910096d640b17fe4c6b2a5ee01106e57](https://i.gyazo.com/910096d640b17fe4c6b2a5ee01106e57.png)](https://gyazo.com/910096d640b17fe4c6b2a5ee01106e57)

### サブネットとルートテーブルの関連付け
作成したサブネットは、VPC内の一つのルートテーブルに関連付ける必要があります。  
本シナリオでは、VPC作成時に自動的に作成されたルートテーブルに関連付けます。  

左側のリストにある「VPC」をクリックし、VPC一覧画面を表示します。  
そして、先ほど作成したVPCを選択し、下部の「ルートテーブル：」横のハイパーリンクをクリックしてください。

[![https://gyazo.com/002ed9d4db211cc58d8ed8176307d2ea](https://i.gyazo.com/002ed9d4db211cc58d8ed8176307d2ea.png)](https://gyazo.com/002ed9d4db211cc58d8ed8176307d2ea)

クリックするとルートテーブル一覧画面に移動し、VPC作成時に自動的に作成されたルートテーブルが表示されるので、  
このルートテーブルを選択してください。

[![https://gyazo.com/3f3f73eaea43fd1cc415c5fdd54ab4b4](https://i.gyazo.com/3f3f73eaea43fd1cc415c5fdd54ab4b4.png)](https://gyazo.com/3f3f73eaea43fd1cc415c5fdd54ab4b4)

その後、下部にある「サブネットの関連付け」タブをクリックし、表示した画面の「編集」ボタンをクリックします。

[![https://gyazo.com/099c9838387ca11e21a5d9db8043b8dd](https://i.gyazo.com/099c9838387ca11e21a5d9db8043b8dd.png)](https://gyazo.com/099c9838387ca11e21a5d9db8043b8dd)

サブネットの一覧が表示されるので、先ほど作成したサブネットにチェックを入れ、「保存」ボタンをクリックします。

[![https://gyazo.com/e97218ffa81d3d4f40c78936c6ab145c](https://i.gyazo.com/e97218ffa81d3d4f40c78936c6ab145c.png)](https://gyazo.com/e97218ffa81d3d4f40c78936c6ab145c)

先ほど作成したサブネットが関連付けられていることを確認したら、完了になります。

[![https://gyazo.com/703de85b9ee385d89110394c9f27f286](https://i.gyazo.com/703de85b9ee385d89110394c9f27f286.png)](https://gyazo.com/703de85b9ee385d89110394c9f27f286)

### インターネットゲートウェイの作成

VPC内部からインターネットに接続させるために、インターネットゲートウェイ(以降、IGW)を作成します。

左側のリストにある「インターネットゲートウェイ」をクリックし、IGW一覧画面を表示します。  

[![https://gyazo.com/3b30f7d924bcbcefc1d52bd1611a1785](https://i.gyazo.com/3b30f7d924bcbcefc1d52bd1611a1785.png)](https://gyazo.com/3b30f7d924bcbcefc1d52bd1611a1785)

左上の「インターネットゲートウェイの作成」ボタンをクリックし、作成ウィザードを開きます。
ウィザードにて、下記情報を入力します。  
※本シナリオでは、XXの部分は自身のユーザ名の下二ケタを設定してください。  
（なお、入力値は任意のものであっても問題ありません。）

| 項目 | 設定値 |
|:------------|:------------|
| ネームタグ  | igw-userXX  |

[![https://gyazo.com/ac98c46cbbe175c80683fc707e1f9d00](https://i.gyazo.com/ac98c46cbbe175c80683fc707e1f9d00.png)](https://gyazo.com/ac98c46cbbe175c80683fc707e1f9d00)

入力後、右下の「作成」ボタンをクリックし、インターネットゲートウェイを作成します。  
ボタンをクリックした後、自動的にインターネットゲートウェイ一覧画面に移ります。  

#### VPCへのアタッチ
インターネットゲートウェイを作成しましたが、一覧画面を確認すると、状態が「detached」になっていると思います。  
次に、作成したインターネットゲートウェイをVPCにアタッチします。

[![https://gyazo.com/af319fd081c2a38fdeac045003dd257a](https://i.gyazo.com/af319fd081c2a38fdeac045003dd257a.png)](https://gyazo.com/af319fd081c2a38fdeac045003dd257a)

上部の「VPCにアタッチ」をクリックし、設定画面を開きます。  
設定画面にて、先ほど作成したVPCを選択します。

[![https://gyazo.com/300b428a56db673bd80fe0045d975bbc](https://i.gyazo.com/300b428a56db673bd80fe0045d975bbc.png)](https://gyazo.com/300b428a56db673bd80fe0045d975bbc)

VPCを選択後、右下の「アタッチ」ボタンをクリックし、インターネットゲートウェイをVPCにアタッチします。  
  
一覧画面にて、インターネットゲートウェイの状態が「attached」になっていれば、設定完了になります。

[![https://gyazo.com/da6b857b1d301cb88681bb2b090fa734](https://i.gyazo.com/da6b857b1d301cb88681bb2b090fa734.png)](https://gyazo.com/da6b857b1d301cb88681bb2b090fa734)

#### IGWをルーティング先に指定
IGWをルーティングテーブルに設定します。  
この設定により、VPC内で稼働するEC2インスタンスがインターネット上に存在するサーバと通信できるようになります。  

左側のリストにある「ルートテーブル」をクリックし、ルートテーブル一覧画面を表示します。  
その後、VPCの列に先ほど作成したVPC名が表示されているルートテーブルを選択します。  

[![https://gyazo.com/789f0eeed75038b19ba65d303ef64b9f](https://i.gyazo.com/789f0eeed75038b19ba65d303ef64b9f.png)](https://gyazo.com/789f0eeed75038b19ba65d303ef64b9f)

下部の「ルート」タブをクリックし、表示した画面にある「編集」ボタンをクリックします。

[![https://gyazo.com/c4ace9c911df8e982f4675d6adc634b2](https://i.gyazo.com/c4ace9c911df8e982f4675d6adc634b2.png)](https://gyazo.com/c4ace9c911df8e982f4675d6adc634b2)

ルーティング設定画面が表示されるので、「別ルートの追加」ボタンをクリックし、新たな入力フィールドを追加します。  
その後、下記情報を入力します。  
（なお、入力値は任意のものであっても問題ありません。）

| 項目 | 設定値 |
|:------------|:------------|
| 送信先 | 0.0.0.0/0 |
| ターゲット | 先ほど作成したIGW |

[![https://gyazo.com/61d331eee3bdc45ec86a4b4452661a08](https://i.gyazo.com/61d331eee3bdc45ec86a4b4452661a08.png)](https://gyazo.com/61d331eee3bdc45ec86a4b4452661a08)

入力完了後、「保存」ボタンをクリックします。  
ルートテーブルにIGWが追加されていることを確認したら、設定完了となります。

[![https://gyazo.com/55667d4622c1ee1a08eeed5f7f8fff59](https://i.gyazo.com/55667d4622c1ee1a08eeed5f7f8fff59.png)](https://gyazo.com/55667d4622c1ee1a08eeed5f7f8fff59)



[次：セキュリティグループの作成へ](https://github.com/yoshirako/aws-handson-scenario/blob/master/WebServer/Scenario/03-prepare-sg-for-launch-instance.md)

