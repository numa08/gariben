!SLIDE

## ScalaとIO

!SLIDE

## ScalaとIO

 - InputStreamとか
 - OutputStreamとかあの変の話
 - IOモナド？知らない子ですね...

!SLIDE

## ストリームという考え

 - UNIX的な考え方
 - 入出力を抽象化
 - 標準入出力、ネットワーク、ファイル読み書き
 - その辺を切り分けずに実装できる

!SLIDE

## その結果・・・

!SLIDE

## その結果

 - 終わりのない`try-catch`
 - xxReaderとかInputStreamReaderとかが登場しまくる
     - 適当な変数名のネタが切れる
 - ネストしたwhile文

!SLIDE

## ぶっちゃけさ・・・
 
 - 冗長化するコード
 - 「お約束」「おまじない」の繰り返し
 - 辛い

!SLIDE

## 簡略化された標準入力


```scala
readLine
readInt
readBoolean
readShort
readLong
readDouble
```

!SLIDE

## 簡略化された標準入力


```scala
readLine //標準入力から1行
/*標準入力から読み込んで、それぞれの型に変換
  変換できない場合は実行時例外*/
readInt
readBoolean
readShort
readLong
readDouble
```


!SLIDE

##　テキストの読み込み

概ね`scala.io.Source`を利用することで、テキストを読み込むことができる。


 - fromFile
 - fromURL
 - fromInputStream

!SLIDE

## 読み込んだテキストの処理

コレクション系とほぼ同じAPIが利用できる。


```scala
Source.fromURL(htp://numa08.net).foreach {println(_)}
```


!SLIDE

まあ、正直そこまで強力じゃないです。

 - javaと比較するとたしかに便利だけど
 - バイト列の操作とかめんどい
 - 結局`scala-io`とか外部ライブラリ使う

!SLIDE

## システムのコマンドを実行

 - scalaの非常に強力なAPI達
 - システムのコマンドの実行と、結果の取得がお手軽
 - システム依存になるので、状況を考えて

!SLIDE

## システムのコマンドを実行する


```scala
"ls" run
```

!SLIDE

## システムのコマンドをリダイレクトする


```scala
"ls" #> new java.io.File("file") run
```


!SLIDE

## システムのコマンドをパイプする


```scala
"ls" #| "sort" run
```

!SLIDE

## コマンドの結果を得る


```scala
val res = "ls" run
```


!SLIDE

## まとめ

 - IOは割りと便利
 - 足りない部分は外部ライブラリで補う
 - システムのコマンドをお手軽に触れる
 - うまく使えばちょう便利