# カンファレンス2日目

カンファレンス2日目です。今日も会場での朝食からスタート！！

## ライトニングトーク

2日朝のライトニングトークからはEric Matthes氏による[django-simple-deploy](https://django-simple-deploy.readthedocs.io/en/latest/)を紹介します。
django-simple-deployはDjangoのプロジェクトを各種プラットフォームに簡単にデプロイできるライブラリです。
現在はFly.io、Platform.shとHerokuに対応しており、実際にデプロイするデモを行いながらトークを進め、今後さらに対応プラットフォームを増やしたいので協力して欲しいという話をしていました。

```{figure} images/lt-eric.jpg
:width: 400

Eric Matthes氏によるライトニングトーク
```

## D&I Panel

* ビデオ：<https://www.youtube.com/watch?v=SQAX4P59u8w>
* https://us.pycon.org/2025/about/keynote-speakers/#diversity-and-inclusion-panel

## Keynote: Linn Root

* ビデオ：<https://www.youtube.com/watch?v=Bglsof9b23k>
* https://us.pycon.org/2025/about/keynote-speakers/#lynn-root

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

* https://us.pycon.org/2025/schedule/presentation/27/
* ビデオ：<https://www.youtube.com/watch?v=np-xKVMIKcY>
* https://github.com/MarieRoald/PyConUS25

## ライトニングトークに申し込み

ライトニングトークはカンファレンス中に4回（1日目夕、2日目朝、夕、3日目朝）開催されます。
2日目夕方のライトニングトークに日本から来ていたshimizukawaさんとwhitphxさんが落ちた（10/58という狭き門）という話を聞いて、申し込みが電子化されたメリットでもありデメリットでもあるなと感じました。
記念受験として出してみるかーと思い、3日目朝のライトニングトークに申し込みました。
タイトルと簡単な概要文を書いて申し込みます。
この時点で発表のアイデアはあるけどスライドはありません。
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
ペンのオークションが始まり300ドルになった頃に「他にこの○○のステッカーを付けます」みたいにしていたら、色んな人がどんどん自分のコミュニティのステッカーを置き始めました。
さらに悪乗りした人が現金を置いて、さらに各国の参加者がさまざまなお金を置き始めて、カオスな状態になりました。
最終的にバッグが提供され、そのバッグに全てを入れてオークションは終わりました。

```{figure} images/auction3.jpg
:width: 400

ペンと雑多なグッズと現金
```

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
PSFメンバーになると、理事選挙の投票権なども得られます。

月に5時間程度、PythonやPyConに継続的に関わっているなどの条件を満たせば、誰でもメンバー登録が可能です。
該当する方や興味のある方は、ぜひ以下のページで詳細をご確認ください。

* [Become a Member of the PSF](https://www.python.org/psf/membership/)

````
