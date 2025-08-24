# カンファレンスDay 2

カンファレンス2日目です。

## キーノート：Brett Cannon

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

* トーク概要：<https://ep2025.europython.eu/session/a-new-safe-external-debugger-interface-for-cpython>
* スピーカー：Pablo Galindo Salgado氏

本トークではPythonのコア開発者でありSteering CouncilのメンバーでもあるPablo Galindo Salgado氏により、CPython 3.14の新機能である安全な外部デバッガー用のインターフェースについて、どのように作成されたか裏側が紹介されました。

Safe external debuggerはPEP 768で提案され、CPython 3.14から有効になります。
この機能により、実行中のCPythonに対して安全にアクセスできるデバッグ用のインターフェースが提供されます。

* [PEP 768 – Safe external debugger interface for CPython | peps.python.org](https://peps.python.org/pep-0768/)

あわせてPythonのデバッガーであるPDBに、このインターフェースに接続する機能が追加されました。
以下のコマンド例のように`-p`オプションでプロセスIDを指定すると、そのプロセスのリモートデバッグができます。

```bash
python -m pdb -p 1234
```

```{figure} images/pablo.jpg
:width: 400

Pablo Galindo Salgado氏
```

現代は脳の検査をするときにはMRIなどが使用できるが、Pythonの動作しているプログラムを調べるにはこの絵のように外から見ることしかできません（面白い絵ですね）。
この状況を改善するためにPEP 768が提案され、機能が追加されました。

以降はリモートデバッグがどのように動作するか、内部の動作が詳細に説明されました。
そしてデモが行われ、動作しているプロセスにデバッガーがアクセスするとそこで処理が止まり、安全に内部の情報を取得できることが確認できました。

CPython 3.14の新機能により、動作しているプログラムのデバッグが便利にできそうで楽しみです。

## Performance improvements in 3.14 and maybe 3.15

* トーク概要：<https://ep2025.europython.eu/session/performance-improvements-in-3-14-and-maybe-3-15>
* スピーカー：Mark Shannon氏

Mark Shannon氏はCPythonのコア開発者で、Faster CPythonというPythonを高速化するチームをリードしています。
今回のトークでは3.14と3.15でのCPythonのパフォーマンス改善について語られました。

```{figure} images/mark.jpg
:width: 400

Mark Shannon氏
```

上の画像のスライドにあるように、CPythonの高速化には「銀の弾丸はない」ということが語られていました。
どういうことかというと、CPythonでどの処理にどれだけの時間を使っているかを調べてみると以下の様になります。
まんべんなく時間を使っているため、どこか一カ所（例えばインタープリター）を速くしただけではパフォーマンスは大きく改善しないということです。

* インタープリター：20%
* JIT：9%
* メモリの割り当てと解除：20%
* GC：12%
* lookupとdynamic：15%
* それ以外：32%

CPython 3.15では「Top-of-stack Caching」という仕組みが入る見込みで、`c = a + b`というコードを例に、スタックの読み込みと書き込みの回数がキャッシュによって減るということが示されました。
以下の様な単純なコードを例にして実行してみると、Python 3.10では28452ms、Top-of-stack Cachingに対応したPythonでは64msとなっていました
（ただこれはPython 3.10と比べているので、Python 3.14と比べた場合にパフォーマンスがどこまで改善しているのかが気になりました）。

```python
import time

def loop(n):
    t = 0
    if n < 0:
        raise ValueError  # Put breakpoint here
    for i in range(n):
        t += 1
    return t

t = time.monotonic_ns()
loop(10_000_000)
d = time.monotonic_ns() - t
print (f"{d/1000_000:.0f} ms")
```

他にはCPython 3.14では[Incremental garbage collection](https://docs.python.org/ja/3.14/whatsnew/3.14.html#incremental-garbage-collection)が導入され、少しGCが速くなり、一時停止の時間も短くなるとのことです。
3.15では"Cnadidate rood" garbage collectionが導入されるかもとのことです。

最後にCPythonの継続的なパフォーマンス改善のために資金を提供して欲しいという呼びかけがありました。
Pythonの運用に多額の費用をかけていて、パフォーマンス向上から利益が得られる会社は、ぜひ話をしにきてほしい、とのことです。

CPythonは継続的にパフォーマンスが改善していますが、そのためにはコア開発者の方々の貢献が必要です。
資金の援助は重要な問題だなと感じました。

## キーノート：Sebastián Ramírez

* トーク概要：<https://ep2025.europython.eu/session/behind-the-scenes-of-fastapi-and-friends-for-developers-and-builders>

カンファレンス2日目夕方のキーノートスピーカーは、FastAPIの作者であるSebastián Ramírez氏です。
このキーノートでは「Behind the scenes of FastAPI and friends for developers and builders」と題して、[FastAPI](https://fastapi.tiangolo.com/ja/)を作成して広めていく過程の中Sebastián氏がどのようなことをしてきたか、という内容が語られました。
Sebastián氏はEuroPythonに参加することは初めてだそうです。
トークの冒頭で「今日は話すことがたくさんあるので、Pabloより速くしゃべるよ」と言って会場の笑いをとっていました。
[Pablo](https://pablogsal.com/)氏は早口だと筆者も思っていましたが、共通認識のようです。

```{figure} images/sebastian.jpg
:width: 400

Sebastián Ramírez氏（スライドのイラストがかわいい）
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

プロダクトを開発するためのTipsとしてたくさんのポイントが示されました。
「メンテナーではなく、ユーザーのために最適化する」では以下のTipsが紹介されました。

* ユーザーの視点を持つ
* まずUXをデザインし、それに合わせて内部を作成する
* 型ヒントを指定してオートコンプリートに対応する
* 型ヒントに依存したインラインエラー
* 明示的な引数にする、`**kwargs`は使わない

「新規いユーザーを捕まえる」ためのTipsは以下です。

* 新鮮な目を持つ
* 情報の空白になっている箇所を見つける
* 初心者から意見を取り入れる

「情報の重複を減らす」ためのTipsは以下です。

* コードの重複のことではない
* 変数や設定の重複を減らす
* 情報の重複は「キャッシュ」である
* 重複が必要な情報は近くに配置する
* 同期されない状態を減らす

「よいドキュメントを書く」では非常にたくさんのTipsが示されました。

* 事前に説明すべきことは何か？
* コンセプトを表すグラフ
* すべてを説明する
* 読み直して書き直して、きれいにする、文章を削る
* コンセプトの重複を減らす
* ユーザーが最小限の努力で最大の価値を得られるようにする
* 空白、画像、絵文字、メモを入れて読みやすくする
* 用語と概念の一貫性を保つ
* 用語と概念のスタイルを設定する
* パワーユーザーにも対応する
* ドキュメント主導で開発する
* ドキュメント上でサンプルコードがテストできる

トークの後半では大規模プロジェクトを管理するためのTipsがいくつも示されました。
ここでは作業量、課題の管理、プルリクエストの処理、レビューの進め方などが説明されました。
また、大規模プロジェクトの運営は「得るものもあれば、痛みを伴うこともある（Yes gain, yes pain）」とまとめられました。
最後に「問題を解決しよう（Solve a problem）」と伝えてトークが締めくくられました。

人気があり大規模プロジェクトであるFastAPIの作者であるSebastián氏から示された多数のTipsは、「確かにそれ大事だよな」と思わせる説得力のあるものでした。
そして、一つ一つは当たり前のことだったりするんですが、その当たり前のことを当たり前にやり続けているであろうSebastián氏とFastAPIチームのすごさを感じました。

なおSebastián氏は[PyCon JP 2025](https://2025.pycon.jp/)にキーノートスピーカーとして来日します。
本トークのような素晴らしいトークが聞けると思います。
筆者も日本での最下位を楽しみにしています。

## ソーシャルイベント

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
無事チェコのSibeeriaに行くことができたので、個人的には大満足です。

```{figure} images/sibeeria.jpg
:width: 400

チェコのSibeeriaに来たぞ！
```

[^sibeeria]: <https://x.com/takanory/status/1939867830742393090>
