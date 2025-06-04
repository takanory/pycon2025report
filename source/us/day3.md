# カンファレンス3日目

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

## ポスター、ジョブフェア、コミュニティーショーケース

3日目の午前中はトークセッションはなく、ポスターセッションとジョブフェア、コミュニティーショーケースのみとなります。
ポスターセッションはボードにA0程度のサイズのポスターを掲示し、その前でディスカッションなどを行う発表形式です。
ジョブフェアは求人をしている企業がブースを出し、仕事を探している参加者が直接企業の担当者と会話ができるという場です。

筆者もポスターセッションを見て回っていくつか質問やディスカッションをしてきました。
「色のセオリー」についてのポスターでは、データ可視化ツールのより見やすい色についての発表がありました。
各ツールのデフォルトの色はおすすめではないということで、ぜひ次に発表する機会があれば、おすすめのカラーテーマを教えて欲しい、もしくはテーマを作って共有してほしいという話をしました。

```{figure} images/poster1.jpg
:width: 400

データ可視化の色のセオリーについてのポスター
```

CrossHairのポスターでは、コードを自動的に解析してテストをしてくれるライブラリ[CrossHair](https://github.com/pschanely/CrossHair)の紹介をしていました。
PurePythonしか対象にできないため、制限があるという話でした。
ただし、大きなプロダクトだったとしても、PurePythonで書かれている部分に絞って適用することは可能だそうです。

```{figure} images/poster2.jpg
:width: 400

CrossHariのポスター
```

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

PSFから最新の情報とアワードの表彰がありました。
PSFの理事の選挙が8月か9月に開催されるとのことです。
PyCon USの次の開催地はカリフォルニアの

PyLadiesアワードでは50名がノミネートされ4名が受賞しました。
ただ、そのうち3名は現地にいないのが残念でした。
PSFのCommunity Service AwardsではPython Asia Organizationの創始者でもあるIqbalさんが受賞していました。
Distinguish Service Awardsでは長年Pythonコミュニティで大きな貢献をしてきたThomas Wouters氏、Van Lindberg氏、Ewa Jodlowska氏が受賞していました。
PSFのExecutive Directorを長年勤めていたEwa氏の受賞の時には、会場からひときわ大きな拍手が送られていました。

## Closing

* PyLadies Auctuin: 67,000 USD
* キャプションがすごい

## Party
