# カンファレンスDay 2


## Keynote: Brett Cannon

* トーク概要：<https://ep2025.europython.eu/session/why-it-took-4-years-to-get-a-lock-files-specification>
* スライド：<https://opensource.snarky.ca/Talks/2025/EuroPython/Slides>

Brett Cannon氏はPythonのコア開発者の一人で、2019年から2023年までSteering Councilを務めた方です。
このトークではタイトル「Why it took 4 years to get a lock files spec」の通り、Pythonのロックファイルの仕様をまとめるまでに4年かかった話が語られました。

```{figure} images/brett.jpg
:width: 400

Brett Cannon氏
```

最初に現在のPythonパッケージを作成するためのファイル構成について説明がありました。
[pyproject.toml](https://packaging.python.org/en/latest/guides/writing-pyproject-toml/)、[sdist](https://packaging.python.org/en/latest/specifications/source-distribution-format/)フォーマット、[wheel](https://peps.python.org/pep-0491/)などが紹介されました。

そして、パッケージ間の依存関係の指定にはいろいろな書き方があるため、これを解決することはとても難しいそうです。
パッケージの依存関係を記述するファイルとして`requirements.txt`、`poetry.lock`、`pdm.lock`、`uv.lock`があり、ツールごとにバラバラという状況です。
そこで、Pythonのロックファイルを標準化したが、そのためには4年の月日がかかったとのことです。
標準化された`pylock.toml`ファイルの仕様は以下で確認できます。

* [pylock.toml Specification - Python Packaging User Guide](https://packaging.python.org/en/latest/specifications/pylock-toml/)

ロックファイルは以下のような設計方針で仕様を検討したそうです。

* ソフトウェアで作成し、人間にも読みやすい
* デフォルトで安全な設定
* 依存関係の解決をせず素早くインストールできる
* ロックファイルの生成ツールとインストーラーは異なるツールもありえる
  * インストーラーはPython製である必要はない
* 単一と複数環境のそれぞれのシナリオに対応する

そしてpylock.tomlの細かいファイル仕様について説明が行われました。

* pylock.tomlの構造について説明
* ファイルレベルの説明

### なぜ4年かかったのか

* 2019にrequirements.txt v2について 106ポスト
* 2020に43ポスト
* 2021 PEP 665 https://peps.python.org/pep-0665/
* 2022 PEP 665 rejected
* 2023 54 posts
* 2024 PEP 751 https://peps.python.org/pep-0751/

## A new safe external debugger interface for CPython

* https://ep2025.europython.eu/session/a-new-safe-external-debugger-interface-for-cpython
* MRIで検査を受けた?
* PythonのMRIはこんな感じ(画像)
* https://peps.python.org/pep-0768/

```
$ readelf -h python
```

## Building a new tail-calling interpreter for Python

* https://ep2025.europython.eu/session/building-a-new-tail-calling-interpreter-for-python

実際に実行しているプロセスにアクセスして処理を止めることができるデモ

PYTHON_DISABLE_REMOTE_DEBUG / -X disable-remote-debug

* Future

## Building a new tail-calling interpreter for Python

* https://ep2025.europython.eu/session/building-a-new-tail-calling-interpreter-for-python

* パフォーマンスを見るところでベンチマークを見るとinterpreterが30%と多い
* interpreterはbytecodeを実行するところ
* swtich caseだとジャンプで遅くなる場合がある。今は違う実装になっている。dispatchテーブルを使って飛ぶ
* The Cake is a lie https://en.wikipedia.org/wiki/The_cake_is_a_lie
* 多少速くなった

## Performance improvements in 3.14 and maybe 3.15

* https://ep2025.europython.eu/session/performance-improvements-in-3-14-and-maybe-3-15
* 高速化に銀の弾丸はない
* Top-of-stack Caching→3.15で入るっぽい?
* c = a + bは5回読み込み4回書き込み
* キャッシュがあると2回読み込み、1回書き込みになる
* デモを実行して高速化していることを確認
* Python 3.6以降のデータの持ち方について説明
* リファレンスカウントの処理を軽量化
* Faster cyclic garbage collection

## Pydantic, Everywhere, All at Once

https://ep2025.europython.eu/session/pydantic-everywhere-all-at-once

* ベーグルを注文する例で伝える

## Behind the Scenes: PSF Infrastructure and How You Can Contribute

* https://ep2025.europython.eu/session/behind-the-scenes-psf-infrastructure-and-how-you-can-contribute
* 前半はPSFの紹介
* Ee DurbinがDirector of Infrastructure
* 内部でCabotageってのを使っている? https://github.com/cabotage/cabotage-app

## Keynote: Behind the scenes of FastAPI and friends for developers and builders

* https://ep2025.europython.eu/session/behind-the-scenes-of-fastapi-and-friends-for-developers-and-builders
* FastAPIの紹介。さまざまなところで使われている。
* 学校をドロップアウト
* Couseraとかで勉強した
* 「Solve a problem」
* メンテナーじゃなくてユーザーのために最適化する
  * **kwargsはだめ
* 同じ名前を異なるものにつけない
* よいドキュメントを書く

## Social Event

* いろいろ話した
