---
title: "モジュールのバージョンは指定した方が良い"
date: 2021-08-31T21:50:35+09:00
summary: "モジュールのバージョンは指定した方が良いと思った話"
draft: false
---
# はじめに
あなたは、プログラムを構成するモジュールのバージョンを指定していますか？  

私は（個人開発において）そこまで大きく意識をしていなかったのですが、最近になって「`モジュールのバージョンは指定した方が良い`」と実感する場面（エラー）に遭遇しました。  

当たり前な内容になりますが、詳細な実例が頭にあると、主観による「`腑に落ちる`」が進むと感じる次第です。  

エラー内容に入る前に、前提となる [環境説明](#環境説明) をしていきます。

# 環境説明
私が実験的に開発している [LINE](https://line.me/ja/) Bot（[LINE Developers](https://developers.line.biz/ja/)）に [aimay](https://github.com/ghsable/aimay) があります。  

大まかな構成は、以下の通りです。  
* プログラミング言語: [Python3](https://www.python.org/)
* モジュールの管理: [pip](https://github.com/pypa/pip)
* モジュールの最新バージョン検知: [Dependabot](https://dependabot.com/)
* Webアプリケーションフレームワーク: [Flask](https://github.com/pallets/flask)
* ドキュメンテーションジェネレータ: [Sphinx](https://github.com/sphinx-doc/sphinx)
* CI/CD: [GitHub Actions](https://github.com/features/actions/)
* PaaS: [Heroku](https://heroku.com/)

話に必要な情報に絞って明示しました。  
より詳細を把握したい方は [aimay#Development](https://github.com/ghsable/aimay#development) をご覧ください。

# 環境説明 - 補足
モジュールとそのバージョンを管理する「`requirements.txt`」を [Dependabot](https://dependabot.com/) が監視して、最新バージョンを検知します。  
モジュールの最新バージョンを検知すると、[Dependabot](https://dependabot.com/) が「`Pull Request`」（「`requirements.txt`」を「`commit`」）を自動でくれます。  
私はその「`Pull Request`」の内容を確認して、「`Pull Request`」で作成された「`branch`」を「`merge`」しています。  

「`commit`」をイベントに [GitHub Actions](https://github.com/features/actions/) が作動し、[Heroku](https://heroku.com/) へ「`Deploy`」されます。  
ちなみに 今回起きたエラーは、この [GitHub Actions](https://github.com/features/actions/) のログから発覚したものです。

# どんなエラーが起きたのか
「`requirements.txt`」に記載のある2つのモジュールの依存モジュールにおいて、バージョンの「`conflict`」が発生しました。

```console
...
The conflict is caused by:
    sphinx 4.0.1 depends on Jinja2<3.0 and >=2.3
    flask 2.0.0 depends on Jinja2>=3.0

To fix this you could try to:
1. loosen the range of package versions you've specified
2. remove package versions to allow pip attempt to solve the dependency conflict
...
```

記載の通りですが、以下の内容が書かれています。
* [sphinx](https://github.com/sphinx-doc/sphinx) `4.0.1`は、[Jinja2](https://github.com/pallets/jinja) `3.0`未満（且つ `2.3`以上）が必要
* [flask](https://github.com/pallets/flask) `2.0.0`は、[Jinja2](https://github.com/pallets/jinja) `3.0`以上が必要

[Jinja2](https://github.com/pallets/jinja) のバージョンで「`conflict`」が発生しています。

# エラーの原因と解決方法
本エラーの原因は、以下の通りです。
* 「`requestment.txt`」の [sphinx](https://github.com/sphinx-doc/sphinx), [flask](https://github.com/pallets/flask) のバージョン指定

本エラーの解決方法は、以下の通りです。
* [flask](https://github.com/pallets/flask) が [Jinja2](https://github.com/pallets/jinja) `3.0`未満（且つ `2.3`以上）を依存モジュールとしていたバージョンまで下げる
* エラーの解決を一旦放置しておき、[sphinx](https://github.com/sphinx-doc/sphinx) が [Jinja2](https://github.com/pallets/jinja) `3.0`以上に対応した後に [sphinx](https://github.com/sphinx-doc/sphinx) のバージョンを上げる

# エラーの原因の原因
* [Dependabot](https://dependabot.com/) による「`Pull Request`」の内容確認が不足していた（「`merge`」するまでの流れ: [環境説明 - 補足](#環境説明---補足)）

# 余談
[flask](https://github.com/pallets/flask) と [Jinja2](https://github.com/pallets/jinja) の開発元は、[Armin Ronacher](https://lucumr.pocoo.org/about/) が率いる [Pallets](https://palletsprojects.com/) です。  
[flask](https://github.com/pallets/flask) と [sphinx](https://github.com/sphinx-doc/sphinx) の開発元は違うんですねぇ..。  
現在では 依存関係による問題を回避してくれるパッケージ管理ツールは沢山あると思いますので、このような細かな話は あまり気にならない時代なのかもしれません。

# 小休止
お疲れ様です。  
ここまで 夕方に読むと頭が痛くなるかもしれません。  
エラーに忠実に、あえて回りくどく書いています。  
「`心地良い 頭の体操`」になると幸いです。  
[小休止](#小休止) と言っても 次で最後です。(ｵｲｯ)

# `モジュールのバージョンは指定した方が良い`
[エラーの原因の原因](#エラーの原因の原因) の通り、形ではバージョン指定をしていましたが、実態としては「`常に最新を保つ`」ようになっていました。  
セキュリティの観点で言えば「`常に最新を保つ`」は正しいのかもしれませんが、安定した稼働を優先するのであれば、少し面倒でも「`モジュールのバージョンは指定した方が良い`」のかもしれません。
```text
✍️ 追記
> 常に最新を保つ
OSSの次バージョンにマルウェアが仕込まれる事件が目に付くようになってきました。
バージョンアップの度に ソースの差分を追うわけにもいきませんし、性善説モデルの弱点を感じた次第です。
「バージョンは lock しておき、アップデートは慎重に・・、なるべく最新バージョンを保つ」が良さそうですね。
```
