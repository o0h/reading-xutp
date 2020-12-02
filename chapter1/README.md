# Chapter1 A Brief Tour

## この章の要約

本書に出てくる多くのプリンシパル、パターン、臭いについての案内となるような章(as a quick tour of the matrerial before diving into particular patterns or smells of interst.)

「自動化テストを成功に導くためのシンプルな戦略」を、次の5つの要素に分類した。

* Development Process
* Customer Tests
* Unit Tests
* Design four Testability
* Test Organization

## 感想

「Brief Tour」というタイトルの通り、この章そのものが「何かの中身」「具体的な紹介」というよりは、「この本で出てくることを網羅的・表面的に触れてみる」「頭出しする」といったところ。なので、あんまり(今の時点で)一生懸命読む・・・というより、「これからどんな話が出てくるのかな？」というワクワク感につながればOKか、という感じ。(自分のように端から通読してみよう〜という使い方をする場合には。ただ、通読するようなやり方を推奨している本でもないので、ここで「興味のあることのあらましを見つける」ようにして、好きなとこ飛ぶ〜って方が本当は正しそう)

「パターンカタログ」な本なので、ここに書いてあるとおり "If we find that we really cannnot make the minimal test strategy work on our project by using these pattenrs, we can fail back to the alternative pattens listed in the full descriptions of these pattens in the other narratives" ということで、「必要そうなものをやってみる」「行き詰まったら別の方法を試す」ための「引き出しを増やす」っていう付き合い方をしてください、って感じなのかな。

その「最終的に良い感じにやっていく」ための工程・視野を、5つの要素に分類してみた！！という。恐らく、この先に出てくる話は「この5つのうちのいずれかの視点に基づいたもの」になるはずなので、頭に入れておくと良いのかも〜。



## 読み途中のメモ

* this chapter provides an adderviated introduction to the bulk of the material in the entire book.
* (もしいずれかのパターンを採用し、ミニマルなテスト戦略が自分たちのプロジェクトに対して成功しないと気づいたら、その他の戦略を変わりに試すことが出来る)<br>I have laid our this simple strategy in five patterns
  * Development Process: How the process we use to develop the code affects our tests.
  * Customer Tests: The first tests we should write as the ultimate difinition of "what done looks like".
  * Unit Tests: The tests that help our design emerge incrementally and ensure that all our code is tested. _設計を段階的に発展させ、すべてのコードがテストされるようにするためのテストです。_
  * Design for Testability: The pattenrs that make our designeasier to test, thereby redusing the cost of test automation.
  * Test Organization: How we can organize our Test Methods and testcase Classes.
* Development Process
  * Storytest-driven developmentと unit testsを良い感じに組み合わせて使う
  * TDDを用いることで、SUTを「テストしやすいデザインにする」「ビジネスロジックのロジックの実装にに集中する」という効果が得られる
* Customoer Tests
  * 実際にカスタマーテストをするか？に関わらずとも、開発の開始前にテストを列挙することで「顧客が本当に欲しい物」を開発チームが理解するための助けになる
  * Scripted TestsやData-Driven Testsを用いて自動化できる。場合によってはRecorded Testsも活用できる
    * しかしRedorded Testsは、Fragile Testsに陥りがちなので、他のテストが構築されたら破棄され得るもの
  * これらのテストは「システムが(真に)どう使われているか」を表すように努めるべき。ただ、量が多い(長い)テストはObscure Testsを誘発するので気をつける。
  * To keep the tests simple and easy to understand, we can bypass the user interface to by performing Subcutaneous Testing against one or more Service Facades.
* Unit Tests
  * 「単体テストはどうあるべきか」みちな説明をしてんだけど、流石にこの本自体が単体テストを取り扱った本だけあって、この「Unit Tests」の項は他の項目に比べて非常にパターンや用語への言及が多い！
* Design for Testability
  * Automated testing is much simpler if we adopt a Layered Architecture
* Test Organization
  * テストクラスにメソッドが増えすぎてきたら、クラスの分割を考える。テストの必要性やフィクスチャを軸に分ける
    * => Testcase Class per Feature
    * => Testcase Class per Fixture

