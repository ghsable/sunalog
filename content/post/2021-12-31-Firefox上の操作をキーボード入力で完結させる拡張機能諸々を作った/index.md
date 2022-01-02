---
title: "Firefox上の操作をキーボード入力で完結させる拡張機能諸々を作った"
date: 2021-12-31T16:52:22+09:00
summary: "Firefox上の操作をキーボード入力で完結させる拡張機能諸々を作った話"
draft: false
---
# Firefox上の操作をキーボード入力で完結させる拡張機能諸々を作った
> 拡張機能
- [vimode](https://addons.mozilla.org/en-US/firefox/addon/vimode/)  
[![get-the-addon](get-the-addon.png)](https://addons.mozilla.org/en-US/firefox/addon/vimode/)

> 諸々
- [searchmode](https://ghsable.github.io/searchmode/)
- [mousemode](https://crates.io/crates/mousemode)

`拡張機能 + 諸々`によって [Firefox](https://www.mozilla.org/en-US/firefox/new/)上の操作をキーボード入力で完結させることができる。

# 目次
* [誘い](#誘い)
* [拡張機能](#拡張機能)
  * [vimode](#vimode)
* [諸々](#諸々)
  * [searchmode](#searchmode)
  * [mousemode](#mousemode)
* [おわり](#おわり)
* [余談1](#余談1)
* [余談2](#余談2)

# 誘い
`Webブラウジングがキーボード操作だけで完結する世界はいいぞ` と。  

私は 以前の状態に戻るのは難しそうだ。  
それ以上の言葉は必要が無いだろう。

# 拡張機能

## vimode
まずは中核。  
キーボードショートカットを提供する [Firefox](https://www.mozilla.org/en-US/firefox/new/) [Add-on](https://addons.mozilla.org/en-US/firefox/) である。
- [vimode](https://addons.mozilla.org/en-US/firefox/addon/vimode/)  
[![get-the-addon-small](get-the-addon-small.png)](https://addons.mozilla.org/en-US/firefox/addon/vimode/)

コンセプトは以下の通りである。
- キー入力の組み合わせは2つ以下
- 主要な操作はキー入力の組み合わせを必要としない
- 標準のキーボードショートカットを可能な限り邪魔しない
- どこか[vi](http://ex-vi.sourceforge.net/),[vim](https://www.vim.org/)らしい操作感
- [vi](http://ex-vi.sourceforge.net/),[vim](https://www.vim.org/)の操作感に寄り過ぎない
- どこか標準のキーボードショートカットを更に短縮している操作感
- 必要最低限のパーミッション要求

あとは、[Demo](https://github.com/ghsable/vimode#vimode)で感じていただきたい。  
操作方法は[vimode#vi-like-operations](https://github.com/ghsable/vimode#vi-like-operations)を参照されたい。  
[![demo_vimode.gif](https://raw.githubusercontent.com/ghsable/vimode/main/.readme/images/demo_vimode.gif)](https://raw.githubusercontent.com/ghsable/vimode/main/.readme/images/demo_vimode.mp4)

# 諸々

## searchmode
続いて [vimode](https://addons.mozilla.org/en-US/firefox/addon/vimode/)のトップページ。  
これは至極シンプルなWeb検索トップ画面で、検索エンジンの切り替えができるようになっている。  
- [searchmode](https://ghsable.github.io/searchmode/)

[vimode](https://addons.mozilla.org/en-US/firefox/addon/vimode/)の キー`o` で開くようにしており、[vimode](https://addons.mozilla.org/en-US/firefox/addon/vimode/)の機能の一部としての位置付けとなる。  
ただし、独立したWebページにしているため 単体での利用もできる。  
動的にDOM操作を行う 数多の検索トップ画面の気持ち悪さから 多少なりとも開放されるのかもしれない。  

先述の通り これは[vimode](https://addons.mozilla.org/en-US/firefox/addon/vimode/)のトップページで、  
[vimode](https://addons.mozilla.org/en-US/firefox/addon/vimode/)とシームレスに繋がるよう ページ内にキーボードショートカットを用意している。  

あとは、[Demo](https://github.com/ghsable/searchmode#demo)で感じていただきたい。  
操作方法は[Keyboard shortcuts](https://github.com/ghsable/searchmode#keyboard-shortcuts)を参照されたい。  
[![demo_searchmode.gif](https://raw.githubusercontent.com/ghsable/searchmode/main/.readme/images/demo_searchmode.gif)](https://raw.githubusercontent.com/ghsable/searchmode/main/.readme/images/demo_searchmode.mp4)

## mousemode
ページ内のリンクをクリックするために `Tab`を連打して目的のリンクにフォーカスを合わせなければいけない？  
その心配は無用、マウス操作もキーボード操作に組み込んでしまえば良い。  
あなたは`Tab`を連打する必要も無いし、リンク属性に付与された小さなアルファベットに目を凝らす必要も無い。  
- [mousemode](https://crates.io/crates/mousemode)

あとは、[Demo](https://github.com/ghsable/mousemode#demo)で感じていただきたい。  
インストール方法・操作方法は[mousemode](https://github.com/ghsable/mousemode#mousemode)を参照されたい。  
[![demo_mousemode.gif](https://raw.githubusercontent.com/ghsable/mousemode/main/.readme/images/demo_mousemode.gif)](https://raw.githubusercontent.com/ghsable/mousemode/main/.readme/images/demo_mousemode.mp4)

# おわり
マウスを排す というよりは、可能な限り 既存との共存を目指した。  
ここまで試していただいた方には まず感謝を述べたい。  

こんなマニアックな話に付き合ってくれて ありがとう！  

ここまで試していただいた方は [Firefox](https://www.mozilla.org/en-US/firefox/new/)をキーボードだけで ある程度自在に操作ができるようになったのではないだろうか。  
私と似た感覚を持つ方が 1人2人...はどこかに存在するのではないか と思い 公開をした。  
数あるオペレーションの一つ として楽しんでいただければ嬉しく思う。

# 余談1
本記事の公開までを含めると それなりの労力が掛かっている。  
構想・初期学習・周辺準備・開発・テスト・ドキュメント作成・デモ撮影・記事作成...。  
ここまでの一連の道のりを経た時、`OSSの在り方`を考えさせられた。  
やる・やらない も自由な世界。  
通常の思考であれば 「やらない」に傾く。  
しかし それが通常となってしまっては `OSSの持続性` に 陰り が出てきそうだ。

# 余談2
`何か`の操作を**キーボードだけ**で制御している時は`そこそこ心地が良い`ものだ。  

脳で現実世界を制御している感覚に浸ることができるからだ。  
大なり小なりあれど`そこそこ心地が良い`ものだ。  

`何か`がWebブラウザとした場合、`脳で現実世界を制御している感覚を阻害する要因`がある。  
そう、マウス操作だ。  
誤解して欲しくないのは、マウスは悪く無い点である。  

キーボードとマウスの両方を扱っている場合、脳からの伝達がそれぞれに分岐する。  
この分岐してしまう点が`脳で現実世界を制御している感覚を阻害する要因`と考えている。  

この分岐問題は どちらかに操作を寄せてしまえば解決する。  
どちらに寄せるか・・文字入力が必要な点で キーボードが妥当な選択だろう。  
スクリーンキーボードは どうも分が悪い。  

キーボードに操作を寄せると決まったところで、キーボードでどのように操作を実現するか。  
既存のショートカットを使う？
- [Keyboard shortcuts](https://support.mozilla.org/en-US/kb/keyboard-shortcuts-perform-firefox-tasks-quickly)

うーん・・・一部は使えそう。  
しかし、使いたいショートカットは それ自体が`脳で現実世界を制御している感覚を阻害する要因`になりそうだ。  
キー入力は簡単に直感的に・・・馴染み深いキーバインドに・・・。  

・・・そうか、そういうことか。
