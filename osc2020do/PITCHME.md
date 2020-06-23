## Python開発環境の整え方

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
* `python3.8 -m venv 環境名`
* `. 環境名/bin/activate`

```sh
$ python3.8 -m venv env
$ . env/bin/activate
(env) $
```

+++

## venv作成、有効化

* Windows
* `py -3.8 -m venv env`
* `env\Scripts\activate.ps1`

```sh
> py -3.8 -m venv env
> env\Scripts\activate.ps1
(env) >
```

+++

## venvとは

* パスを書き換えているだけ
* 削除するときはフォルダーごと削除

+++

## venv無効化

* `deactivate`
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
(env) $ pip install beautifulsoup4
Collecting beautifulsoup4
  Downloading beautifulsoup4-4.9.1-py3-none-any.whl (115 kB)
     |████████████████████████████████| 115 kB 2.1 MB/s 
Collecting soupsieve>1.2
  Downloading soupsieve-2.0.1-py3-none-any.whl (32 kB)
Installing collected packages: soupsieve, beautifulsoup4
Successfully installed beautifulsoup4-4.9.1 soupsieve-2.0.1
```

+++

## pipでインストール

* バージョン指定
  * `pip install パッケージ名==バージョン`
* 最新にアップグレード
  * `pip install -U パッケージ名`

```bash
(env) $ pip install beautifulsoup4==4.8.0
: (省略)
      Successfully uninstalled beautifulsoup4-4.9.1
Successfully installed beautifulsoup4-4.8.0
(env) $ pip install -U beautifulsoup4
: (省略)
Successfully installed beautifulsoup4-4.9.1
```

+++

## パッケージ一覧を表示

* `pip list`
  
```bash
(env) pip install beautifulsoup4==4.8.0
: (省略)
(env) $ pip list
Package        Version
beautifulsoup4 4.8.0
setuptools     41.2.0
soupsieve      2.0.1
```

+++

## 古いパッケージを確認

* `pip list -o`
  
```bash
(env) $ pip list -o
Package        Version Latest Type
beautifulsoup4 4.8.0   4.9.1  wheel
setuptools     41.2.0  47.3.1 wheel
```

+++

## パッケージ一覧を再利用

* `pip freeze > requirements.txt`
* requirements.txtファイルをバージョン管理

```bash
(env) $ pip freeze > requirements.txt
(env) $ cat requirements.txt
beautifulsoup4==4.8.0
soupsieve==2.0.1
```

* 別の仮想環境でインストール

```bash
$ python3.8 -m venv newenv
$ . newenv/bin/activate
(newenv) $ pip install -r requirements.txt
(newenv) $  pip freeze
beautifulsoup4==4.8.0
soupsieve==2.0.1
```

+++

## アンインストール

* `pip uninstall -y パッケージ名`
* 依存パッケージは削除されない

```bash
(env) $ pip uninstall -y beautifulsoup4
Found existing installation: beautifulsoup4 4.8.0
Uninstalling beautifulsoup4-4.8.0:
  Successfully uninstalled beautifulsoup4-4.8.0
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

* `pip install flake8`

+++

## だめなコード

```python
TODO: ここにだめなコードを入れる
```

+++

## Flake8を実行

* `flake8 ファイル名`

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

* `pip install black`

+++

## だめなコード

```python
TODO: だめなコード
```

+++

## Blackを実行

* `balck ファイル名`

```sh
$ black hoge.py
```

---

## まとめ

+++

## まとめ

* Python公式版
* venvで仮想環境
* pipでパッケージ管理
* Flake8で静的チェック
* Blackでコード整形

---

## ありがとうございました 🙇‍♂️

---

## Question?


