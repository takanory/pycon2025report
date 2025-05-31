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

現場のコードでは `typing.Any` の多用、安易な `# type: ignore`、旧記法のまま残る `typing.List` などが原因で型品質が下がるケースが少なくありません。登壇では、こうした問題を大きなコストなしで改善する方法をいくつか紹介しました。代表例は次のとおりです。

* **最新機能を `typing_extensions` で先取り**  
  `TypeIs` など Python 3.13 以降の型機能を旧バージョンでも利用し、ランタイムを変えずに静的解析の精度を高めます。
* **Ruff + pyupgrade による自動リライト**  
  旧式のコレクション型(`typing.List`, `typing.Dict`)や他の古い記法を現行記法へ統一し、レビュー負荷を抑えつつコードの一貫性を保ちます。
* **限定的な `# type: ignore[...]` の採用**  
  無視するエラーコードを明示しておくことで、予期せぬ型エラーを検知できなくなる事態を防ぎます。

これらの工夫により、型ヒントを陳腐化させずに運用し続けることが可能になります。継続的な利用がプロダクションや OSS で一般化すれば、ライブラリ側の型対応やドキュメント整備も加速し、エコシステム全体で型システムがさらに促進・向上していくと考えています。

私の見方では、Python が長く選ばれてきた理由の一つは、コミュニティが機能と知見を段階的に積み上げてきた点にあります。型ヒントの運用も同じく、現場での継続的な改善が広がることで、より良い型システムが育っていくと期待しています。

```{figure} images/pyconus2025_talk_koudai.jpg
:width: 400px

登壇中の様子
```


````