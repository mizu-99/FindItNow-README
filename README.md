# FindItNow - ファイル検索ツール

<img src=icon.ico width=100>

![License-MIT](https://img.shields.io/badge/license-MIT-blue.svg?style=flat)
![Python](https://custom-icon-badges.herokuapp.com/badge/Python-3572A5.svg?logo=Python&logoColor=white)
![SQL](https://custom-icon-badges.herokuapp.com/badge/SQL-e38c00.svg?logo=SQL&logoColor=white)

FindItNow は、ファイルを効率的に検索するためのツールです。
このツールはPythonのTkinterライブラリを使用してGUIアプリケーションとして作成されており、データベース内のファイル情報を検索し、結果を表示します。

## 主な機能

- 任意のディレクトリのファイル情報をSQL形式のデータベース化
  - CUIソフトのみ提供
- データベース内のファイル情報を検索
- 検索結果の表示とファイルのオープン
- 検索は[専用演算子](#検索)を使用した高度な検索
- グラフィカルなユーザーインターフェース

## 開発環境

- Python 3.x
- Tkinterライブラリ

## 使い方

### 基本編

1. データベースを選択
2. 検索キーワードや条件を入力([後述](#検索))
3. Enterキーを押して検索を開始
4. 検索結果がリストとして表示される
    - 表示例
        > D {C:\Program Files\Git}  
        > F {C:\Program Files\Git\git-bash.exe}
        - D : ディレクトリを意味する
        - F : ファイルを意味する
    - 以下の操作でファイルを開くことが可能
        - ダブルクリック
    - 以下の操作で選択したファイル・ディレクトリのパスをコピー可能
        - `Ctrl` + `左ダブルクリック`
        - 注意
            - `Ctrl` + `c` はOS標準の機能が優先されるためパスのみのコピー不可
            - 上記表示例の場合「D {C:\Program Files\Git} 」などとコピーされる点に注意
    - 以下の操作で選択したファイル・ディレクトリの親ディレクトリのパスを開くことが可能 (v0.2.0)
        - `Alt` + `左ダブルクリック`
    - 以下の操作で選択したファイル・ディレクトリの親ディレクトリのパスをコピー可能 (v0.2.0)
        - `Ctrl` + `Alt` + `左ダブルクリック`

### 応用編

#### 絞り込み検索時にNOT条件を追加する

- 効果
  - 検索条件から指定除外が可能
- 入力例
  - > !pptx
- 意味
  - > NOT pptx
  - pptxを含まない

#### ( )の活用

- 効果
  - 複雑な入力の簡易化
  - 下記のような冗長な入力の場合
    - 冗長な入力
      - > 資料 pptx | 資料 doc | 資料 xlsx
    - 意味
      - > 資料 AND pptx OR 資料 AND doc OR 資料 AND xlsx
      - 資料 かつ pptx もしくは 資料 かつ doc もしくは 資料 かつ xlsx
  - 下記のように簡易化が可能
    - 入力例
      - > 資料 (pptx|doc|xlsx)
    - 意味(下記2つは同じ意味)
      - > 資料 AND (pptx OR doc OR xlsx)
      - 資料 かつ (pptx もしくは doc もしくは xlsx)

## ヘイシャの方へ

### データベースについて

ヘイシャの方はShearePointの当該チャネルの「ファイル」をご自身のOneDriveと同期してください。  
ヘイシャ用のデータベースが同期されます。

### Windows用の実行ファイルについて

同期されたフォルダ内のWindows用の実行ファイル「finditnow_gui.exe」をご使用ください。

## 検索

### 検索用演算子の意味

| 入力 | 意味 |
| :--: | :--: |
| ␣    | AND  |
| \|   | OR   |
| !    | NOT  |
| (    | (    |
| )    | )    |

␣ : スペース

### 入力例

| 入力           | 意味                      |
| :-             | :-                        |
| a b            | a AND b                   |
| !a b           | NOT a AND b               |
| a (!b\|c)      | a AND (NOT b OR c)        |
| (a b)\|!(c d)  | (a AND b) OR NOT(c AND d) |
| (a\|(!b\|c)) d | (a OR (NOT b OR c)) AND d |

## ライセンス

このプロジェクトはMITライセンスの下で公開されています。詳細については、[LICENSE][LICENSE]ファイルを参照してください。

[LICENSE]: https://github.com/mizu-99/FindItNow/blob/master/LICENSE


## 作者
FindItNowは、GitHubで[Mizu-99][Mizu-99]によって開発されました。

[Mizu-99]: https://github.com/mizu-99
