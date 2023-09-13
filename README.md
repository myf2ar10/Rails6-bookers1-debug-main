20230913
1342
/Rails6-bookers1-debug-main/app/views/books/index.html.erb
(book.id)追加
/Rails6-bookers1-debug-main/app/views/books/_form.html.erb
確認
/Rails6-bookers1-debug-main/app/views/books/index.html.erb
, book: @book追加

/Rails6-bookers1-debug-main/app/views/books/_form.html.erb
<% else %>追加

/Rails6-bookers1-debug-main/db/schema.rb
t.text "title"追加

rails db:migrateする

消える

20230912
2130
/Rails6-bookers1-debug-main/config/routes.rb
root to: 'homes#top'追加。

/Rails6-bookers1-debug-main/app/controllers/homes_controller.rb
Homes追加

メンター高野氏より
yarn add @babel/plugin-proposal-private-methods
「最近ブートストラップのエラーが多いから…」とのこと。

/Rails6-bookers1-debug-main/app/views/homes/top.html.erb
, books_path 追加

2300
/Rails6-bookers1-debug-main/app/views/books/index.html.erb
要改善
*****
取り組み方
このBookers1は未完成です。
バグを見つけ、エラーをご自身で解決していただきます。
修正し終えたらRSpecテストを実行し、項目全てエラーが起きないか確認しましょう。

※問題zipでは、既にspecフォルダが入った状態になっています。

つまずいてしまったりわからないときは、下記のヒントを参考に進めてください。

ヒント
<!--サーバー起動時-->
<!--1. You’re on Rails!が表示されてしまう-->
<!--You’re on Rails!が表示される原因はrootの指定がされていないためです。-->
<!--routes.rbに指定しましょう。-->

<!--homes/top-->
<!--2. LoadError-->
<!--routes.rbでrootの指定をしたhomes_controller.rbを読み込もうとしているのですが、-->
<!--読み込めずにエラーが出ています。-->


<!--3. startのリンクをクリックしても反応しない-->
<!--startのリンクであるtop.html.erbのlink_toの記述を確認してみましょう。-->


<!--books/index-->
<!--4. NameError undefined local variable or method `book'-->
<!--render先である_form.html.erbでbookが未定義になっています。-->
<!--books/index.html.erbのrenderの部分を確認してみましょう。-->


5. NoMethodError undefined method 'title'
titleがundefined methodとエラーが出ているため、schema.rbを確認してみましょう。


6. 空白で投稿するとエラーが出る
eachはメソッドであるため未定義であるというわけではありません。
eachの前である@booksが未定義になっています。
books_controller.rbを確認してみましょう。


7. 5の解決後、再度一覧画面を表示するとUrlGenerationError
エラー文に、No route matches {...}, missing required keys: [:id]と書かれています。
urlにidを要求しているのに渡せていない状況になりますのでlink_toを確認しましょう。


books/edit
8. 編集フォームのupdateボタンが発火しない
edit.html.erbのフォーム近辺に余計な記述がないかを確認しましょう。


9. 投稿の編集が行えない
updateメソッドはsaveメソッドと違い、「何をどう更新するか」を指定するために、 @book.update(...)と、後ろに引数が必要になります。
books_controller.rbを確認してみましょう。

*****

# README

This README would normally document whatever steps are necessary to get the
application up and running.

Things you may want to cover:

* Ruby version

* System dependencies

* Configuration

* Database creation

* Database initialization

* How to run the test suite

* Services (job queues, cache servers, search engines, etc.)

* Deployment instructions

* ...
