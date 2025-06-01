# Day 3

## Lightning Talk

* ビデオ：<https://www.youtube.com/watch?v=lXngPPRaqGg>

## Keynote: The Marshall Project


* https://us.pycon.org/2025/about/keynote-speakers/#the-marshal-project
* https://www.themarshallproject.org/

* 2名のキーノートと1名のモデレーター
* それぞれのバックグラウンドを紹介
* Marshall Projectのミッション

## PSF - Update from our Security Engineers

* 2FA対応
* メールが生きているかチェック→ドメイン失って乗っ取られないように

## Poster, Job Fair, Community session

* Posterおもしろかった

## Reinventing the Wheel: A Community-Driven Roadmap for Python Packaging

* ビデオ：<https://www.youtube.com/watch?v=1Oki8vAWb1Q>
* https://us.pycon.org/2025/schedule/presentation/100/
* Jonathan Dekhtiar, Barry Warsaw 
* WheelNext
* いろんなハードウェアに対応できない
* PyTorchとかそういう系のやつが必要としてそう
* PEP772でパッケージングのガバナンス
* GPUとかのバージョンごとのwheelが作れる?

## Phantom Dependencies: is your requirements.txt haunted? - PyCon US 2025

* https://us.pycon.org/2025/schedule/presentation/14/
* ビデオ：<https://www.youtube.com/watch?v=x9K3xPmi_tg>
* Seth Michael Larson
* SBOMがでペン伝シーに対応するの?
* PEP 770 でSBOMはいる。Apr 11 にAcceptされた
* SBOMのjsonがつく
* Linuxのライブラリが入る?
* anchore/syft: CLI tool and library for generating a Software Bill of Materials from container images and filesystems https://github.com/anchore/syft
* anchore/grype: A vulnerability scanner for container images and filesystems https://github.com/anchore/grype

## Keynote: Dr. Kari L. Jordan

* https://us.pycon.org/2025/about/keynote-speakers/#dr-kari-l-jordan


## Python Steering Council

* https://us.pycon.org/2025/about/keynote-speakers/#python-steering-council
* Sttering Councilがやっていることを説明
* 3.14の新機能をいろいろ説明

## Python Software Foundation Update & Awards

* PSF Board eceltion Aug/Sep
* 2026はCalifornia
* PyLadies Awards
  * 50人ノミネート
  * 3名が現地にいないのは残念。4名が受賞
* Community Service Awards
  * Iqbalさんが受賞
* Distinguish Service Awards
  * Thomas Wouters
  * Van Lindberg
  * Ewa Jodlowska

## Closing

* PyLadies Auctuin: 67,000 USD
* キャプションがすごい

## Party

## Sprint

````{admonition} PyCon US 2025 t-strings Sprint
このコラムは清水川(@shimizukawa)がお届けします。

私は今回が **PyCon US初参加** でした。一番楽しかったのは、 "t-strings スプリント" に参加し、Python 3.14の最新の技術に触れることができました。また、参加者との交流も貴重な経験となりました。

スプリントでは、t-stringsの[PEP-750](https://peps.python.org/pep-0750)オーサーのPaul Everittさん、Dave Peckさん、青野高大さん（[@koxudaxi](https://github.com/koxudaxi)）と協力して、作業を進めました。

"t-strings"はPython 3.14から導入される新しい文法です。 t-stringsの核心は「安全な文字列処理」にあります。従来のf-stringsとの違いは、すぐに文字列にはならない点です。
```
>>> user_input = "</div><script>XSS文字列</script>"
>>> f"<div>{user_input}</div>"
"<div></div><script>XSS文字列</script></div>"
>>> t"<div>{user_input}</div>"
Template(strings=('<div>', '</div>'), interpolations=(Interpolation('</div><script>XSS文字列</script>', 'user_input', None, ''),))
```

この挙動により、ユーザー入力の即時評価リスクを排除できます。
スプリントでは、t-stringsの動作を体験できる https://t-strings.help/ サイトの手順をなぞり、ドキュメントやサイトの改善に協力しました（ [PR#18](https://github.com/t-strings/tdom/pull/18)、[PR#19](https://github.com/t-strings/tdom/pull/19)、[PR#19](https://github.com/t-strings/help/pull/19)）。

このサイトで紹介している [tdom](https://github.com/t-strings/tdom)ライブラリは、Templateオブジェクトを安全に文字列に変換する処理を担当しています。これによって、例えば以下の様に書けるようになります。


```
>>> from tdom import html
>>> user_input = "</div><script>XSS文字列</script>"
>>> str(html(t"<div>{user_input}</div>"))
'<div>&lt;/div&gt;&lt;script&gt;XSS文字列&lt;/script&gt;</div>'
```

Paul氏とは、スプリント中にt-strings以外にもSphinxの進化の可能性を議論しました。Paul氏はSphinxをより進化させたいと考えていて、「既存の拡張機能の互換性を維持しながら進化させる方法を探っている」とのことでした。

今回私は、トークセッションを持たずに参加しましたが、そのためかSprintの前日までは緊張感が少なく、いまいち乗り切れていなかったように思います。しかし、Sprintで1日どっぷりと最新技術に触れ、英語で議論を交わす時間を持てたことで、PyCon US参加が特別な体験となり、また参加したいイベントになりました。なにより、Python開発の中核にいる開発者と一緒に開発し、新たなつながりを築けたことが最大の収穫でした。Pythonコミュニティの温かさを改めて実感するPyCon US初参加となりました。

```
:width: 400px
Paul氏と記念撮影
```

````