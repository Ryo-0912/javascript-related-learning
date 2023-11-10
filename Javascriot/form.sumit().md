htmlで記述されたformタグを送信する際に、formタグ内に、```type=submit```を記述していると、そのボタンをクリックした時に、form内容が送信されてしまう。

ボタンをクリックした時に、ワンクッション処理を行った上で、formデータを送信したいときは次のように実装すると解決する。

1. typeをsubmitからbuttonに変更 => 保存するをクリックしてもformデータがすぐに送信されなくなる。
```
<form action="{{ route('schools.zukan.store') }}" id="uploadForm" method="POST" enctype="multipart/form-data">
  @csrf

  略

  <button class="btn btn-primary" type="button" id="videoSubmit">保存する</button>
</form>
```

2. Javascript側でformタグの内容を取得し、送信する。

```
const form = document.getElementById("uploadForm");
form.submit();
```
このような記述をすることで、javascriptの処理で処理を挟んだ上でformの内容を送信することができる。
