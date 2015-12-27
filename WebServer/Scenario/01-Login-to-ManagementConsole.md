## クラウド環境へのアクセス


**(重要)** 以下の操作に移る前に、必ず基本的な操作シナリオ Aamazon Web Service (AWS)[Link-Top]を一読してください。
[Link-Top]:]https://github.com/yoshirako/aws-handson-scenario/blob/master/WebServer/Introduction.md

### Webブラウザからログインページへアクセス
PC上で、Webブラウザを起動し、接続先を入力して、アクセスします。

本シナリオでは、アカウント名を「hogehogehoge」として作成しているため、接続先URLは下記になります。  
※hogehogehogeの部分をご自身の環境に合わせて適宜読み替えてください。
```
https://hogehogehoge.signin.aws.amazon.com/console
```
[![https://gyazo.com/4ca48c03bce644776bbc6177944d6871](https://i.gyazo.com/4ca48c03bce644776bbc6177944d6871.png)](https://gyazo.com/4ca48c03bce644776bbc6177944d6871)

### ログイン
ユーザ名 ／パスワードを入力し、ログインボタンをクリックします。
ユーザ名およびそのパスワードは、事前に用意されている必要があります。用意するアカウントは、一般的なIAMアカウントとなります。

```
アカウントが不明の場合は、クラウド管理者に問い合わせてください。
```

[![https://gyazo.com/c9130b0bf458267f817c587088b7c003](https://i.gyazo.com/c9130b0bf458267f817c587088b7c003.png)](https://gyazo.com/c9130b0bf458267f817c587088b7c003)

### 概要ページ
ログインに成功すると、AWSマネジメントコンソールのトップページが表示されます。

[![https://gyazo.com/e20315639ecc925a1bc89998cc192b03](https://i.gyazo.com/e20315639ecc925a1bc89998cc192b03.png)](https://gyazo.com/e20315639ecc925a1bc89998cc192b03)

[次：ネットワークの作成](https://github.com/yoshirako/aws-handson-scenario/blob/master/WebServer/Scenario/02-create-network.md)
