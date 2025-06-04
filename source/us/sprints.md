# Sprint

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
スプリントでは、t-stringsの動作を体験できる https://t-strings.help/ サイトの手順をなぞり、ドキュメントやサイトの改善に協力しました（ [PR#18](https://github.com/t-strings/tdom/pull/18)、[PR#19](https://github.com/t-strings/tdom/pull/19)、[PR#19](https://github.com/t-strings/help/pull/19)）。

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