# Chapter2 Test Smells

## この章の要約

Test Smellsには大まかに分けると3つの種類がある



1. Project Smells: プロジェクトのあり方や、メンバーの働き方に関する不吉な臭い
2. Behavior Smells: 開発者のテストに対する取り組み方についての不吉な臭い
3. Code Smells: コードの内容に関する不吉な臭い

これらは相互に関連していて、1->2->3の順に抽象度が高く、また抽象度が低い問題によって上の問題が引き起こされやすくなる。抽象度が高い問題は「何かが起きているサイン」として検知しやすいものでもあり、それが見つかったらより下位の不吉な臭いに原因を求める事ができる。逆に、下位の不吉な臭いが見つかった場合は、上位の臭いに達する前に対処するべきである。

Project Smellsは、「リソース」「納期」といった問題によって生じる。品質やスループットの低下を招く。
Behavior Smellsは、壊れやすい・遅いテストによって生じる。開発者がテストの実行をする頻度の低下を招き、「テストを上手く活かせていない」状態になる。  
Code Smellsは、テストのメンテナンス不足やテストが困難なプロダクトコードによって生じる。テストのメンテナンスコストの増加を招く。

不吉な臭いの中には、「取り除くには重すぎる」というものもある。大事なのは、その臭いに気づくことと、それによって何が引き起こされるかを知っておくことである。あらゆる不吉な臭いへの対応は、コストと利益のバランスから判断されるものである。

## 感想

この章は過去に読んでいたな・・・と思いつつ、同時に「この本は難しいな」と思った章でもあった(気がする)

結局の所は「テストをちゃんと書くこと、使うこと」「その意識を維持し続けること」が大事であり、そうでないと「自動化テストが持つ本来の価値が損なわれていく」のだな〜というように理解。  
現場レベルの観点からするとCode Smellsは気づきやすいかも知れない。それは「眼の前にあるコードの良し悪し」みたいな、物理的に現れる形の問題に近いので。他方で、Behavior Smellsになると、「ある日パッと現れる！！」というものでもなく(例えばCIの実行時間などはジワジワと肥大化する)、定期的なアセスメントのようなものが必要なのかもしれない。なまじ「テスト増えてきたね、実行時間もそりゃ多くなるよね」みたいに、「正当性」を感じやすいのがよくなさそう。注視すべきは「テストの実行頻度が落ちていないか」というところかな。それは「バランスを判断して」という原則にも適うように思った。  
さらにProjet Smellsともなると・・・これはアウトカムが「プロダクトの品質・速度」なので、より注意深い観察が必要だよなぁ。とはいえ「バグが増えた」とかは、じゃあテストちゃんと書けてた？って話になり、「そういえばCIをよくre-runさせてました」みたいになったら、そりゃ危ないねぇ(=behavior smellsを特定できた)ってな話になるのかな？



## 読み途中のメモ

* the smells in three broad categories: test code smells, automated test behaviour smells, and project smells realated to automated testing.

* The motivation for this refactoring was the identification of "bad smells" that frequently occur in object-oriented code. 

  * "If it stinks, change it."

* The authors also recommended a set of reactorings that can be applied to the tests to remove the noxious smells

* A smell is a sympton of a problem

* least two different kinds of smells

  * code smells : コードの中に見られる臭い
  * behavior smells: テストの(から得られる)成果に影響を及ぼす(ような振る舞い)

* code smells are coding-level anti-patterns

  * notice(d by them) while reading or writing test code
  * the code just doesn't look quite right or doesn't communicate its intent very clearly
  * (ツールによって記録された)Recorded Testsは、人にとって「何をしたいのか」が明白になりにくいため _Obscure Tests_ に陥りがち

* Behavior smells, by constast, are much more difficult to ignore because they causes tests to fail

  * あくまで「テスト通さなきゃマージしちゃダメ」とかの仕組みが強制されている場合には、ってことかな？

* 最近になって3つ目のsmellを見つけた: project smells

* いくつかのsmellは「取り除くには重すぎる」という理由から免れ得ないものもある。重要なことは、smellに気づき、それが何を引き起こすかを知っておくこと。

* 「どのsmellsを取り除くか」という決定は、コストと利益のバランスの上に行われる。

* とても多くの場面で、いくつかのsmellsは同時に観測することになる

  * 例えばProject smellsはいくつかの原因が横たわって生じている事の顕れ
    * behavior smells、これも突き詰めて言えばcode smellsが根本の原因だったりもする
  * 1つのレベルに集中してしまうことは簡単だが、根幹にある原因を理解すること抜きに問題を解決することは難しい

* A very effective technique for identifying the root cause is the "Five Why's"

  * why somehing is occuring
  * why each of those factors occured
  * asking why finve times is usually enouch ─ hence the name "Five Why's"

* The Project Smells

  * 「プロジェクトが何か良くない感じになってる」というsmell
  * 1つもしくは複数のcode smells / behavior smellsによって生じる
  * その反面、Project smellsは「完璧に自動化テスト(の実行による快適な状態)を実現できていない」ということに気づくための最初のヒントたりえる
  * PJは機能性・品質・リソース・コストに着目して成り立つもの、ゆえにProject smellsとはそれらの問題を網羅する
* 根本的な原因を探っていくと、大量のテストの失敗が「壊れやすいソフト _buggy software_ 」のせいではなくて「壊れやすいテスト _buggy tests_ 」によるものだと判明することもある。これは、たくさんのリソースがテストに注がれて居るにも関わらず、テストがプロダクションコードの品質を上げない例だ。
    * buggy testsは「メンテナスコストの高いテスト」という不吉な臭いをもたらし、チームの生産性を引き下げる
    * テストがしばしば修正を要したり不安定になっている場合、もしかしたら自動化テストに拘りすぎないで同じ時間をプロダクションコードの開発に宛てたり、あるいは手動テストに使ったほうが良いかも知れない。すなわち、この状況でマネージャーがすべきことは「テストを書くのを止めさせる」ことだ
  * もしくは、「開発者がテストを書かない」ことによってプロダクトコードの破壊が引き起こされているケースがある(レトロスペクティブで検知される)。タイトなスケジュールや、管理者が「テストを書くのに時間を使うな」と指示していたり、単に開発者にテストを書くだけのスキルが不足していることが原因となり得る。
    * 他に、テストをしにくい設計や、テスト環境の問題でFragile Testsが生じていることも考えられる。
    * 最後の1つは、 _Lost Tests_ のケースによるもの。テストが作成されているのにAll Tests Suiteに含まれていないというケース。
  
* The  Behavior Smells

  * コンパイル時やテスト実行時のSmell
  * よくあるのは _Fragile Tests_。1回通ったはずなのに何か壊れるやつ。根本的な原因は以下の4つに分類される
    * _Interface Sensitivity_ : テストプログラミングAPIやUIの変更によって破壊が生じるもの
    * _Behavior Sensitivity_: SUTの振る舞いに引きずられてテストの破壊が生じるもの。「変更が起きたならテストが壊れる」というのは正しい、が、それは「(対応する)局所的なテストが壊れるべき」であって、「多く、もしくはほとんどのテストが壊れる」なんて変な話
    * _Data Sensitivity_: データが変になったことで破壊が生じるもの。これは _Context Sensitivity_ の特殊系で、問題のコンテキストがdatabase(の中身)由来のもの。
    * _Context Sensitivity_: 環境の差異によって破壊が生じるもの。日時に依存しているものや、デバイス(サーバーやその他の接続デバイス)の状態に依存しているものなど
  * 最もよくある絶望の原因は、コケたテストがその理由を何も示さないこと。SUTが変更されていないのに突如コケるなど。
  * _Erratic Tests_ は、鬱陶しいし修復に時間を要する。これには以下のような原因が考えられる
    * _Interacting Tests_ は _Shared Fixture_ によって生じる。テストを独立的に動かしたり、 _Suite of Suites_ として実行することを困難にする。また、ドミノ倒し的な「他のテストもこけさせる」という自体を生じさせることも(fixtureの状態が「失敗したまま」のものを引きずる事による
    * _Test Rnu Wars_ は、_Shared Fixture_ を用いながら複数のテストが同時実行されることによる。
    * _Unrepeatable Tests_ は、最初に実行した時とその後で異なる結果をもたらす結果として、自動化テストに対して手動での介入の必要性を生じさせるかも知れない
  * その他の生産性を低下させる臭いは _Frequent Debugging_ 。
    * 自動化された単体テストはデバッガーを使うべき理由を、一部を覗いて、除去するようにすべき。なぜならコケたテストはなぜその失敗が生じたかを明確に示すべきだからだ(そうなっていれば要らないはずじゃん、的な)
  * 自動化テストの真の価値は、それを高頻度で実行することが可能になること
    * TDD実践者は数分ごとにテストを走らせるが、これは推奨されるべきで、フィードバックループを短くすることでコードにある欠陥を見つけにいくコストを減らせるから
    * _Manual Intervention_ を要するようになると、開発者はテストを実行する頻度を下げる。この態度は、コードにある全ての欠陥を発見するのにかかるコストを増大化させる。最後にテストが実行されてから今に至るまでの全ての変更が、捜査の対象となる
  * _Slow Tests_ も生産性に対して影響を与える
    * 大体30sを超えると、開発者はテストを都度実行するのをやめて”合理的な時間”に実行するようになる。休憩前とか。
      * このフィードバックの遅延が結果的に”flow"の逸失を招き、欠陥が混入してから(テストによって)発見されるまでの時間の増大化を招く
      * この臭いに対する良くあるソリューションは、事態を悪化させる・・・ _Shared Fixture_が、その他の多くの behavior smellsを誘発する

* The Code Smells

  * マーティンファウラーによって説明された「古典的」な臭い。(言い換えると、ファウラーが言った「臭い」は、ほとんどcode smellsのもの)。
  * これはテストコードを修正している時に自動化テストによって発見されるべきもの。テストのメンテナンスにはコストがかかるかもしれないが、この臭いは後に生じうるbehavior smellsの早期警戒サインとなりえる
  * _Obscure(はっきりしない) Tests_ : 色々な形があるが、共通して言えるのは「何をしたいのかわかりにくいテスト」であり、意図をよく表していないことによって(the test does not Communicate Intent)陥るものである
    * メンテナンスコストを増大させるし、もしメンテナが誤った修正をすれば壊れやすい(Buggy)テストを生むことにつながる
  * _Conditional test Logic_ : Obsucre〜に関係する。テストはシンプルで、直列的なものであるべき。複数のパスがテスト内に存在していた場合、どのケースでどれが実行されるかが分からなくなる
  * _Hard-Coded Test Data_ : いくつかの理由で、気づいたら(臭いの悪化を？)進行させていることがある。
    * 値を見つけ出して、それが他の値とどのように関連するかを推測して、SUTがどのように振る舞うと推測されたのかを理解しなければならなくなる
    * データベースを含む場合のテストを困難にさせる。Erratic Testsを(もしテストが同じキーを利用していた場合に)生じさせるし、もしくはFragile Testsを(参照している値が変更されていた場合に)生じさせる
  * _Hard-to-Test Code_ : 他のcode/behavior smellsを生じさせる原因となる。
    * これは「Fixtureの用意の仕方がわからない」「SUTの動かせない」「期待する結果を確認できない」という人には明らかな問題
    * テストコードを読んでいるときに、 _Hard-to-Test_なコードはObscure Testとして現れる
  * _Test Code Dupilcation_ : テストのメンテコストを増やす
    * 大体Obscure Testsと同時に発生するので、メンテナンスをより困難なものにする
    * テストコードを複製し、テストロジックの再利用をどのように行うかをよく考えられなかった場合に生じる
  * _Test Logic in Production_ : 「それが本当に(事故って)動作しないか」を保証する術がなくなるので、望ましくないやり方
    * = 「テストが動きました」が「プロダクトコードがちゃんと動作します」を意味しなくなるもんね的な理解
    * プロダクトコードを巨大化・複雑化させる、という点でも良くない

  