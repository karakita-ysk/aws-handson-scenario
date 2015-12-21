## ネットワークの設定

*(重要)* 以下の操作に移る前に、必ず[基本的な操作シナリオ Amazon Web Service(AWS)][Link-Top]を一読してください。 

### リージョンの選択
画面右上の「サポート」の左隣にあるドロップダウンリストから、環境を構築するリージョンを選択出来ます。
本シナリオでは東京リージョンを使用いたしますので、「アジアパシフィック(東京)」を選択してください。

[![https://gyazo.com/06a9f329d0fbd99aa00a8b99bd632a06](https://i.gyazo.com/06a9f329d0fbd99aa00a8b99bd632a06.gif)](https://gyazo.com/06a9f329d0fbd99aa00a8b99bd632a06)

### プライベートクラウドネットワークの作成

画面左下のVPCアイコンをクリックし、VPCダッシュボード画面に移動します。

[![https://gyazo.com/29ec4d1d3c4136a6d3c9acb019ac9078](https://i.gyazo.com/29ec4d1d3c4136a6d3c9acb019ac9078.png)](https://gyazo.com/29ec4d1d3c4136a6d3c9acb019ac9078)

*VPCダッシュボード画面*

VPCダッシュボード画面では、VPCに関連するサービスの設定が可能になります。

[![https://gyazo.com/3a74285d879569dd35ea7d88be0fcc29](https://i.gyazo.com/3a74285d879569dd35ea7d88be0fcc29.png)](https://gyazo.com/3a74285d879569dd35ea7d88be0fcc29)


### Virtual Private Cloud (VPC)の作成

仮想プライベートクラウドを作成します。VPCにより、パブリッククラウド内に仮想的にプライベートクラウド環境が構築できます。

まず、左側のリストにある「VPC」をクリックします。ボタンをクリックすると、VPC一覧画面が表示されます。
[![https://gyazo.com/b5f1d621292b5de3cbc0a60d44963a4d](https://i.gyazo.com/b5f1d621292b5de3cbc0a60d44963a4d.png)](https://gyazo.com/b5f1d621292b5de3cbc0a60d44963a4d)

すでにVPCが存在しますが、こちらはAWSがデフォルトのVPCとして作成したものになります。

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

左側のリストにある「サブネット」をクリックします。ボタンをクリックすると、サブネット一覧画面が表示されます。

すでにサブネットが存在しますが、こちらはVPCと同じくAWSがデフォルトとして作成したものになります。

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

### インターネットゲートウェイの作成

VPC内部からインターネットに接続させるために、インターネットゲートウェイ(以降、IGW)を作成します。

左側のリストにある「インターネットゲートウェイ」をクリックします。ボタンをクリックすると、IGW一覧画面が表示されます。  
すでにIGW存在しますが、こちらはVPCやサブネットと同じくAWSがデフォルトとして作成したものになります。

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



[次：ルータの作成へ](https://github.com/)

