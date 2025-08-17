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
ファイル名のとおりフォーマットは[TOML](https://toml.io/)形式です。
ファイルレベルの詳細情報としては以下が必要です。

```toml
lock-version = "1.0"
environments = ["..."]
requires-python = "..."
extras = ["..."]
dependency-groups = ["..."]
default-groups = ["..."]
created-by = "..."
```

そして`[[packages]]`以下に具体的なパッケージの情報が記述されます。
詳細は上記のファイル使用を確認してください。

### なぜ4年かかったのか

トークの後半ではタイトルの「なぜ仕様の策定に4年かかったのか」の話となります。
はじまりは4年どころか2019年に遡ります。
古いWebサイト（おそらくTwitter）でBrett氏がある人の発言に対して「そのロックファイルPythonのオフィシャルではなくツール固有のものなので、安定性はツールの作者に聞いて欲しい」という発言に対して、Tzu-ping Chung氏から「交換可能なロックファイルフォーマットの議論をした方がよさそう」と返し、Brett氏が「そうですね、頭の片隅で考えています」という返答をしていました。
ちなみに、Tzu-ping氏はPyCon TaiwanのメンバーでEuroPythonにも参加しており、筆者も仲良くさせてもらっています。

```{figure} images/brett-tp.jpg
:width: 400

ロックファイルについてのやりとり
```

2019年にrequirements.txt v2についての議論が行われて106ポスト、2020年にも継続して43ポストが投稿されました。

* [Structured, Exchangeable lock file format (requirements.txt 2.0?) - Packaging - Discussions on Python.org](https://discuss.python.org/t/structured-exchangeable-lock-file-format-requirements-txt-2-0/876)

2021年にはPEP 665が提案され、359ポストの議論が行われ、最終的に却下されました。

* [PEP 665 – A file format to list Python dependencies for reproducibility of an application | peps.python.org](https://peps.python.org/pep-0665/)
* [PEP 665: Specifying Installation Requirements for Python Projects - Packaging - Discussions on Python.org](https://discuss.python.org/t/pep-665-specifying-installation-requirements-for-python-projects/9911)
* [PEP 665, take 2 -- A file format to list Python dependencies for reproducibility of an application - Packaging - Discussions on Python.org](https://discuss.python.org/t/pep-665-take-2-a-file-format-to-list-python-dependencies-for-reproducibility-of-an-application/11736)

その後2024年にPEP 751が提案され、974ポストの議論が行われました。
PEP 751は最初の提案から2度の改変を経て、2025年1月に提案したバージョンで承認されました。

* [PEP 751 – A file format to record Python dependencies for installation reproducibility | peps.python.org](https://peps.python.org/pep-0751/)
* [PEP 751: lock files (again) - Packaging / Standards - Discussions on Python.org](https://discuss.python.org/t/pep-751-lock-files-again/59173)
* [PEP 751: now with graphs! - Packaging / Standards - Discussions on Python.org](https://discuss.python.org/t/pep-751-now-with-graphs/69721)
* [PEP 751: one last time - Packaging / Standards - Discussions on Python.org](https://discuss.python.org/t/pep-751-one-last-time/77293)

ここに至るまで4年間で1,800件以上の投稿があったということで、ものすごく大変な作業だったなと感じました。
こうして作成されたロックファイルの仕様ですが、すでに各種ツールが対応しているそうです。

* メインのロックファイルとして使用：[PDM](https://pdm-project.org/)
* インストール対応：PDM、[uv](https://docs.astral.sh/uv/)
* 生成に対応：PDM、uv、[pip](https://pip.pypa.io/en/stable/)

このように長い年月をかけて仕様が策定されたロックファイル（pylock.toml）ですが、すでに各種パッケージング関連のツールも対応しており、今後標準として活用されていくと思われます。
このようにたくさんの人達の議論の上に仕様が策定されるということで、中心を担ったBrett Cannonさんには本当にお疲れ様と思いました。

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
