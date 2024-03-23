# inside-estimator  

**[https://github.com/izumi4632/docs_for_friends/blob/master/如月くんに捧ぐ開発案.md] のコピー**

# この文書は何

如月くんに提案するアイデアです。  
自然言語処理と企業研究というところで考えました。  
人間とか企業とか中身の見えないものに手を突っ込みたいですよね。  
反転工学ならぬ反転人文学って感じです。

# 概要

- 人格の中に直接は測れない何かステータスのような内部データがあるとする。
- その内部データの値に応じて変わる確率に応じた結果が発生するとする。
- このとき、現実にある結果から内部データを確率的に測定する。
- 何にでも使える部品として作りたい。

# どのように役に立つか

- 例えば企業の中には情報感度という内部データがあるとする。
- 情報感度が高い企業から順にアーリーアダプター的に情報にアクセスし言及するとする。
- 企業の情報感度を推定することで企業研究の一助になる。
- 情報感度が高い企業を見つけるとその企業から質の良い情報を得ることができる。

# どのように実現するか

- 先に「この結果は内部データが平均だろう」という結果を幾つか事前に用意しておく。これをキャリブレータ（標準試薬）と呼ぶ。
  - 情報感度の例であれば「AIについて◯年◯月から言及を始めた企業が平均的な情報感度だろう」とか。
    - それを知っていてすぐに言及しないことが少ないほど良い。
- キャリブレータについて関連している人格の内部データを推定する。
  - 情報感度の例であればどこかの時点でAIについて言及していることが確認された企業。
- キャリブレータで内部データを推定された集合をプロトタイプ（原器）と呼ぶ。
- プロトタイプと測定したい人格とで共通している結果について、プロトタイプからその内部データとの関連を推定する。
  - 情報感度の例で言えば、プロトタイプの一部（多いほど良い）と測定したい企業がどちらも言及している情報を使う。
- 得られた関連から測定対象の人格の内部データを推測する。
- 測定された人格はプロトタイプの中に、結果はキャリブレータに追加で格納され次回以降使うことができる。

# 実際使うとなると

測定部分はまあぼくが出すので良くて、自然言語の処理がかなり大変になる想定。  
ざっと思いつく限りで

- 言及に関する情報を取得して
  - （ここは別モジュール？）
- IPA辞書引っ張ってきて単語分割して名詞だけ取り出して保存して
- キャリブレータとの成否を判定して
- 測定部分に投げて

くらいはありそう。
