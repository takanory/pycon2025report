# カンファレンス2日目

カンファレンス2日目です。今日も会場での朝食からスタート！！

```{figure} images/breakfast-day2.jpg
:width: 400

朝食のテーブル
```

## ライトニングトーク

* ビデオ：<https://www.youtube.com/watch?v=47NJt_3ED_k>

2日朝のライトニングトークからはEric Matthes氏による[django-simple-deploy](https://django-simple-deploy.readthedocs.io/en/latest/)を紹介します。
django-simple-deployはDjangoのプロジェクトを各種プラットフォームに簡単にデプロイできるライブラリです。
現在はFly.io、Platform.shとHerokuに対応しており、実際にデプロイするデモを行いながらトークを進め、今後さらに対応プラットフォームを増やしたいので協力して欲しいという話をしていました。

```{figure} images/lt-eric.jpg
:width: 400

Eric Matthes氏によるライトニングトーク
```

## ダイバシティ&インクルージョンのパネル

* ビデオ：<https://www.youtube.com/watch?v=SQAX4P59u8w>
* <https://us.pycon.org/2025/about/keynote-speakers/#diversity-and-inclusion-panel>

ダイバシティ&インクルージョン（D&I）のパネルディスカッションは、以下の5名により行われました
（写真の左から右の順番です）。

* Keanya Phelps氏：モデレーター。ソフトウェア開発者、PyCon US初参加
* Naomi Ceder氏：長年Pythonコミュニティに関わっており、2022年に[PSF Distinguished Service Awards | Python.org](https://www.python.org/community/awards/psf-distinguished-awards/#section-2)を受賞
* Jay Miller氏：[Black Python Devs](https://blackpythondevs.com/)の創設者。PyCon US 2024のキーノートスピーカー[^2024day1]
* Cristián Maureira-Fredes氏：スペイン語圏コミュニティの[Python España](https://es.python.org/)の主催者
* Alla Barbalat氏：モデレーター。弁護士でPython愛好家であり、サンフランシスコの[SF Python](https://www.sfpythonmeetup.com/)の主催者

パネラーはCristián氏はベルリン在住ですが、それ以外はアメリカ在住であり、昨年のD&Iパネルとは異なる方向性の話となりました。[^2024day2]

[^2024day1]: [#01 PyCon US 2024の開幕、Day 1ライトニングトークに挑戦 | gihyo.jp](https://gihyo.jp/article/2024/07/pycon-us-2024#ghdJ5nqSdH)
[^2024day2]: [#02 PyCon US 2024 Day 2、CPythonコンパイルの新たなパイプライン | gihyo.jp](https://gihyo.jp/article/2024/07/pycon-us-2024-02#gh4EPg2SZe)

```{figure} images/dandi.jpg
:width: 400

ダイバシティ&インクルージョンのパネル
```

最初にPythonコミュニティで長年D&Iに取り組んできたNaomi氏に現状について質問をすると「心配している、がっかりしている、怒っている。しかし希望も持っている」と語られました。
これはおそらく最近のアメリカの国内・国際情勢について触れていると思われます。
今回のPyCon USへの渡航に際し、入国が厳しいのではないか、スマートフォンの中身を見られる[^smartphone]といった情報が事前にあり、筆者も少し気にしていました。
実際にアメリカに住んでいるパネラーのみなさんにとっても、色々と変化があるのだなと感じられました。

Cristián氏はベルリンからの参加だったため、やはり無事にアメリカに入国できるか少し心配だったようです。
ただ「自分たちはハッキングすることが得意だから、うまく行く方法を見つけようとしている」という話をしていました。
たしかにその考え方はエンジニア全般に通じるものがあるなと感じました。
Jay氏は昨年、PyCon USに来たがホテルでクレジットカードが通らず保証金が支払えない知人がおり、すぐにホテルに向かって代わりに支払ったそうです。
これは元々の知り合いじゃないとなかなかできないことですが、確かに現実で発生しそうなことだなと思いました。
筆者も2024年のPyCon APACのホテルに着いたときに、保証金が現金のみと言われ、他のメンバーに現金を借りました（危ない）。

構造的な支援が薄れていく中でなにができるか？という質問に対して、Jay氏は率直に「財政的に支援が必要」といことが述べられました。
PyLadiesやDjango Girlsやローカルのコミュニティが継続して欲しいなら寄付をしてほしい、と伝えました。
Cristián氏はローカルのミートアップやカンファレンスの運営を手伝う、ということを述べていました。
Jay氏はさらにPython EspañaやPAO（Python Asia Organization）のように、言語や国を越えたコミュニティが発展していることは素晴らしいと語られました。

[^smartphone]: [旅行が一瞬で台無しになる…海外紙が警告｢アメリカの空港で続く"スマホ検査"の異様な実態｣ ｢怪しい｣と思われただけでデータが抜き取られるケースも | PRESIDENT Online（プレジデントオンライン）](https://president.jp/articles/-/94921)

## Keynote: Linn Root

* ビデオ：<https://www.youtube.com/watch?v=Bglsof9b23k>
* <https://us.pycon.org/2025/about/keynote-speakers/#lynn-root>

```{figure} images/linn.jpg
:width: 200px

Linn Root氏
```

````{admonition} Type Hintsを「導入で終わらせない」ために
このコラムは青野 高大([@koxudaxi](https://github.com/koxudaxi))がお届けします。

今年は [Type Hints in Real-World Projects: Practical Steps for Continuous Maintenance and Improvement](https://us.pycon.org/2025/schedule/presentation/13/) というタイトルで登壇しました。[昨年](https://us.pycon.org/2024/schedule/presentation/42/)に続く2年連続の登壇で、今回は現場でよく聞かれる「型は入れたが運用が続かない」という課題に対し、**導入後の継続** に焦点を当てています。

現場のコードでは `typing.Any` の多用、安易な `# type: ignore`、旧記法のまま残る `typing.List` などが原因で型品質が下がるケースが少なくありません。本発表では、こうした問題を大きなコストなしで改善する方法をいくつか紹介しました。代表例は次のとおりです。

* **最新機能を `typing_extensions` で先取り**  
  `TypeIs` など Python 3.13 以降の型機能を旧バージョンでも利用し、ランタイムを変えずに静的解析の精度を高めます。
* **Ruff + pyupgrade による自動リライト**  
  旧式のコレクション型(`typing.List`, `typing.Dict`)や他の古い記法を現行記法へ統一し、レビュー負荷を抑えつつコードの一貫性を保ちます。
* **限定的な `# type: ignore[...]` の採用**  
  無視するエラーコードを明示しておくことで、予期せぬ型エラーを検知できなくなる事態を防ぎます。

これらの工夫により、型ヒントを陳腐化させずに運用し続けることが可能になります。継続的な利用がプロダクションや OSS で一般化すれば、ライブラリ側の型対応やドキュメント整備も加速し、エコシステム全体で型システムがさらに促進・向上していくと考えています。

---

### 2年目の登壇で見えたこと
昨年は時間内に収めつつコード例を伝えることで精一杯でしたが、今回はプロダクションで役立つ具体策をより深く盛り込む余裕がありました。講演後のフィードバックでも「知らなかった実践例を持ち帰れた」という声が多く、整理して提示する意義を再確認しています。  
さらに、講演後に廊下で交わした会話では `typing.ParamSpec` や `typing.Concatenate` を用いても「位置引数とキーワード引数を入れ替えるデコレータで正確な型を保てない」といった相談が寄せられ、Python の型システムは発展途上でまだ改良の余地があるという共通認識を得られました。

---

私の見方では、Python が長く選ばれてきた理由の一つは、コミュニティが機能と知見を少しずつ積み上げてきた点にあります。型ヒントの運用も同じく、現場での継続的な改善が広がることで、より扱いやすい型システムへと進化していくはずです。

```{figure} images/pyconus2025_talk_koudai.jpg
:width: 400px

発表中の様子
```

````

## Why `len('😶‍🌫️') == 4` and other weird things you should know about strings in Python 

* スピーカー：Marie Roald、Yngve Mardal Moe
* ビデオ：<https://www.youtube.com/watch?v=np-xKVMIKcY>
* スライド：<https://github.com/MarieRoald/PyConUS25/blob/main/PyConUS-2025-slides.pdf>
* <https://us.pycon.org/2025/schedule/presentation/27/>

このトークではPythonでは文字列をどのように扱っているか、またUnicodeの詳細についても触れていきます。
最初に以下のようなコードがスライドが示されました。この段階で「え？なにがどうなってるの？」と思いながらトークがはじまります。
うまいフリだなと思いました。

```{code-block} python
:caption: 冒頭で示されたコード例（このコードをコピペしてもうまく動きません、すいません）

>>> "naïve" == "naïve"
True
>>> "naïve" == "naïve"
False
>>> int("৪")
4
```

```{figure} images/why-len.jpg
:width: 400px

Yngve Mardal Moe氏（左）とMarie Roald氏
```

トークは文字列のエンコーディング、比較、スライスの3つのパートに分かれて進みます。
Pythonは87種類の文字列のエンコーディング[^encoding]に対応しています。
2バイトでは65536文字に対応していますが、Unicodeでは4バイトを使用して100万以上の文字に対応しています。
同じ文字列でもエンコーディングによってサイズが変わります。

[^encoding]: <https://docs.python.org/3.13/library/codecs.html#standard-encodings>

またUnicodeの各文字にはカテゴリがあり、unicodedataモジュールの`category()`関数で取得できます。以下の`'Nd'`は十進数を意味します。

```python
>>> from unicodedata import category
>>> category("৪")
'Nd'
```

ここで冒頭に謎に迫るわけですが、この文字列を`int()`に変換するとなぜか4になります。
`name()`関数で名前を取得すると「ベンガル文字の4」であることがわかります。


```python
>>> int("৪")
4
>>> from unicodedata import name
>>> name("৪")
'BENGALI DIGIT FOUR'
```

文字列の比較では、Pythonでは`"y" is "y"`とすると「`==`じゃないの？」と警告が出ますが、結果としてはTrueが返ります。
これは時間とメモリの節約のために、Pythonではいくつかの文字を1度だけメモリ上に格納しているためです[^string_interning]。
しかし全ての文字ではないため、文字列の比較では`==`を使いましょう。

[^string_interning]: <https://github.com/python/cpython/blob/main/InternalDocs/string_interning.md>

```python
>>> "y" is "y"
<stdin>:1: SyntaxWarning: "is" with a literal. Did you mean "=="?
True
>>> "a" * 4097 is "a" * 4097
False
```

## ライトニングトークに申し込み

ライトニングトークはカンファレンス中に4回（1日目夕、2日目朝、夕、3日目朝）開催されます。
2日目夕方のライトニングトークに日本から来ていたshimizukawaさんとwhitphxさんが落ちた（10/58という狭き門）という話を聞いて、申し込みが電子化されたメリットでもありデメリットでもあるなと感じました。

「記念受験として出してみるかー」と思い、3日目朝のライトニングトークに申し込みました。
タイトルと簡単な概要文を書いて申し込みます。
この時点で発表のアイデアはありますがスライドはありません。
するとフォーム締め切り後の16時頃にメールがあり、私のライトニングトークが当選しました！！
明日の朝まで時間はあまりありませんが、ここからは集中して発表の準備を進めました。

```{figure} images/lt-accepted.png
:width: 400

ライトニングトークがAcceptされた！
```

## PyLadies Auction

カンファレンス2日目の夜は毎年恒例のPyLadies Auctionです。
このイベントはPyCon USの関係者がグッズを提供し、オークション形式で購入するというものです。
落札されたお金は全てPyLadiesに寄付されて運営資金となる、というチャリティオークションです。

```{figure} images/auction1.jpg
:width: 400

Guidoさんパネルと巨大Pythonぬいぐるみ
```

丸テーブルでおいしい食事を食べながら、楽しくオークションに参加します。
とはいえ、あっという間にすごい金額になるため、オークションそのものには全然参加できませんでした。

```{figure} images/auction2.jpg
:width: 400

オークションの食事風景
```

オークションで全ての商品が終わった後に会場から「ペン！！」という声があがりました。
これは、商品を写すモニターに写り込んだペンをオークションしよう、という悪乗りです。
ペンのオークションが始まり300ドルになった頃に「他にこの○○のステッカーを付けます」みたいにMCがおまけを追加していたら、会場中の人がどんどん自分のコミュニティのステッカーを置き始めました。
さらに悪乗りした人が現金を置いて、さらに各国の参加者がさまざまなお金を置き始めて、カオスな状態になりました。
最終的にバッグが提供され、そのバッグにペンと全てのグッズを入れて落札者に渡され、オークションは終わりました。

```{figure} images/auction3.jpg
:width: 400

ペンと雑多なグッズと現金
```

こうしてカンファレンス2日目は21時40分くらいに終わりましたが、このあと私はライトニングトークの資料作成があるため、ホテルに戻った後に夜なべしてスライドを作成していました。

````{admonition} PyCon での PSFメンバーランチについて

一般社団法人PyCon JP Association理事の吉田（[@koedoyoshida](https://twitter.com/koedoyoshida/)）です。
このコラムではPSFメンバーランチについて紹介します。

PSFメンバーランチとは、PyCon US中のどこか一日カンファレンスランチの時間帯で、Python Software Foundation（PSF）のさまざまな地域のメンバーが集まってランチするサブイベントです。

例年ここではランチを取りながら、PSFのスタッフとボードメンバーから昨年の活動や会計に関する報告がされ、他のPSFメンバーと交流します。今年もPython生みの親のGuido van Rossum氏が参加していました。
今年も主にPSFのExecutive DirectorであるDeb Nicholson氏から説明がありました。

活動や会計報告と言うだけでは無味乾燥に思われるかも知れませんが、今年もプレゼンテーションに加え、フルカラーで30ページ弱の報告資料冊子が用意されており、大変分かりやすくなっていました。

この冊子にも一日目のPyCon USのオープニング記事で書かれたPyCon JP 2024のライトニングトークの出番待ち写真が使われていたのを発見し、とても嬉しかったです。

本題の会計報告についです。
PSFの収入の主要な物としては、年間スポンサーおよびPyCon USなどのイベントの参加者収入となります。また、主な支出としてはPyCon USの開催費用や遠方などからの参加者に対する費用の援助であるTravel Grant、スタッフ人件費、またPython開発者の保険料の支払いなどがあります。

今年の報告および報告資料を読んで、特に大きな変化が見られたのは資産状況の推移とその背景です。昨年の総資産がおよそ545万ドルだったのに対し、今年は約426万ドルと、約120万ドル（およそ2割）減少していました。今年の資料だけではこの原因は明確ではありませんでしたが、手持ちの昨年の資料と比較してみたところ、「Packaging Work Group/Infrastructure/Other」に関連する支出が、合計で100万ドルほど増加しているように見受けられ、これが主な要因と考えられました。

```{figure} images/psfbooklet3.jpg
:width: 400

今年の冊子のGrowrh of AssetsおよびProgram Service Expensesのなどのページ
```

こちらについて、吉田でその場で質問して再確認したところ、今年の報告資料にもあるPSF PyPI Safety & Securityの活動に大きく費用がかかっているとのことでした。これについては今回は特に重点的に投資しているとのことでした。

```{figure} images/psfbooklet4.jpg
:width: 400

PSF PyPI Safety & Security
```

PyPIのセキュリティを保つための活動については後日のKeynoteでも取り上げられており、PSFがこの部分に注力している事が良く分かりました。

PSFメンバーランチは、PSFメンバーが事前登録のうえ参加できる貴重なイベントで、その場で質問も可能です。
PSFメンバーになると、理事選挙の投票権なども得られます。月に5時間程度、PythonやPyConに継続的に関わっているなどの条件を満たせば、誰でもメンバー登録が可能です。該当する方や興味のある方は、ぜひ以下のページで詳細をご確認ください。

* [Become a Member of the PSF](https://www.python.org/psf/membership/)

````
