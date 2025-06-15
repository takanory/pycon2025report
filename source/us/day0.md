# カンファレンス前日まで

筆者はカナダのトロント経由で、カンファレンス2日前の5月14日(水)の深夜にピッツバーグに到着しました。

今回のホテルは会場すぐ近くのThe Westin Pittsburghです。
PyCon JP Associationでも一緒に理事をやっている吉田さん（[@koedoyoshida](https://twitter.com/koedoyoshida/)）と同室でした。

## Opening Reception

カンファレンス前日に会場の[David L. Lawrence Convention Center](https://www.pittsburghcc.com/)を訪れ、受付で名札を受け取ります。
名札にはリボンを付けてデコります。私はスピーカーなので「SPEAKER」というリボンを付けました！！

```{figure} images/ribbon.jpg
:width: 200

名札をデコるリボン
```

```{figure} images/my-badge.jpg
:width: 200

さまざまなリボンでデコられた名札
```

その後はOpening Receptionというイベントで、ビールを片手に企業ブースを回ります。
今年もさまざまな[スポンサー](https://us.pycon.org/2025/sponsorship/sponsors/)が企業ブースを展開しています。

```{figure} images/booth.jpg
:width: 400

たくさんの企業ブース
```

アジアのPythonコミュニティを支える組織、Python Asia Organizationもコミュニティとしてブースを出していました。
日本から参加した寺田さんもそのメンバーの一人ですが、営業担当として色々な人に「ブースに来てね」と精力的に声をかけていました。
Guidoさんに声かけしているところを見かけたので写真を撮っておきました。
PyCon USに来るとGuidoさんは全然普通にいるんですよね。

```{figure} images/terada-and-guido.jpg
:width: 200

Guidoさん（手前）にPython Asia Organizationブースを宣伝する寺田さん
```

この日の夜はスポンサー企業である[Anaconda](https://www.anaconda.com/)のハッピーアワーがあったので参加してみました。
会場は[Social House 7](https://www.socialhouse7.com/)というアジア料理のお店です。
看板に「七」の漢字が書いてあるので「あれはsevenって意味の漢字なんだよ」という説明をしたりしてました。

```{figure} images/seven.jpg
:width: 400

看板に「七」の文字
```

```{admonition} コラム：WebAssembly Summit
橘祐一郎（[@whitphx](https://github.com/whitphx)）です。今年初めてPyCon USに参加しました。

トークの行われる3日間の前に、チュートリアルなどのための期間が2日間あり、Summitというタイプのイベントもそこで行われます。ここではカンファレンスのメイン日程でやるには若干ニッチだけど重要なテーマに関して、興味ある人が集まって発表や議論を行います。
私はその中の一つ、WebAssembly Summitに参加しました。
若干背伸び気味の参加でしたが、自分と同じような関心を持っている方と繋がれたりと実りのある体験でした。

自分はもともと[Pyodide](https://pyodide.org/)（WebAssembly向けにビルドされブラウザやNodeJSで動くCPython）を利用したOSSをいくつか開発しています。
そんな中でPyCon USのイベント情報を眺めていたら"WebAssembly Summit"の名前が目に入り、その存在を知りました。
イベント情報の説明文には初心者向けではない旨、Pythonに限らずC,JS,Wasm,コンパイラなどに関する知識があればより楽しめる旨が注意書きされていて気後れしましたが、気になっているのに参加しないのも後悔するだろうと思い申し込みました。

希望者には発表の機会が設けられます。
せっかくの初参加なので、自己紹介を兼ねて、発表を申し込みました。
自分の開発している、Pythonだけで書けてサーバサイド不要で動作するWeb UIフレームワーク[Stlite](https://github.com/whitphx/stlite)と[Gradio-Lite](https://www.gradio.app/guides/gradio-lite)の紹介と、そこから派生して最近取り組み始めている、ブラウザで実行する機械学習（WebML）関連の話題などを軽く話すトークです。

<!-- いざ部屋に行ってみると、参加者は10名ほどでした。
午前中は希望者が発表する時間で、午後にそれを踏まえて自由に議論を膨らませるという構成でした。 -->

他の方の発表は、注意書きの通り技術的に尖った発表が多かったです。
例えば、Pyodideのアプローチ（CPythonインタプリタをWasm向けにビルドする）の代わりに、より実行時オーバーヘッドを減らすためにPythonのバイトコードを直接Wasmにコンパイルするという研究が紹介されました。発表者は大学で研究されている方で、アカデミックな学会の雰囲気でした。
また当然の如くPyodideの作者の方も発表していて、直近の進捗や今後の展望について話されていました。

自分の発表はWasm Pythonそのものに関連する技術に触れるものではないためどう捉えられるか不安でしたが、司会の方が親切に進行してくれました。
また、この場には Anaconda の [PyScript](https://pyscript.net/) プロジェクトの方が多く参加していて、その中の1人がかなり興味を持って話しかけてくれました。
その方は PyScript の文脈で、ツールチェインやAIなどを含めたアプリケーションの拡充などに関心があるようで、自分の興味・発表内容ともかなり親和的でした。

発表後の議論タイム（unconference）ではWasm周辺の技術的な話題が中心で、正直自分はほとんど聞くだけでしたが、
小さいテーブルの方で上記の PyScript の方と議論を深められたのが収穫でした。

総じて、Summitの名の通りかなり少数精鋭の感があるイベントで若干場違いな気持ちを勝手に感じてしまったものの、場の雰囲気は包摂的でそれなりに受け入れてもらえたと思います。
自分と重なる興味関心のある方とも繋がれました。
勇気を出して参加してみて良かったと思います。
```
