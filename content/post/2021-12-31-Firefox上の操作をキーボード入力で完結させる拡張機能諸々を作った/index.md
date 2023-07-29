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

「`拡張機能 + 諸々`」によって [Firefox](https://www.mozilla.org/en-US/firefox/new/) 上の操作をキーボード入力で完結させることを目指しました。

# 目次
* [誘い](#誘い)
* [拡張機能](#拡張機能)
  * [vimode](#vimode)
* [諸々](#諸々)
  * [searchmode](#searchmode)
  * [mousemode](#mousemode)
* [おわり](#おわり)

# 誘い
`Webブラウジングがキーボードの操作だけで完結してくれると心地良い！`  

# 拡張機能

## vimode
```text
⚠️
キーボードショートカットの競合はなるべく避けるよう意識したつもりですが、完全に避ける事は当然に不可能です。
(余談ですが vimode のような拡張機能はブラウザベンダが想定している「王道」ではなく「邪道」な拡張機能です。)
また vimode が機能しては困るサイトも出てくると思います。(タイピングサイトなど)
そのようなサイトでは vimode を機能させないようになるべく共通の特性でフィルターを掛けていますが、
共通の特性の無いWebサイトに対しては個別の対応はしていません。(対応予定もございません。)
vimode が機能して困る場面で「拡張機能を無効」、必要な場面で「拡張機能を有効」という運用を想定しています。
```
まずは中核。キーボードショートカットを提供する [Firefox](https://www.mozilla.org/en-US/firefox/new/) [Add-on](https://addons.mozilla.org/en-US/firefox/) です。
- [vimode](https://addons.mozilla.org/en-US/firefox/addon/vimode/)  
[![get-the-addon-small](get-the-addon-small.png)](https://addons.mozilla.org/en-US/firefox/addon/vimode/)

コンセプトは以下の通りです。
- キー入力の組み合わせは2つ以下
- 主要な操作はキー入力の組み合わせを必要としない
- 標準のキーボードショートカットを可能な限り邪魔しない
- どこか [vi](http://ex-vi.sourceforge.net/),[vim](https://www.vim.org/) らしい操作感
- [vi](http://ex-vi.sourceforge.net/),[vim](https://www.vim.org/) の操作感に寄り過ぎない
- どこか標準のキーボードショートカットを更に短縮している操作感
- 必要最低限のパーミッション要求

あとは [Demo](https://github.com/ghsable/vimode#vimode) へどうぞ。操作方法は [vimode#vi-like-operations](https://github.com/ghsable/vimode#vi-like-operations) に載せています。  
[![demo_vimode](https://raw.githubusercontent.com/ghsable/vimode/main/.readme/images/demo_vimode.gif)](https://raw.githubusercontent.com/ghsable/vimode/main/.readme/images/demo_vimode.mp4)

# 諸々

## searchmode
続いて [vimode](https://addons.mozilla.org/en-US/firefox/addon/vimode/) のトップページ。これは至極シンプルなWeb検索トップ画面で検索エンジンの切り替えができるようになっています。
- [searchmode](https://ghsable.github.io/searchmode/)

[vimode](https://addons.mozilla.org/en-US/firefox/addon/vimode/) のキー「`o`」で開くようにしており、[vimode](https://addons.mozilla.org/en-US/firefox/addon/vimode/) の機能の一部としての位置付けとなります。  
ただし独立したWebページにしているため（※1）単体での利用もできます。  
動的にDOM操作を行う数多の検索トップ画面の気持ち悪さから多少なりとも開放されるかもしれません。  
（※1）組込みページは拡張機能が無効になる仕様が存在するため、独立したWebページにしています。

ちなみに [vimode](https://addons.mozilla.org/en-US/firefox/addon/vimode/) とシームレスに繋げるため、ページ内にキーボードショートカットを用意しています。  

あとは [Demo](https://github.com/ghsable/searchmode#demo) へどうぞ。操作方法は [searchmode#keyboard-shortcuts](https://github.com/ghsable/searchmode#keyboard-shortcuts) に載せています。  
[![demo_searchmode](https://raw.githubusercontent.com/ghsable/searchmode/main/.readme/images/demo_searchmode.gif)](https://raw.githubusercontent.com/ghsable/searchmode/main/.readme/images/demo_searchmode.mp4)

## mousemode
```text
⚠️
Repository を Public から Public archive へ変更しました。
私が X Window System から Wayland へ移行したからです。

また dependencies の mouse_rs の dependencies の stdweb は2019年10月に開発を停止しています。
ご利用の際はご留意いただけますと幸いです。
koute/stdweb - https://github.com/koute/stdweb

ついでに余談ですが mousemode 的アプローチはお遊び程度のご利用をお勧めします。
手元に「赤ポチ」がある方はそちらをご利用された方が幸せになれると思います。
```
ページ内のリンクをクリックするために「`Tab`」を連打して目的のリンクにフォーカスを合わせなければいけない？  
その心配は無用、マウス操作もキーボード操作に組み込んでしまえば良いのだ。わはは。  
あなたは「`Tab`」を連打する必要も無いしリンク属性に付与された小さなアルファベットに目を凝らす必要も無いのDA。  
- [mousemode](https://crates.io/crates/mousemode)

あとは [Demo](https://github.com/ghsable/mousemode#demo) へどうぞ。インストール方法・操作方法は [mousemode#mousemode](https://github.com/ghsable/mousemode#mousemode) に載せています。  
[![demo_mousemode](https://raw.githubusercontent.com/ghsable/mousemode/main/.readme/images/demo_mousemode.gif)](https://raw.githubusercontent.com/ghsable/mousemode/main/.readme/images/demo_mousemode.mp4)

# おわり
「マウスを排す」というよりは可能な限り「既存との共存」を目指しました。[Firefox](https://www.mozilla.org/en-US/firefox/new/) をキーボードだけでそれなりに操作ができるようになったのではないでしょうか。  

キーバインドは人との相性問題が大きいですが、私と感覚が近い方がいらっしゃれば幸いです。数あるオペレーションの一つ として楽しんでいただければ嬉しく思います。
