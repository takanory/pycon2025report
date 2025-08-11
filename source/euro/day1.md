# カンファレンスDay 1

## オープニング

カンファレンスのオープニングです。
カンファレンスのChairからあいさつなどがありました。
「初めてEuroPythonに参加した人？」という呼びかけには、半分くらいの人が手を上げていたようです。
多いですね。

```{figure} images/opening.jpg
:width: 400

オープニング
```

プログラムチームからはキーノートなどの紹介がありました。
また、オープンスペースとライトニングトークの申し込みがフォームになったというアナウンスがありました。
PyCon US同様ここにも電子化の波が！

```{figure} images/keynotes.jpg
:width: 400

5名のキーノートスピーカー
```

## Keynote: Savannah Bailey

* <https://ep2025.europython.eu/session/you-dont-have-to-be-a-compiler-engineer-to-work-on-python>

最初のキーノートはSavannah Bailey氏による「You don't have to be a compiler engineer to work on Python」です。
直訳すると「コンパイラーのエンジニアじゃなくてもPythonに携わることができる」といった感じでしょうか。

```{figure} images/savannah.jpg
:width: 400

Savannah Bailey氏
```

Savannah氏は2020年頃プロダクトマネージャーとして働いており、自身の所属するチームがLanguage Serverなどをやっており、その頃にPythonの動作を学んだそうです。
チームとしては[typeshed](https://github.com/python/typeshed)[^typeshed]に貢献していたそうです。

[^typeshed]: Pythonの標準ライブラリに対して型アノテーションを追加するためのライブラリ

Pythonの開発としてはCPythonのインタプリターを開発する作業もありますが、それ以外にも以下のような細かい作業も大事だという話をしていました。

* issueのトリアージ（重要な課題をとりあげたり、そうでもないものや重複している物を閉じたりする作業）も大事だし、
* 公式ドキュメントの更新、typoの修正や翻訳など
* 標準ライブラリへの貢献：issueのトリアージ、ドキュメントの更新、テストカバレッジの改善

このように、CPythonのインタープリターがどのような入出力をしてPythonが実行されているかを知らなくても、Pythonに貢献できるということが語られました。
興味があれば、学びながら貢献ができます。
実際にSavannah氏もできるところからCPythonへの貢献をはじめたそうです。

Savannah氏の地道な貢献により、氏をCPythonのコア開発者チームのメンバーにする提案が2024年11月に行われ、賛成多数によりコア開発者の一人となりました。

* [Vote to promote Savannah Ostrowski - Committers - Discussions on Python.org](https://discuss.python.org/t/vote-to-promote-savannah-ostrowski/70302)

また、自身にDevOpsの経験があるため、CPythonのJITありバージョンのCI/CDやビルドについて貢献し、また、PEP 774の作者としてJITのビルドについて提案をしています。

* [PEP 774 – Removing the LLVM requirement for JIT builds | peps.python.org](https://peps.python.org/pep-0774/)
* [PEP 774: Removing the LLVM requirement for JIT builds - PEPs - Discussions on Python.org](https://discuss.python.org/t/pep-774-removing-the-llvm-requirement-for-jit-builds/78548/25)

また、Savannah氏はPython 3.16と3.17のリリースマネージャーとなるそうです。
すごい活躍です。

* [Welcome the 3.16 and 3.17 Release Manager: Savannah Bailey! - Core Development - Discussions on Python.org](https://discuss.python.org/t/welcome-the-3-16-and-3-17-release-manager-savannah-bailey/100163)

Savannah Bailey氏からは貢献をはじめるためのツールキットとして、以下が示されました。

* [github.com/python/cpython](https://github.com/python/cpython/)>：Pythonコードが管理されており、issueの確認、PRの提出やリポジトリでコードを参照できる
* [peps.python.org](https://peps.python.org/)：Pythonの大きな変更を提案、説明するドキュメント
* [discuss.python.org](https://discuss.python.org/)：機能、ガバナンス（管理方法）、パッケージングやアイデアに関してハイレベルな議論が行われる場所
* [devguide.python.org](https://devguide.python.org/)：貢献をはじめるための必要な物がある。セットアップ、ツール、トリアージの手順、テストなど

まさに、コンパイラーのエンジニアじゃなくてもCPythonの開発に携わって貢献できるということを、Savannah氏自身が体現していると感じました。
筆者自身もできるところから貢献することができるかも知れないと感じる、とても印象的なキーノートでした。

## Exploring the CPython JIT

* <https://ep2025.europython.eu/session/exploring-the-cpython-jit>
* スピーカー：[Diego Russo](https://ep2025.europython.eu/speaker/diego-russo/)
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

## Pythonクイズ

1日目のライトニングトークの前にPython Quizがありました。
これは各参加者がスマートフォンやPCから指定されたサイトにアクセスして、クイズに同時に挑戦するというものです。
[Mentimeter](https://www.mentimeter.com/)というサービスを使っているようです。

```{figure} images/quiz1.jpg
:width: 400

クイズに532名が参加！
```

素早く回答した方が高得点になるのですが、後半に進むに従ってクイズの内容がめちゃくちゃ難しくなります。
筆者の結果は236位と全然だめでした...
ただ、とても楽しかったです。

## ライトニングトーク

ライトニングは今年からフォームでの申し込みで、午後に採択された人に連絡が来ます。
筆者も申し込みましたが返事が来ないため落選したようです。

最初のライトニングトーク「Lessons for a Lightning Talk」と題してライトニングトークについて話していました。
ライトニングトークをすると自分のことを知ってもらえる、一回で700名に対して自己紹介できるのでやるべきだ、という話をしていました。
私も全く同意です。

```{figure} images/lt1.jpg
:width: 400

Lessons for a Lightning Talk
```

## Pyvo

この日の夜は、チェコのローカルコミュニティ主催で[Pyvo](https://ep2025.europython.eu/pyvo/)というカジュアルなパーティーが行われました。
この名前はチェコ語でビールのことを"Pivo"というのにかけています。

カンファレンス会場から歩いて10分くらいにある、[Na Hradbách](http://www.na-hradbach.cz/)という屋外のビアガーデンに適当に集まってビールを飲みます。
ただ、別に貸し切りというわけではないので、誰がEuroPython参加者なのかよくわかりません。

```{figure} images/pyvo1.jpg
:width: 400

Pyvoの会場の様子
```

[Pyvec](https://pyvec.org/en/)とEuroPythonのサポートによりフードも多少は提供されるのですが、参加人数が多いため私も小さいハンバーガーを1つ確保するのが精一杯でした。
また、イベントの途中でDjangoのコミュニティからDjango 20周年を記念したケーキの差し入れがありました。
とてもかわいらしいケーキです。

```{figure} images/django-cake.jpg
:width: 200

Django 20周年ケーキ
```

夜も更けると楽器を持ってきた参加者が演奏を始めてみんなで歌っていました。
なかなかカオスです。
Pyvo自体は19時くらいから始まっていて、このときは22時半頃です。
私は全種類のビールを一通り飲んだので会場を後にし、カンファレンス1日目を終えました。

```{figure} images/pyvo.mp4
:width: 400
:class: controls

カオスなPyvo
```

