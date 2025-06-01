# Day 2

## 朝食

## LT

* django-simple-deploy: Eric Matteusさん。manage.pyコマンドでデプロイできる

## D&I Panel

* ビデオ：<https://www.youtube.com/watch?v=SQAX4P59u8w>
* https://us.pycon.org/2025/about/keynote-speakers/#diversity-and-inclusion-panel

## Keynote: Linn Root

* ビデオ：<https://www.youtube.com/watch?v=Bglsof9b23k>
* https://us.pycon.org/2025/about/keynote-speakers/#lynn-root

## Why `len('😶‍🌫️') == 4` and other weird things you should know about strings in Python 

* https://us.pycon.org/2025/schedule/presentation/27/
* ビデオ：<https://www.youtube.com/watch?v=np-xKVMIKcY>
* https://github.com/MarieRoald/PyConUS25

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


````{admonition} PyCon での PSFメンバーランチについて

一般社団法人PyCon JP Association理事の吉田（[@koedoyoshida](https://twitter.com/koedoyoshida/)）です。
このコラムではPSFメンバーランチについて紹介します。

PSFメンバーランチとは、PyCon US中のどこか一日カンファレンスランチの時間帯で、Python Software Foundation（PSF）のさまざまな地域のメンバーが集まってランチするサブイベントです。

例年ここではランチを取りながら、PSFのスタッフとボードメンバーから昨年の活動や会計に関する報告がされ、他のPSFメンバーと交流します。今年もPython生みの親のGuido van Rossum氏が参加していました。
今年も主にPSFのExecutive DirectorであるDeb Nicholson氏から説明がありました。

活動や会計報告と言うだけでは無味乾燥に思われるかも知れませんが、今年もプレゼンテーションに加え、フルカラーで30ページ弱の報告資料冊子が用意されており、大変分かりやすくなっていました。

```{figure} images/psfbooklet1.jpg
:width: 400

PSFの活動報告の冊子
```

この冊子にはPyCon JP 2024で撮影された写真が使われており、見知ったメンバーや発表者の方々が掲載されていたことは意外な驚きと嬉しさがありました。この写真はPyCon USのオープニングでも短時間ですが、使われていました。これも大変嬉しかったです。

```{figure} images/psfbooklet2.jpg
:width: 400

PyCon JP 2024で撮影された写真のあるページ
```

PyCon JP で撮影された写真についてはクリエイティブコモンズライセンスで公開しています。
* [PyCon JP Association ライセンスについて](https://www.pycon.jp/committee/license.html)


本題の会計報告についです。
PSFの収入の主要な物としては、年間スポンサーおよびPyCon USなどのイベントの参加者収入となります。また、主な支出としてはPyCon USの開催費用や遠方などからの参加者に対する費用の援助であるTravel Grant、スタッフ人件費、またPython開発者の保険料の支払いなどがあります。今年の報告および報告資料を読んで大きく変化のあった点は資産状況(Growrh of Assets)の変化とその原因です。昨年の全体資産から今年の全体資産でおよそ$5,454->$4,256と$1000前後、2割近く落ちていました。(単位 $ in thousands)。今年の資料だけではその原因は分かりにくいのですが、昨年のPSFメンバーランチで配られた活動報告冊子の同様の資料について、私の手持ちで記録を残していたので、その場でそれと比較したところ、その原因となっていると思われる大きな支出(Program Service Expenses)の変化としてPackaging Work Group/Infrastructure/Otherの支出が相当して$1000程度相当増加しているように見えました。

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

PSFメンバーランチはPSFのメンバーであれば、PyCon USの開催の少し前に登録案内が来て、それに登録すれば、無料で参加することができます。

PSFメンバーランチはその場で質問なども出来る貴重な機会です。
また、例年の冊子や資料と比較することで寄り深く状況を把握することができます。

PSFのメンバーにはいくつかの種類があります。私は投票権のあるマネージングメンバー(Managing Members)として登録しています。
マネージングメンバーになるには、月に5時間程度PythonやPyConについて継続して活動している必要があります。
PSFメンバーを通じて、ボードメンバーの投票などPSFの活動に関わることが出来ます。
条件を満たしている方、また興味のある方は下記のページから詳細を確認してみてはいかがでしょうか？

* [Become a Member of the PSF](https://www.python.org/psf/membership/)

````