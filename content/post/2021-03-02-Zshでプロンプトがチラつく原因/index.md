---
title: "Zshでプロンプトがチラつく原因"
date: 2021-03-02T19:27:56+09:00
summary: "Zshでプロンプトがチラつく原因の話"
draft: false
---
# はじめに
早速ですが、[Zsh](https://www.zsh.org/)上で`Enter`を連打してみましょう。  

![image1](image1.gif)

えっ、何も違和感を感じないって？  

では、以下は素の[Zsh](https://www.zsh.org/)で`Enter`を連打したものです。  

![image2](image2.gif)

はい。気が付いちゃいましたね。  

# Zshでプロンプトがチラつく原因
素の[Zsh](https://www.zsh.org/)のプロンプトで発生しないという事は、[Zsh](https://www.zsh.org/)の設定ファイルに原因がある事になります。  
では、[Zsh](https://www.zsh.org/)の設定ファイルのどの箇所が原因になっているのでしょうか。  

なんだか、何かの読込みで引っ掛かっているように見えますよね。  
と、ということは・・・まさか・・  

* `~/.zshrc`
  ```zsh
  ...
  # プラグインを git clone した後、source をして読込み
  source ${HOME}/.zsh/plugins/fast-syntax-highlighting/fast-syntax-highlighting.plugin.zsh
  ...
  ```

ここだ！！  

さて、早速コメントアウトをして動作確認をしてみます。  

* `~/.zshrc`
  ```zsh
  ...
  #source ${HOME}/.zsh/plugins/fast-syntax-highlighting/fast-syntax-highlighting.plugin.zsh
  ...
  ```

すると・・・  

![image3](image3.gif)

ｷﾀ━━━━(ﾟ∀ﾟ)━━━━!!  

# めでたしめでたし？
全然めでたくありません。  
しょうもない設定が原因であれば消す方向で考えていましたが、そんな期待は見事に打ち砕かれました。  

まぁ、本件は原因が分かっただけで良しとしましょう・・ではではー。
