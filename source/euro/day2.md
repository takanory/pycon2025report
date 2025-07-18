# Day 2

## Keynote: Brett Cannon: Why it took 4 years to get a lock files spec

* https://opensource.snarky.ca/Talks/2025/EuroPython/Slides

各パッケージのファイル構成について説明

requirements.txt以外にpoetry.lock, pdm.lock, uv.lockがあるのかー

pylock.tomlという仕様ができた

https://packaging.python.org/en/latest/specifications/pylock-toml/

* pylock.tomlの構造について説明
* ファイルレベルの説明

### なぜ4年かかったのか

* 2019にrequirements.txt v2について 106ポスト
* 2020に43ポスト
* 2021 PEP 665 https://peps.python.org/pep-0665/
* 2022 PEP 665 rejected
* 2023 54 posts
* 2024 PEP 751 https://peps.python.org/pep-0751/

## A new safe external debugger interface for CPython

* https://ep2025.europython.eu/session/a-new-safe-external-debugger-interface-for-cpython
* MRIで検査を受けた?
* PythonのMRIはこんな感じ(画像)
* https://peps.python.org/pep-0768/

```
$ readelf -h python
```

## Building a new tail-calling interpreter for Python

* https://ep2025.europython.eu/session/building-a-new-tail-calling-interpreter-for-python

実際に実行しているプロセスにアクセスして処理を止めることができるデモ

PYTHON_DISABLE_REMOTE_DEBUG / -X disable-remote-debug

* Future

## Building a new tail-calling interpreter for Python

* https://ep2025.europython.eu/session/building-a-new-tail-calling-interpreter-for-python

* パフォーマンスを見るところでベンチマークを見るとinterpreterが30%と多い
* interpreterはbutecodeを実行するところ
* swtich caseだとジャンプで遅くなる場合がある。今は違う実装になっている。dispatchテーブルを使って飛ぶ
* The Cake is a lie https://en.wikipedia.org/wiki/The_cake_is_a_lie
* 多少速くなった

## Performance improvements in 3.14 and maybe 3.15

* https://ep2025.europython.eu/session/performance-improvements-in-3-14-and-maybe-3-15
* 高速化に銀の弾丸はない
* Top-of-stack Caching→3.15で入るっぽい?
* c = a + bは5回読み込み4回書き込み
* キャッシュがあると2回読み込み、1回書き込みになる
* デモを実行して高速化していることを確認
* Python 3.6以降のデータの持ち方について説明
* リファレンスカウントの処理を軽量化
* Faster cyclic garbage collection

## Pydantic, Everywhere, All at Once

https://ep2025.europython.eu/session/pydantic-everywhere-all-at-once

* ベーグルを注文する例で伝える

## Behind the Scenes: PSF Infrastructure and How You Can Contribute

* https://ep2025.europython.eu/session/behind-the-scenes-psf-infrastructure-and-how-you-can-contribute
* 前半はPSFの紹介
* Ee DurbinがDirector of Infrastructure
* 内部でCabotageってのを使っている? https://github.com/cabotage/cabotage-app

## Keynote: Behind the scenes of FastAPI and friends for developers and builders

* https://ep2025.europython.eu/session/behind-the-scenes-of-fastapi-and-friends-for-developers-and-builders
* FastAPIの紹介。さまざまなところで使われている。
* 学校をドロップアウト
* Couseraとかで勉強した
* 「Solve a problem」
* メンテナーじゃなくてユーザーのために最適化する
  * **kwargsはだめ
* 同じ名前を異なるものにつけない
* よいドキュメントを書く

## Social Event

* いろいろ話した
