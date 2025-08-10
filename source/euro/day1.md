# Day 1

## Opening

* はじめてEuroPythonに参加した人を確認。半分くらい?
* EuroPython Societyが運営しているよ。ブースに来てね
* オープンスペースとLTが電子化

## Keynote: Savannah Bailey

* https://ep2025.europython.eu/session/you-dont-have-to-be-a-compiler-engineer-to-work-on-python

はじめてのEuroPython。
最近結婚したらしい。

2020年
Language ServerとかをやっていてPythonの動作を学んだ。Pylance?
チームがtypeshedとかに貢献した
PdMとして働いていた

issueのトリアージが大事だよね
ドキュメントの更新も大事だよ。typo治したりとか。翻訳したりとか

標準ライブラリへの貢献
トリアージ、ドキュメントの更新、テストカバレッジを改善

インタープリターの入出力を知らなくてもPythonに貢献できる
興味があれば学ぶことができる

DevOpsの経験からJITのCI/CDとかビルドについて貢献した
PEP 771を作成してacceptされた

Contribution Tookkit
GitHub
PEP
discuss.python.org
devguide.python.org

## Myths and fairy tales around Python performance

* https://ep2025.europython.eu/session/myths-and-fairy-tales-around-python-performance

JITコンパイラーが解決する
互換性を壊さないとPythonは速くできない

## Exploring the CPython JIT

* https://ep2025.europython.eu/session/exploring-the-cpython-jit
* CPythonへの貢献して2年、CPython JITに1年
* 2025年5月からcore developer

JITとは

3.13ではbuildでオプション
3.14は実行時のオプション

JITではμopで最適化されてnativeマシンコードになる

サンプルコードを元に動作を説明

* バイトコード化
* バイトコードのスペシャル化
* tracesで不要な命令を削除?して最適化

copy and patchの例

3.15ではJITをスレッドセーフにする。

## A tour of (some) Python JIT compilers

https://ep2025.europython.eu/session/a-tour-of-some-python-jit-compilers

* GraalPyを作っている人

## Uncovering the magic of implementing a new Python syntax feature

* https://ep2025.europython.eu/session/uncovering-the-magic-of-implementing-a-new-python-syntax-feature

* t-stringの説明、Template型になるよ
* 最近の新しい言語仕様
  * t-string
  * Pattern Matching
  * Exception Groupほか
* Tokenizer, Parser, Bytecode compiler, Interpreter
* Tokenizer: source code -> tokens
  * t"hello {name}" で6つのトークンになる
* Parser: tokens -> AST
  * トークンが正しいフォーマットかの確認の手順を詳細に説明
  * ASTの構築
  * 文法の定義にエラーメッセージも書いてあるらしい?
* Pytecode Compiler: AST->Bytecode
  * t-stringでBULD_INTERPOLATION, BUILD_TEMPLATEという新しいBytecodeができたのか
* Interpreter: Bytecodeを実行する

## PyScript as Infrastructure: Running EduBlocks at Scale Without the Cost

* https://ep2025.europython.eu/session/pyscript-as-infrastructure-running-edublocks-at-scale-without-the-cost
* PythonをBlockベースでプログラミングするツール
* https://edublocks.org/
* 2016年に初リリース
* skulptでPythonをJSで動かす https://skulpt.org/ →Pythonのバージョンが古い
* 別のアプローチとしてPyScript
* PyScriptはPyodideとMicroPython上で動く
* ブロックを組み合わせたら、そこからコードを生成してPyScript上で動作させる(どうやってるんだ??
* donkeyっていう機能で動作を制御してる? https://docs.pyscript.net/2025.2.1/api/#pyscriptcoredonkey

## A Pythonic semantic search

* https://ep2025.europython.eu/session/a-pythonic-semantic-search

* https://github.com/wsvincent/django-microframework
* microDjango https://github.com/pauloxnet/uDjango
* postgresql使うとSearchVectorとかできるの?
* VectorFieldってのがあるのか
* qdrantのvector DBにいれる→DBが更新されたらqdrantに同期
* https://pypi.org/project/pgvector/
* sentence-transformersもインストール
* ClosingDistanceで検索できる

## Keynote: Building a large SaaS AI product with Python: The tale of three ecosystems

https://ep2025.europython.eu/session/building-a-large-saas-ai-product-with-python-the-tale-of-three-ecosystems

* Rossumはロボットのこと。チェコ語?
* お金のヤル取りのトランザクジョンを処理する
* AI部分はFrask、データ管理はDjango、IntegrationはFastAPI

````{admonition} コラム：EuroPythonトーク

## トークが発表2日前にアクセプトされた話

橘祐一郎（[@whitphx](https://github.com/whitphx)）です。EuroPython 2025に参加し、トークもしてきました。

当初はプロポーザルを出したものの不採択で、一般参加者として参加する予定でした。
しかしカンファレンス2日前に、キャンセル待ちリストから繰り上がりでアクセプトされたのでした。
かなりバタバタしてしまいましたが、スピーカーになったおかげで、よりEuroPythonを楽しめました。

不採択通知およびキャンセル待ちリスト（Waiting List）入りの連絡は2ヶ月ほど前に来ていました。
直前にアクセプトされて困る場合は事前に取り下げておいてほしいという注意が度々ありましたが、私は取り下げずにキャンセル待ちを継続していました。

一方で、他所での発表予定はなかったため、仮に資料を作ってもEuroPythonで繰り上がらなければ無駄になってしまう状況でした。繰り上がりの可能性と資料作成のコストをざっと天秤にかけ、あまり深く考えずに資料は作らずに放置していました。
アクセプトを若干期待しつつも資料は作らないというこの矛盾した行動のせいで、後々苦しむことになりました…

現地にはカンファレンスの2日前に到着し、その日の夕方に「トークのキャンセルがあった。もしあなたのプロポーザルをアクセプトしたらトークできるか」というメールを受け取りました。
上述の通り、うっすら期待しつつも資料は作っていなかったので若干の逡巡がありつつも、取り下げずにいた責任もある上、何よりせっかくの貴重なチャンスなので、はいと返事をしました。

```{figure} images/whitphx_badge.jpg
:width: 400

スピーカーになったので Speaker シールを貼る権利を獲得
```

ここからが大変です。
私のトークは1日目の午後で、準備期間はおよそ1日半です。
翌日（カンファレンス前日）は会場に行き、隅のソファで一日中発表の準備をしていました。
さらにその日の夜にはスピーカーを集めたディナーイベントがありました。
私も晴れてスピーカーになったので、参加できるようになったのです。
準備が数時間削られる不安はありつつも、こんな楽しそうなイベントに行かない手はありません。
スピーカーディナーを楽しみと同時に締切だと思って、日中はひたすら資料作成に集中しました。

```{figure} images/whitphx_speakers_dinner.jpg
:width: 400

スピーカーディナーで他のスピーカーと飲むのも楽しみの一つ
```

当日（カンファレンス1日目）も発表までずっと準備をしていました。
昼休みにやっと資料が完成し、隅の方で喋りの練習を始めました。
どのパートをどの時間までに終わらせる必要があるかを確かめ、
重要な部分（特に伝えたい情報や、ストーリーの接続部分など）で大事になる言い回しを重点的に洗練させて、頭に入れていきます。

結局リハーサルは２、３回しかできずに本番を迎えましたが、なんとか時間内にやり切ることができました。
準備不足で詰め込み気味の発表でしたが、伝えたいことは伝えきれたと思います。
発表後の質疑応答では何人か手を挙げてくれ、終了後も多くの方が質問や議論をしに来てくれました。

発表自体をやりきれば、あとはカンファレンスを楽しむだけです。
やはりスピーカーになると、他の参加者との交流の機会は増えます。
前日のスピーカーディナーもそうですし、会期中はトークテーマが自分の名刺代わりになって、発表後や休み時間の雑談で話しかけてもらうネタができます。
最初の1日半だけ大変でしたが、EuroPythonを大いに楽しめました。

最後に、1日半で30分のトーク資料を作るのは本当にお勧めしません。
みなさんはもしキャンセル待ちリストに入ったら、完璧なものでなくともある程度の資料は作っておきましょう。

このときの発表資料はこちらです：[Democratize serverless web AI apps for Python devs](https://slides.whitphx.info/202507-python-serverless-web-apps/)

````

## Python Quiz

* めちゃめちゃ難しかった
* 236位だった...

## Lightning Talks

* Lightning Talkのすすめ
* みんなにしってもらえる。一度に700名に自己紹介できる

* https://github.com/IljaManakov/quack_walk_snake

* SSTVっていう画像を音声で送信する方法?
* https://en.wikipedia.org/wiki/Slow-scan_television

## Pyvo

カオス
