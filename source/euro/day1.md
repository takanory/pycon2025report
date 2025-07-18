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
(whitphxさんに書いて欲しい)
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
