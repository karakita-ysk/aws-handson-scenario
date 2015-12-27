## 環境のクリーンアップ

以前の章でハンズオンは完了となりますが、
Introductionにも記述した通りAWSは従量課金のため、インスタンスを上げ続けると料金が継続して発生するため、
今までの作業で構築した環境を削除し、料金が継続して発生しない状態まで戻します。

本シナリオで使用したサービスの中で、料金が発生するものは以下になります。  
・EC2インスタンス  
・EBS  
・EIP  

また、料金は発生しませんが、
本シナリオにて作成したもので削除するものは以下になります。  
・VPC  
・キーペア

### EIPの関連付けの解除＋解放

#### EIPの関連付けの解除
AWSマネジメントコンソールのトップ画面より、EC2アイコンをクリックし、EC2ダッシュボード画面を開きます。

[![https://gyazo.com/d5404064c02f29ecd8949c1b7c5af3ee](https://i.gyazo.com/d5404064c02f29ecd8949c1b7c5af3ee.png)](https://gyazo.com/d5404064c02f29ecd8949c1b7c5af3ee)

左側リストの「Elastic IP」をクリックし、EIP一覧画面を表示します。
そして、先ほど自身で作成したEIPを選択してください。

[![https://gyazo.com/b50157ae4a7c887141d190f0a22b04c1](https://i.gyazo.com/b50157ae4a7c887141d190f0a22b04c1.png)](https://gyazo.com/b50157ae4a7c887141d190f0a22b04c1)

選択後、上部の「アクション」ボタンをクリックし、「アドレスの関連付けの解除」をクリックしてください。

[![https://gyazo.com/a939f81501bed5aa0c293397441dcf41](https://i.gyazo.com/a939f81501bed5aa0c293397441dcf41.png)](https://gyazo.com/a939f81501bed5aa0c293397441dcf41)

クリックすると、解除確認画面が表示されるので、「はい、関連付けを解除する」ボタンをクリックしてください。

[![https://gyazo.com/0026737bf2cac5b3bf57e72213757334](https://i.gyazo.com/0026737bf2cac5b3bf57e72213757334.png)](https://gyazo.com/0026737bf2cac5b3bf57e72213757334)

EIP一覧画面にて、自身のEIPの「インスタンス」列と「プライベートIPアドレス」列に値が何も入っていなければ、関連付けの解除が完了です。

#### アドレスの解放
再度、自身で作成したEIPを選択してください。  
そして、上部の「アクション」ボタンをクリックし、「アドレスの解放」をクリックしてください。

[![https://gyazo.com/a939f81501bed5aa0c293397441dcf41](https://i.gyazo.com/a939f81501bed5aa0c293397441dcf41.png)](https://gyazo.com/a939f81501bed5aa0c293397441dcf41)

確認画面が表示されるので、「解放」ボタンをクリックしてください。

[![https://gyazo.com/38512c4fa2e37b27415d6637249598a3](https://i.gyazo.com/38512c4fa2e37b27415d6637249598a3.png)](https://gyazo.com/38512c4fa2e37b27415d6637249598a3)

EIP一覧画面にて、自身のEIPが表示されていなければ、アドレスの解放は完了です。

### EC2インスタンスの削除
左側リストの「インスタンス」をクリックし、EC2インスタンス一覧画面を表示します。  
そして、先ほど自身で作成したEC2インスタンスを選択してください。

[![https://gyazo.com/d05041b007bc18cde90af967e489aee8](https://i.gyazo.com/d05041b007bc18cde90af967e489aee8.png)](https://gyazo.com/d05041b007bc18cde90af967e489aee8)

EC2インスタンスを選択後、上部「アクション」タブをクリックし、「インスタンスの状態」にカーソルを合してリストを表示した後、リスト内の「削除」をクリックしてください。

[![https://gyazo.com/4c9c462b580b51b78c8887125c73815d](https://i.gyazo.com/4c9c462b580b51b78c8887125c73815d.png)](https://gyazo.com/4c9c462b580b51b78c8887125c73815d)

インスタンスの削除確認画面が表示されますので、「はい、削除する」ボタンをクリックしてください。

[![https://gyazo.com/a80ae8b5e32a089a1b7a4b78024ff6e0](https://i.gyazo.com/a80ae8b5e32a089a1b7a4b78024ff6e0.png)](https://gyazo.com/a80ae8b5e32a089a1b7a4b78024ff6e0)

インスタンスの削除が開始されると、
「インスタンスの状態」列が「shutting-down」になり、削除が完了すると「terminated」になります。

[![https://gyazo.com/c47bd919a21b8a47563e5770e98c92a0](https://i.gyazo.com/c47bd919a21b8a47563e5770e98c92a0.png)](https://gyazo.com/c47bd919a21b8a47563e5770e98c92a0)

[![https://gyazo.com/7e78c5cc7cb66108a9a1fcf82672a090](https://i.gyazo.com/7e78c5cc7cb66108a9a1fcf82672a090.png)](https://gyazo.com/7e78c5cc7cb66108a9a1fcf82672a090)

````
状態が「terminated」になっても、一覧画面には一定期間インスタンスが表示されています。
しかし、状態が「terminated」であれば、今後料金は発生しませんのでご安心ください。
````

### EBSの削除
本シナリオでは、EC2インスタンスを作成した際の設定で、EC2インスタンスが削除される際に合わせて削除されるようにしております。  
(シナリオ：インスタンスの起動 [4. ストレージの追加] をご覧ください。)

ですので、本シナリオではEBSが削除されていることを確認するだけになります。  
*(重要)*設定に不備があった場合はEBSは自動で削除はされませんので、その際は明示的に削除してください。

左側リストの「ボリューム」をクリックし、EC2インスタンス一覧画面を表示します。

自身のEBSが表示されない、又は状態が「deleting]になっていれば、EBSの削除は完了となります。

[![https://gyazo.com/9c37aa4c9179dc110bbbdf17bbb72777](https://i.gyazo.com/9c37aa4c9179dc110bbbdf17bbb72777.png)](https://gyazo.com/9c37aa4c9179dc110bbbdf17bbb72777)

### キーペアの削除

左側リストの「キーペア」をクリックし、キーペア一覧画面を表示します。  
先ほど作成したキーペアを選択し、上部の「削除」ボタンをクリックしてください。

[![https://gyazo.com/2c6b9614fd3a7ea3d5265d8556c96c75](https://i.gyazo.com/2c6b9614fd3a7ea3d5265d8556c96c75.png)](https://gyazo.com/2c6b9614fd3a7ea3d5265d8556c96c75)

確認画面が表示されるので、「はい」ボタンをクリックし削除を行ってください。

[![https://gyazo.com/64ac14ff96ffc297eb948e7e23923994](https://i.gyazo.com/64ac14ff96ffc297eb948e7e23923994.png)](https://gyazo.com/64ac14ff96ffc297eb948e7e23923994)

キーペア一覧画面にて、自身のキーペアが表示されなければ、削除完了になります。

### VPCの削除
AWSマネジメントコンソールのトップ画面より、VPCアイコンをクリックし、VPCダッシュボード画面を開きます。

[![https://gyazo.com/f9c570bb6ad34ed2a4638b7fa398f7bf](https://i.gyazo.com/f9c570bb6ad34ed2a4638b7fa398f7bf.png)](https://gyazo.com/f9c570bb6ad34ed2a4638b7fa398f7bf)

左側のリストにて「VPC」をクリックし、VPC一覧画面を表示します。

[![https://gyazo.com/b8955fd9428fb1226de4cbb5137742e7](https://i.gyazo.com/b8955fd9428fb1226de4cbb5137742e7.png)](https://gyazo.com/b8955fd9428fb1226de4cbb5137742e7)

自身で作成したVPCを選択後、上部の「アクション」ボタンをクリックし、「VPCの削除」をクリックします。

[![https://gyazo.com/d0f4d7fbb481b85bab2fb731bb008fc2](https://i.gyazo.com/d0f4d7fbb481b85bab2fb731bb008fc2.png)](https://gyazo.com/d0f4d7fbb481b85bab2fb731bb008fc2)

クリック後、確認画面が表示されるので、「削除」ボタンをクリックします。

[![https://gyazo.com/febeafa43463018ae5603c041d1c954b](https://i.gyazo.com/febeafa43463018ae5603c041d1c954b.png)](https://gyazo.com/febeafa43463018ae5603c041d1c954b)

VPCの削除を行うと、併せて下記設定も削除されます。  
・サブネット  
・セキュリティグループ  
・インターネットゲートウェイ  
・ルートテーブル  

VPC一覧画面に、自身のVPCが表示されなければ削除完了となります。

以上で、本シナリオは終了です。  
お疲れさまでした。
