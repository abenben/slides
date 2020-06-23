## タイトル

#### サブタイトル

2020年6月27日 / OSC Online/Hokkaido

鈴木たかのり

<!-- https://docs.google.com/document/d/1sfhGtTWzKcSUvPucC851jxF9c1DkW9GWb1MDCeDxWjU/edit -->

---

## アジェンダ

* Pythonの環境について
* 開発環境を整える方法
* その他

---

## Tweets 🐦 👍

`#osc2020do` / `@takanory`

+++

## スライドはこちら

* @fab[github] [`github.com/pyconjp/slides`](https://github.com/pyconjp/slides)

+++

## どんどん質問してください ‍🙇‍♂️

---?include=assets/takanory.md

+++

## 私と北海道

* 釧路市出身
* 小中学校は阿寒町
* 釧路高専出身
* OCS 2019 Hokkaidoに初参加

+++?image=osc2020do/images/osc2019do.jpg&size=90% auto

---?include=assets/pyconjp2020.md

+++

## Python Charity Talks

* https://pyconjp.connpass.com/event/177586/
* 2020年7月4日(土) 13:00-18:00
* オンラインイベント
* 参加費は全額Python Software Foundation(PSF)に寄付

+++

## ミーティングにも来てね

* F会場で16:15〜17:00にセミナーの質疑応答など

+++

#### コミュニケーション用 Slack ワークスペース

- [PyCon JP Fellow Slack](https://pyconjp-fellow.herokuapp.com/)

---

## Pythonインストール

+++

## Pythonインストール

* [`www.python.org/downloads`](https://www.python.org/downloads/)から公式版をインストール
  * WindowsはPATH設定のチェックを忘れずに
* 最新バージョンは3.8.3
* 2020年10月に3.9がリリース予定

+++

## 環境構築ガイド

* [`www.python.jp/install/install`](https://www.python.jp/install/install.html)

![python.jpの環境構築ガイド](osc2020do/images/pythonjp-install.png)

+++

## 他の手段

* Anaconda: [`www.anaconda.com`](https://www.anaconda.com/)
* pyenv: ['github.com/pyenv/pyenv'](https://github.com/pyenv/pyenv)
* Homebrew: [`brew.sh`](https://brew.sh/)
* Linux:
  * Ubuntu 20.04LTS: Python 3.8.2
  
+++

## Pythonインストール

* 特に理由がなければ公式版を使おう

---

## 仮想環境(venv)

+++

## 仮想環境(venv)

* [`docs.python.org/ja/3/library/venv`](https://docs.python.org/ja/3/library/venv.html)
* Pythonに標準でついてくる
* 常に使いましょう
* プロジェクト単位で使用パッケージを変えられる

+++

## venvの概念

* システムのPython
  * venv1
    * Django 3.0.7
  * venv2
    * Django 2.2.13

+++

## venv作成、有効化

* macOS、Linux

```sh
$ python3.8 -m venv env
$ . env/bin/activate
(env) $
```

* Windows

```sh
> py -3.8 -m venv env
> env\Scripts\activate.ps1
(env) >
```

+++

## venvとは

* パスを書き換えているだけ
* 削除するときはフォルダーごと削除

```
$ rm -rf env/
```

+++

## venv無効化

* macOS、Linux

```sh
(env) $ deactivate
$
```

* Windows

```sh
(env) > deactivate
>
```

+++

## 仮想環境(venv)

* パッケージをインストールするときは常に使おう

---

## パッケージ管理(pip)

+++

## パッケージ管理(pip)

* サードパーティ製パッケージの管理ツール
* venvの中で使用するのが一般的

+++

## PyPI

* [`pypi.org`](https://pypi.org/)
* サードパーティー製パッケージの配布サイト
* 「パイピーアイ」と読むらしい

+++?image=osc2020do/images/pypi.png&size=auto 90%

+++

## pipでインストール

* `pip install パッケージ名`
* 依存パッケージもまとめてインストール

```bash
(env) $ pip install requests
:
: (省略)
:
Installing collected packages: chardet, certifi, urllib3, idna, requests
Successfully installed certifi-2020.6.20 chardet-3.0.4 idna-2.9 requests-2.24.0 urllib3-1.25.9
```

+++

## pipでインストール

* `pip install requests==2.14.0`: バージョン指定
* `pip install -U requests`: 最新にアップグレード

```bash
(env) $ pip install requests==2.14.0
: (省略)
      Successfully uninstalled requests-2.24.0
Successfully installed requests-2.14.0
(env) $ pip install -U requests
: (省略)
Successfully installed requests-2.24.0
```

+++

## パッケージの探し方

* Awesome Python: [`awesome-python.com`](https://awesome-python.com/)

![Awesome Python](osc2020do/images/awesome-python.png)


---

## テキストエディター

+++

## テキストエディター

* 好きな物を使いましょう
* とくになければ以下がおすすめ
  * VSCode: [`code.visualstudio.com`](https://code.visualstudio.com/)
  * PyCharm: [`www.jetbrains.com/pycharm`](https://www.jetbrains.com/pycharm/)

---

## 静的チェックツール(Flake8)

+++

## 静的チェックツール(Flake8)

* [`flake8.pycqa.org`](https://flake8.pycqa.org/)
* コードを静的にチェックするコマンド
  * [pycodestyle](https://pycodestyle.pycqa.org/): PEP8のチェック
  * [pyflakes](https://pypi.org/project/pyflakes/): エラーが発生しそうなコードをチェック
  * [mccabe](https://pypi.org/project/mccabe/): 循環的複雑度のチェック

+++

## PEP8

* PEP 8 -- Style Guide for Python Code
  * [`www.python.org/dev/peps/pep-0008/`](https://www.python.org/dev/peps/pep-0008/)
  * [`pep8-ja.readthedocs.io`](https://pep8-ja.readthedocs.io/): 日本語訳
* Python標準のスタイルガイド
* 主なルール
  * インデント4つ
  * 1行の最大文字数
  * 空行の入れ方
  * スペースの入れ方

+++

## Flake8をインストール

```
$ pip install flake8
```

+++

## だめなコード

```python
TODO: ここにだめなコードを入れる
```

+++

## Flake8を実行

```sh
$ flake8 sample.py
TODO: ここにエラーメッセージ
```

+++

## コードをきれいにする

```python
TODO: きれいになったコード
```

+++

## Flake8を再実行

```sh
$ flake8 sample.py
$
```

* エラーメッセージが出なくなった!!

+++

## Flake8とエディター

* 多くのエディターから直接チェックできる
* PyCharm: External Toolsで設定
* VSCode: Python Extension→設定変更
* Emacs: flycheck, flymake
* Vim: vim-flake8

---

## Black

![Black logo](/osc2020do/images/black.png)

+++

## Black

* [`black.readthedocs.io`](https://black.readthedocs.io/)
* 頑固なコードフォーマッター
* PEP8準拠のコードにしてくれる
* 設定はほぼなし
  * Blackの流儀に合わせる

+++

## Blackをインストール

```
$ pip install black
```

+++

## だめなコード

```python
TODO: だめなコード
```

+++

## Blackを実行

```sh
$ black hoge.py
```

---

## まとめ

+++

## まとめ

* Python公式版
* venvで仮想環境
* Flake8で静的チェック
* Blackでコード整形

---

## ありがとうございました 🙇‍♂️

---

## Question?


