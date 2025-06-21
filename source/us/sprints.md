# スプリント

カンファレンスのあとは開発スプリントです。
スプリントとは、Python関連のオープンソースのプロジェクトに参加し、一緒に開発をするというイベントです。
PyCon US 2025のスプリントは5月19日（月）から22日（木）の4日間開催されます。筆者は1日目のみ参加しました。

スプリントの一覧は以下のページで確認できます。
CPython、mypy and mypyc、tstring、Read the Docs、PyLadiesCon Web Portalなどさまざまなプロジェクトがあります。

* [Development Sprints - PyCon US 2025](https://us.pycon.org/2025/events/dev-sprints/)

会場に行くと、ボードにどの部屋でどのプロジェクトが行われているかが書いています。
参加者はこのボードを見て参加したいプロジェクトの部屋に行きます。
たとえば「First-Time CPython Contributors（初めてのCPythonへの貢献）」はRoom 315であることがわかります。
CPythonのコアチームは隣のRoom 316で行われており、初めての人と経験者の部屋を分けるようになったんdすが、良いアイデアだと思います。

```{figure} images/sprints-board.jpg
:width: 200

スプリントの部屋割りボード
```

スプリントの各部屋には丸テーブルがあり、一緒に開発やディスカッションを進めます。
筆者はトークとライトニングトークでだいぶ疲れていたため、プロジェクトには参加せず、自分のタスクを進めていました。

```{figure} images/nishimotz-sprints.jpg
:width: 400

スプリントに参加する西本さん
```

スプリント会場の廊下ではGuidoさんとDongheeさん（Steering Councilの一人）が膝をつき合わせて会話していました。
なにの話をしているかはわかりませんが、Python開発の進め方について語っているのでしょうか。

```{figure} images/guido-donghee.jpg
:width: 400

語り合うGuidoさんとDongheeさん
```

````{admonition} First-time CPython Contributions
橘祐一郎（[@whitphx](https://github.com/whitphx)）です。
スプリントでは、First-time CPython Contributionsのテーブルに参加しました。
CPythonへの貢献を初めてやってみようというテーブルで、CPython開発者の方がその場にいて親切に導入してくれたり、議論や相談に乗ってくれます。
これがあるのはPyCon USとEuroPythonくらいではないかと思います。せっかくPyCon USに来たので飛び込んでみました。
結果的に、3.13から導入された新しいREPLに関する [issue](https://github.com/python/cpython/issues/127960) に取り組み、[PR](https://github.com/python/cpython/pull/134275)を出してマージされるところまでできました。

<!-- 当日部屋に行って、スプリントリーダーらしき人に声をかけつつまだ始まったばかりという気配のテーブルを選んで席に着くと、軽く流れを説明してくれました。
始め方に関してはドキュメントにまとまっていて、[PyCon USのブログのスプリントに関する記事](https://pycon.blogspot.com/2025/04/pyconus-sprints.html)でスプリントに関する一般的な情報をおさらいし、技術的な部分は[Python Developer’s Guide](https://devguide.python.org/getting-started/setup-building/)に従ってセットアップしていきます。

セットアップと並行して、取り組むissueを見つけるように促されました。
自分で見つけたバグや機能要望から出発するのではなく、OSSへの貢献そのものを目的にしてissueから探し始めるというのは普段やらないため新鮮でした。
CPythonリポジトリではこういう場で初心者が取り組みやすいissueに `easy` label をつけて管理しています。
しかし実際には `easy` のissueはスプリント参加者数に対して足りておらず、すぐに売り切れて取り組めるものがなくなってしまいました。同じテーブルの参加者も同様に困っており、スプリントリーダーに相談してみても、こればかりはどうしようもないという感じでした。

仕方がないので `easy` 以外のissueからできそうなものを探しました。とはいえissueは5k+個あるので、適当な条件で絞ります。
* `easy` labelのissueリストを眺めた時に（ドキュメント修正以外では）`topic-repl` labelの共起が多い印象だったので、このlabelで検索しました。3.13から入った新しいREPLは実装言語がPythonになったので、Cを書かなくても貢献できそうという見込みもありました。
* 数年経っているようなissueは除くようにアドバイスを受けました。長く残っているということは解決が難しい可能性が高いからです。
* コメント数が多いissueはすでに誰かが取り組んでいる可能性が高いので、今回の目的からは除外します。同様にassigneeがいるissueも当然除外します。 -->

スプリントに参加したら、まず取り組むissueを決めます。
CPythonリポジトリでは初心者が取り組みやすい簡単なissueに [`easy` label](https://github.com/python/cpython/issues?q=is:issue%20state:open%20label:easy)がついていて、ここから探すのが一般的です。
しかし今回は `easy` issueの数が参加者に対して全然足りておらず、空いているissueがすぐに無くなってしまったため、`easy` 以外のissueから探しました。

結局 [#127960](https://github.com/python/cpython/issues/127960) を見つけました。新しいREPLでは相対インポートの挙動が従来のものと違っているという指摘です。
自分の手元で最新のコミットでも問題を再現できることを確認し、修正点のアテをつけてから issue に自分がスプリントで取り組みたい旨の[コメント](https://github.com/python/cpython/issues/127960#issuecomment-2891721324)を残しました。

早々に関連する箇所を見つけ、Pythonコードに1行足すだけでissueの指摘事項を直せることが分かりました。

しかしその修正はなんともその場限りのものだったので、問題の根本的な原因を探って一貫性のある修正を模索してみました。するとCで書かれた部分にまで手が及び、さらに元の実装の意図と衝突する修正を導入してしまうことになりました。

このまま頑張っても手戻りのリスクが大きいと判断し、この時点でスプリントリーダーに相談しました。
すると、PyREPLのメイン実装者の[Pablo](https://github.com/pablogsal)にその場で繋いでくれました。こういうことが気軽に起きるのが現地開催のスプリントの良い点です。

Pablo に上記の懸念を伝えると、以下のような返答でした。
* issue としてはエッジケース寄りなのであまり大きな修正は労力の割に合わないだろうから無理しなくてもよく、現状を正として、ここでの議論をコメントに残しつつ issue を close するのも選択肢である。
* 一方で私が実装を頑張るならその実装方針には同意できるしレビューするのも問題ない。

私としてはせっかくなのでまず実装を頑張ってみて、どうしようもなくなったら妥協してissueに議論の過程だけ残して撤退することにし、Pabloにもその方針を伝えました。

撤退も視野に入れつつ最初の実装を終えていざdraft PRを作ったところで、テストコードで担保されている、つまり元の実装者が意図的・明示的に選択した挙動を破壊してしまうことが判明しました。ここで1日目が終わり、draft PRをそのまま寝かせていたら、後日、別のコア開発者[Łukasz](https://github.com/ambv)が議論に加わってくれて、私の実装方針を支持してくれ、当該テストコードを削除してくれました。また[Tomas](https://github.com/tomasr8)が、PyREPLのimportの挙動を変えるとautocompleteにも修正が必要である点を指摘してくれました。
これらの後押しを受けて実装とテストコードを拡充し、最終的にマージされるところまで至りました。

プログラミング言語そのもののリポジトリに自分のコードが入るは初めての経験でした。
このスプリントは、CPythonのような大きなOSSに対して何らかの貢献を始めるために、とても良い助走の機会を提供してくれたと思います。コア開発者の方々が気軽に議論に加わってサポートしてくれるため、大きなハードルを感じずに出したPRがマージされるところまでやり切れました。

<!-- CPythonリポジトリのマネジメントは技術的にも大規模プロジェクトとして洗練されていました。例えばCPythonプロジェクトでは、出したPRをマージするまでにContributor License Agreement (CLA)　へのサインが求められます。これ自体は大きめのOSSでは割と一般的な手続きかと思います。
CPythonではCLAへのサインを含む必要な手続きや実装上の作業（リリースブランチへのバックポートなど）がbotで自動化されていて、ほぼ追加の労力なしに出したPRがマージ可能な状態になりました。
特にスプリントは多くの初参加者が短期間で成果をあげないといけない特殊な状況ですが、このような自動化はそのハードルを下げるのに一役買っているでしょう。 -->

また月並みな感想ですが、最近のAIの性能向上によって、CPythonのようなプロジェクトの実装に新しく参加するハードルは下がっていると実感しました。
この時自分はCursorを使っていましたが、AIがコードリーディングの速度をかなり上げてくれました。それなりに長いCやPythonのコードを依存関係をジャンプしながら全容を把握する代わりに、AI chat に説明させることでかなり短時間でコードベースを把握して、スプリント中に実装を進められたと思います。
<!-- 一方でCPython程度に複雑なコードベースに対して、例えば上記 issue をそのままAIに投げてマージに値するコードを人間以上に早く書かせるのはまだ難しそうです。 -->
````


````{admonition} PyCon US 2025 t-strings Sprint
このコラムは清水川(@shimizukawa)がお届けします。

私は今回が **PyCon US初参加** でした。一番楽しかったのは、 "t-strings スプリント" に参加し、Python 3.14の最新の技術に触れられたことです。また、参加者との交流も貴重な経験となりました。

スプリントでは、t-stringsの[PEP-750](https://peps.python.org/pep-0750)オーサーのPaul Everittさん、Dave Peckさん、青野高大さん（[@koxudaxi](https://github.com/koxudaxi)）と協力して、作業を進めました。

"t-strings"はPython 3.14から導入される新しい文法です。 t-stringsの核心は「安全な文字列処理」にあります。従来のf-stringsとの違いは、すぐに文字列にはならない点です。
```python
>>> user_input = "</div><script>XSS文字列</script>"
>>> f"<div>{user_input}</div>"
"<div></div><script>XSS文字列</script></div>"
>>> t"<div>{user_input}</div>"
Template(strings=('<div>', '</div>'), interpolations=(Interpolation('</div><script>XSS文字列</script>', 'user_input', None, ''),))
```

この挙動により、ユーザー入力の即時評価リスクを排除できます。
スプリントでは、t-stringsの動作を体験できる <https://t-strings.help/> サイトの手順をなぞり、ドキュメントやサイトの改善に協力しました（ [PR#18](https://github.com/t-strings/tdom/pull/18)、[PR#19](https://github.com/t-strings/tdom/pull/19)、[PR#19](https://github.com/t-strings/help/pull/19)）。

このサイトで紹介している [tdom](https://github.com/t-strings/tdom)ライブラリは、Templateオブジェクトを安全に文字列に変換する処理を担当しています。これによって、例えば以下の様に書けるようになります。


```python
>>> from tdom import html
>>> user_input = "</div><script>XSS文字列</script>"
>>> str(html(t"<div>{user_input}</div>"))
'<div>&lt;/div&gt;&lt;script&gt;XSS文字列&lt;/script&gt;</div>'
```

Paul氏とは、スプリント中にt-strings以外にもSphinxの進化の可能性を議論しました。Paul氏はSphinxをより進化させたいと考えていて、「既存の拡張機能の互換性を維持しながら進化させる方法を探っている」とのことでした。

今回私は、トークセッションを持たずに参加しましたが、そのためかSprintの前日までは緊張感が少なく、いまいち乗り切れていなかったように思います。しかし、Sprintで1日どっぷりと最新技術に触れ、英語で議論を交わす時間を持てたことで、PyCon US参加が特別な体験となり、また参加したいイベントになりました。なにより、Python開発の中核にいる開発者と一緒に開発し、新たなつながりを築けたことが最大の収穫でした。Pythonコミュニティの温かさを改めて実感するPyCon US初参加となりました。

```{figure} images/pyconus2025_shimizukawa.jpg
:width: 400px
Paul氏と清水川
```

````

