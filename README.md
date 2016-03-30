# Karabiner設定

よくわからなくなってきたのでメモ。

## 前提

- 英字キーボード
- システム環境設定で修飾キーを下記の通りカスタマイズ済み

| 物理キー        | 機能    |
|:---            |:---     |
|CapsLook(物理)  | Command |
|Control(物理)    | Control |
|Option(物理)      | Option  |
|Command(物理)     | Control |

- ターミナルアプリは『iTerm2』を使用
- エディタは『SublimeText』を使用
- クリップボード拡張として『ClipMenu』を使用

## やりたいこと

- 基本的に 「左・Command(物理)」+ 「tab」でアプリを切り替えたい
- ターミナル系アプリのときは 「CapsLook(物理)」を 「Control(機能)」 として使いたい
- SublimeTextのときも 「CapsLook(物理)」を 「Control(機能)」 として使いたい
- できるだけコピー、ペースト、アンドゥ、リドゥなどの基本操作はアプリ間で同じキー(物理)でやりたい

## 現在の状況

### 全体

| 機能                   | キー                         | 実現状況| メモ  |
|:---                   |:---                          | :---:   | :--- |
| アプリケーションの切り替え |[左・Commandキー(物理)] + [tab] | ◎     |     |
| 入力ソース切り替え(HHK使用時)       |[左・Option]キー(物理)]  + [`]   | ×  |
| 入力ソース切り替え(付属キーボード使用時)  | 1ボタンで[US/日本語]を切り替えたい  | ×  |
| Alfredの呼び出し       |[左・CapsLook]キー(物理)]  2回押し | △    | 『iTerm2』『SublimeText』は [左・Command]キー(物理)]  2回押し|


### ターミナル系アプリ

『Terminal.app』は、カーソルでフォーカスしてコピーすることが出来ない（やり方がわからない）ので『iterm2』を使うことにする。

#### ターミナル系アプリ使用時のキー割り当て

A の左に Controlキー が欲しい。
なので、ターミナル使用時は下記のキー割り当てにしたい。
- [CapsLook(物理)(機能Control)] + [A] で行の先頭に移動
- [CapsLook(物理)(機能Control)] + [C] でキャンセル
などを実現したい。

| 物理キー       | システム環境設定の機能    | iTerm2 専用の機能 |
|:---           |:---                   | :--             |
|CapsLook(物理)  | Command               | Control         |
|Command(物理)   | Control                | Command         |

『iTerm2』の Preferences >> Keys より、 修飾キーを下記の通りカスタマイズ済み。

| 物理キー        | システム環境設定の機能 | iTerm2 専用の機能 |
|:---            |:---                |:--             |
|Command(物理)    | Control            |Command         |

Karabinerでキーの入れ替え。

- Command と Control
- Option と Shift


| 機能                   | キー                         | 実現状況| メモ  |
|:---                   |:---                          | :---:   | :--- |
| 行の先頭に移動           |[左・Capslock(物理) + [A]      | ◎       |     |
| 処理の中断              |[左・Capslock(物理) + [C]      | ◎       |     |
| ペースト                |[左・Capslock(物理) + [C]      | ×        | 現在は[左・Commandキー(物理)] + [左・Shiftキー(物理)] + [C] で 『ClipMenu』呼び出し  |

### エディタ


- 『SublimeText』のときも 「CapsLook(物理)」を 「Control(機能)」 として使いたい。
- でもアプリの切り替えは 「左・Command(物理)」+ 「tab」でおこないたいので、単純なキーの入れ替えじゃダメそう
- 今のところうまいやり方がわかっていない