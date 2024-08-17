# PHP App ① レビュー

## 全般

### 以下のaタグのリンクを押下した際にedit.phpの$_GETにどんな値が格納されるか説明してください。

```html
<a href="edit.php?todo_id=123&todo_content=焼肉">更新</a>
```

### 以下のフォームの送信ボタンを押下した際にstore.phpの$_POSTにどんな値が格納されるか説明してください。

```html
<form action="store.php" method="post">
    <input type="text" name="id" value="123">
		<textarea　name="content">焼肉</textarea>
    <button type="submit">送信</button>
</form>
```
id=123とcontent=焼肉が入ってる
作ったやつはauto incrementで自動でIDが付くからID自体が存在しない（new.php）
中身的にも入ってない。SQLで自動で管理する際にDB上だけで、順番で付いてる。

### `require_once()` は何のために記述しているか説明してください。
引数に入ってるファイル名を参照して読み込みを行わせるために記述している。
参照元に記述されている関数を使用するため。

### `savePostedData($post)`は何をしているか説明してください。

### `header('location: ./index.php')`は何をしているか説明してください。
header関数を使って特定のページ、
今回でいうindex.phpにリダイレクトするためにlocation ヘッダーを使用している。

### `getRefererPath()`は何をしているか説明してください。

### `connectPdo()` の返り値は何か、またこの記述は何をするための記述か説明してください。
DBへログインするための、接続情報、IDとパスワード
DBへログインするためのもの。

### `try catch`とは何か説明してください。
tryで動作(今回の場合は接続)を試みて、失敗した場合にcatchで受ける(今回はエラーメッセージを出力してる)もの。

### Pdoクラスをインスタンス化する際に`try catch`が必要な理由を説明してください。
例外処理(PDOException)を受け取る為にcatchを使う必要がある。
今回は受け取った内容($e)を文字列で返してもらうためにPDOExeceptionのgetMessageメソッドを使っている。

## 新規作成

### `createTodoData($post)`は何をしているか説明してください。
新規作成ページで作成ボタンを押した時のデータの箱の名前が$postであり、
受け取った$postの中に入っている欲しい情報を召喚するため、
今回は['content']を付けてる。

## 一覧

### `getTodoList()`の返り値について説明してください。
SQL文で実行されたdeleted_atに時間が入っていないデータを、
PDOstatementのメソッドであるfetchAllで全取得したものを返り値として返している。

### `<?= ?>`は何の省略形か説明してください。
echoの省略形。
これは
<?php
function(){
  ここに記載する場合は普通にechoでいいのだろうか。
  この書き方はしないでくれとの事だが、知識的な質問である。
}
?>
## 更新

### `getSelectedTodo($_GET['id'])`の返り値は何か、またなぜ`$_GET['id']` を引数に渡すのか説明してください。

### `updateTodoData($post)`は何をしているか説明してください。

## 削除

### `deleteTodoData($id)`は何をしているか説明してください。

### `deleted_at`を現在時刻で更新すると一覧画面からToDoが非表示になる理由を説明してください。

### 今回のように実際のデータを削除せずに非表示にすることで削除されたように扱うことを〇〇削除というか。

### 実際にデータを削除することを〇〇削除というか。

### 前問のそれぞれの削除のメリット・デメリットについて説明してください。
