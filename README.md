# Karabiner設定

よくわからなくなってきたのでメモ。

## 前提

- MacBookPro 英字キーボード版を使用
- HHKの英字キーボードを接続して使用することもある

## よく使うアプリ

- ターミナルアプリは『iTerm2』を使用
- エディタは『SublimeText』を使用
- クリップボード拡張として『ClipMenu』を使用

## やりたいこと

- 全体的に「CapsLook(物理)」を「Command(機能)」として使いたい
- ターミナル系アプリのときは 「CapsLook(物理)」を 「Control(機能)」 として使いたい
- SublimeTextのときも 「CapsLook(物理)」を 「Control(機能)」 として使いたい
- すべてのアプリで、「左・Command(物理)」+ 「tab」でアプリを切り替えたい
- できるだけコピー、ペースト、アンドゥ、リドゥなどの基本操作はアプリ間で同じキー(物理)でやりたい
- 付属キーボード使用時、1ボタンで『US』と『かな』を切り替えたい
- HHK使用時、[左・Option]キー(物理)]  + [`] で『US』と『かな』を切り替えたい

### 実現状況

| 機能                   | キー                         | 実現状況| メモ  |
|:---                   |:---                          | :---:   | :--- |
| アプリケーションの切り替え |[左・Commandキー(物理)] + [tab] | ◎     |     |
| 入力ソース切り替え(HHK使用時)       |[左・Option]キー(物理)]  + [`]   | ×  |
| 入力ソース切り替え(付属キーボード使用時)  | 1ボタンで[US/日本語]を切り替えたい  | ×  |
| Alfredの呼び出し       |[左・CapsLook]キー(物理)]  2回押し | △   | 『iTerm2』は [左・Command]キー(物理)]  2回押し|

## 現在の設定

### 全体

Macのシステム環境設定で、修飾キーを下記の通りカスタマイズした。

| 物理キー        | システム環境設定    |
|:---            |:---              |
|CapsLook(物理)   | Command          |
|Control(物理)    | 変更無し          |
|Option(物理)     | 変更無し          |
|Command(物理)    | Control          |

その後、Karabinerで下記設定を有効化した。
（一部アプリを除いて、ControlキーにCommandキーを割り当て）

- Control_L to Command_L (expect Terminal, Virturl Machine, RDC, VNC, Teamviewer, EMACS, X11, Citrix Viewer)

現在の設定。
懸念点: 全体的にControlキーが無くなったこと。Controlキーが必要なアプリについては個別にKarabinerでxmlの設定が必要なこと。

| 物理キー        | システム環境設定    | Karabiner        |
|:---            |:---              | :--                |
|CapsLook(物理)   | Command          |                  |
|Control(物理)    |                  | Command          |
|Option(物理)     |                  |                  |
|Command(物理)    | ~~Control~~          | Command          |



### ターミナル系アプリ

『Terminal.app』は、カーソルでフォーカスしてコピーすることが出来ない（やり方がわからない）ので『iterm2』を使うことにする。

設定前は下記の状態。

| 物理キー        | システム環境設定    | Karabiner        |
|:---            |:---              | :--                |
|CapsLook(物理)   | Command          |                  |
|Control(物理)    |                  | Command          |
|Option(物理)     |                  |                  |
|Command(物理)    | ~~Control~~          | Command          |

Karabinerのprivate.xmlに、iTerm専用にCommandにControlを割り当てる設定を追記し、有効化した。

```
  <appdef>
    <appname>iTerm2</appname>
    <equal>com.googlecode.iterm2</equal>
  </appdef>

  <item>
    <name>[my][iTerm2] Command_L to Control_L (iTerm2 ONLY)</name>
    <identifier>iTerm2_change_CmdL-to-CtrlL</identifier>
    <only>iTerm2</only>
    <autogen>__KeyToKey__ KeyCode::COMMAND_L, KeyCode::CONTROL_L</autogen>
  </item>
```

有効化した状態。

| 物理キー        | システム環境設定    | Karabiner        | Karabiner(iterm専用) |
|:---            |:---              | :--              | :--             |
|CapsLook(物理)   | ~~Command~~          |                  | Control       |
|Control(物理)    |                  | Command          |               |
|Option(物理)     |                  |                  |               |
|Command(物理)    | ~~Control~~          | Command          |               |