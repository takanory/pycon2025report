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

## Behind the Scenes: PSF Infrastructure and How You Can Contribute

* https://ep2025.europython.eu/session/behind-the-scenes-psf-infrastructure-and-how-you-can-contribute
* 前半はPSFの紹介
* Ee DurbinがDirector of Infrastructure
* 内部でCabotageってのを使っている? https://github.com/cabotage/cabotage-app

## Keynote: Behind the scenes of FastAPI and friends for developers and builders

* トーク概要：<https://ep2025.europython.eu/session/behind-the-scenes-of-fastapi-and-friends-for-developers-and-builders>

カンファレンス2日目夕方のキーノートスピーカーは、FastAPIの作者であるSebastián Ramírez氏です。
このキーノートでは[FastAPI](https://fastapi.tiangolo.com/ja/)を作成して広めていく過程の中Sebastián氏がどのようなことをしてきたか、という内容が語られました。
Sebastián氏はEuroPythonに参加することは初めてだそうです。
トークの冒頭で「今日は話すことがたくさんあるので、Pabloより速くしゃべるよ」と言って会場の笑いをとっていました。
[Pablo](https://pablogsal.com/)氏は早口だと筆者も思っていましたが、共通認識のようです。

```{figure} images/sebastian.jpg
:width: 400

Sebastián Ramírez氏
```

トークの前半はFastAPI自体の簡単な紹介です。
Webフレームワークとして非常に多くのGitHubスターを持っており、日々大量にダウンロードされています。
[Python Developer Survey](https://lp.jetbrains.com/python-developers-survey-2024/#frameworks-and-libraries)の調査でも利用が伸びており、PythonでWeb APIを構築するためのフレームワークとして広く利用されていることがわかります。

次にSebastián氏の過去について振り返ります。
コロンビア出身のSebastián氏は幼稚園の段階でドロップアウトしたそうです。
その後は自宅で勉強しながら、コンピューター、ビデオ編集、楽曲制作、グラフィックデザイン、Web開発、親の仕事用のシステム開発をしていたそうです。
コンピューターにはまり、[cousera](https://www.coursera.org/)、[edX](https://www.edx.org/)、[Udacity](https://www.udacity.com/)のようなオンラインコースで世界中の人と一緒に学んだそうです。
似たようなプロダクトを0から開発することを繰り返す中で、似たような複雑な処理があることに気づきました。
このような問題を解決するために、FastAPIなどのプロダクトを開発していると述べました。

* メンテナーじゃなくてユーザーのために最適化する
  * **kwargsはだめ
* 同じ名前を異なるものにつけない
* よいドキュメントを書く

## Social Event

この日は[Social Event](https://ep2025.europython.eu/social-event/)です。
会場は[Střelecký Island](https://www.google.com/maps/place/St%C5%99eleck%C3%BD+Island/@50.0808254,14.4100926,138m/data=!3m1!1e3!4m6!3m5!1s0x470b94fac3cf3515:0x80d309307da30232!8m2!3d50.0812108!4d14.4098907!16s%2Fg%2F1v8kzb1g?hl=en&entry=ttu)という川の中にある島です。
ちなみに、この島がある川が[ヴルタヴァ川（モルダウ）](https://ja.wikipedia.org/wiki/%E3%83%B4%E3%83%AB%E3%82%BF%E3%83%B4%E3%82%A1%E5%B7%9D)です。

```{figure} images/island.jpg
:width: 400

Social Event会場の島
```

```{figure} images/social.jpg
:width: 400

Social Event会場の入り口
```

Social Eventでは食事が提供され、ドリンクも最初の1杯は無料です。
[Bubeneč](https://pivovarbubenec.choiceqr.com/section:napoje/nase-piva)という地元のクラフトビールがお店を出していたので、ここのビールを飲んでいました。

いろんな人と話をしましたが、途中であいにくの雨となり、テントがあるところからあまり動けなくなったのが残念です。
途中で入り口にもなっている建物の方にも行ったんですが、なぜか台湾と韓国から来たメンバーが3DSでマリオカートで遊んでました。
なぜここでマリオカートを...


他のビールも飲みたいなと思い、会場を後にして[Sibeeria](https://sibeeria.cz/)というクラフトビールの店に行きました。
この店は日本に海外唯一の支店があり、チェコのクラフトビール情報を仕入れようと事前に訪問していました[^sibeeria]。
無事チェコのSibeeriaに行くことができたので、個人的は満足です。

```{figure} images/sibeeria.jpg
:width: 400

チェコのSibeeriaに来たぞ！
```

[^sibeeria]: <https://x.com/takanory/status/1939867830742393090>
