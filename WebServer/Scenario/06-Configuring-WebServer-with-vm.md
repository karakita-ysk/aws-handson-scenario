## EC2インスタンスでの作業（例）

ここでは、実際に作成したEC2インスタンスを利用するシーンを体験するため、Webサーバをセットアップします。

### EC2インスタンスへのSSHアクセス

sshクライアントソフトウェアを起動し、EC2インスタンスのEIPへ鍵交換方式で接続します。
接続に必要な情報は、下記の通りです。
 * 接続先EC2インスタンスのEIP  
    -. (インスタンスの起動）[EIP設定]にてEC2インスタンスに関連付けたEIP)  

 * 接続ユーザ名：ec2-user
 * ssh秘密鍵 
 
    -. (インスタンス起動の前準備（続き）[キーペアの作成]にてダウンロードしたファイル)
    


以下は、Windowsマシンからteratermを使用した場合の操作例となります。

#### 接続先IPを指定

ホスト欄に、接続先のEC2インスタンスのEIPを指定します。

[![https://gyazo.com/3b46da2ad65f2e8eeb2956c0c261bc7b](https://i.gyazo.com/3b46da2ad65f2e8eeb2956c0c261bc7b.png)](https://gyazo.com/3b46da2ad65f2e8eeb2956c0c261bc7b)

セキュリティ警告が表示される場合は、「続行」ボタンを押下

[![https://gyazo.com/573ee45361572375212f757b452e1ca0](https://i.gyazo.com/573ee45361572375212f757b452e1ca0.png)](https://gyazo.com/573ee45361572375212f757b452e1ca0)

#### ログインの実施

ユーザ名を入力し、RSA/DSA鍵を使う オプションのラジオボタンを有効にした上で、秘密鍵（ダウンロードしたもの）を指定します

入力が完了したら、「OKボタンを押下します。」

[![https://gyazo.com/930bffc7cd2e7f9b32eabb452d082fe3](https://i.gyazo.com/930bffc7cd2e7f9b32eabb452d082fe3.png)](https://gyazo.com/930bffc7cd2e7f9b32eabb452d082fe3)


ログインが完了すると、SSHのセッションが開始されます。

[![https://gyazo.com/c62b0858748405b611812dc45a517c44](https://i.gyazo.com/c62b0858748405b611812dc45a517c44.png)](https://gyazo.com/c62b0858748405b611812dc45a517c44)


### httpd(webサーバプログラム)のインストール
yum コマンドを使用して、httpd プログラムをインストールします。

``` command
$ sudo yum install -y httpd
```

### シンプルなHTMLコンテンツの作成
Webページを作成します。 デフォルトのDocument Root 配下に、index.htmlをviエディタで作成しても構いませんが、より簡単に行うためには、下記のコマンドを実行します。

```
$ hostname | sudo tee -a /var/www/html/index.html
```

### httpdサービスの起動
Webサーバプログラムを起動します。

```
$ sudo service httpd start
```

### 接続テスト
操作を行っているPC上で、Webブラウザを立ち上げ、EIPを指定して接続します。画面にあるように、画面が応答されれば成功となります。

* URL(例): http://52.68.28.155/ ※これまでの例で示してきたEIPを指定しています。

[![https://gyazo.com/d2dfa18b9f00e10b682a3d541c34f59e](https://i.gyazo.com/d2dfa18b9f00e10b682a3d541c34f59e.png)](https://gyazo.com/d2dfa18b9f00e10b682a3d541c34f59e)


AWS環境上に、Webサーバを構築するシナリオは、以上となります。

[次：環境のクリーンアップへ](https://github.com/yoshirako/aws-handson-scenario/blob/master/WebServer/Scenario/07-cleanup.md)

