!SLIDE

## Scalaとデータ構造

!SLIDE

## Scalaの強力な標準APIたち

 - Listに対する逐次処理
 - List2Listの変換処理
 - Mapに対する処理
 - Map2List,List2Mapなど
 - タプルもサポート

!SLIDE

## Scalaの強力なAPIたち

 - 基本的に非破壊的
 - 新しいオブジェクトを返す
 - 美しいメソッドチェイン！！
 - 流れるような処理！！

!SLIDE

## Listの生成


```scala

val list = 2 :: 0 :: 1 :: 4:: Nil

```

!SLIDE

## Listの生成


```scala
// :: はListの連結
// Nil自体が空のListを表す
val list = 2 :: 0 :: 1 :: 4:: Nil
// => list: List[Int] = List(2, 0, 1, 4)
```


!SLIDE

## foreach
##Listの逐次処理

 - Listの中の要素に対して同じ処理を行う
 - 行う処理は、引数として渡された関数を利用する
 - 関数を引数とか、関数型言語っぽい

!SLIDE

## foreach


```scala

val list = 2 :: 0 :: 1 :: 4:: Nil
list.foreach{i => println(i + 1)}
```


!SLIDE

## foreach


```scala

val list = 2 :: 0 :: 1 :: 4:: Nil
list.foreach{i => println(i + 1)}
//Listの要素を変数iとする
//iの内容に1足したものを出力
//3
//1
//2
//5
```

!SLIDE

## ちょっとまって！
 
 - 関数を引数にできるのはおもしろかも？
 - でも、そんな他の言語でもできるよね？

!SLIDE

## ちょっとまって！


```java

final List<Integer> list = Arrays.asList(2, 0, 1, 4);
foreach(int i : list) {
	System.out.println(i + 1);
}
```


!SLIDE

##  本当の戦いはここからだ

 - 関数を引数にできるのは結構強い
 - 引数に取った関数利用して
     - オブジェクトの抽出
     - オブジェクトの変換
     - Listを単一のオブジェクトに変える

!SLIDE

## 文字列に変換するmkString


```scala
val list = 2 :: 0 :: 1 :: 4:: Nil
list.mkString 
res1: String = 2014   
```

!SLIDE

## 文字列に変換するmkString


```scala
val list = 2 :: 0 :: 1 :: 4:: Nil
list.mkString 
res1: String = 2014   
//要素をすべて連結した文字列"2014"が生成される
```

!SLIDE

## 文字列に変換するmkString


```scala
scala> list.mkString(",") 
res2: String = 2,0,1,4
```

!SLIDE

## 文字列に変換するmkString


```scala
scala> list.mkString(",") 
res2: String = 2,0,1,4
//要素の間に","を挿入した文字列"1,2,3"が生成される
```


!SLIDE

## 文字列に変換するmkString



```scala
scala> list.mkString("[", ",", "]")  
res3: String = [2,0,1,4]
```


!SLIDE

## 文字列に変換するmkString



```scala
scala> list.mkString("[", ",", "]")  
res3: String = [2,0,1,4]
//要素の先頭に"[",要素間に",",要素の末尾に"]"を連結した文字列
//"[1,2,3]"が生成される
```

!SLIDE

## Javaだとどうなる？


```java
final StringBuilder builder = new StringBuilder();
final List<Integer> list = Arrays.asList(2, 0, 1, 4);
final String first = "[", seq = "," , end = "]";
```


!SLIDE


```java
builder.append(first);
boolean first = true;
foreach(int i : list) {
	if(first) {
		builder.append(i);
		first = false;
	} else {
		builder.append(seq);
		builder.append(i);
	}
}
builder.append(end);
System.out.println(builder.toString());
```


!SLIDE

## うわ！めんどくせぇ！！

!SLIDE

ちなみに、この実装はScala内部の実装をベースに作りました

!SLIDE

この後は面倒なので、Javaとの比較はやりません

!SLIDE

## Listを別のListに変換するMap


```scala
val list = 2 :: 0 :: 1 :: 4:: Nil
list.map{i => i.toString()} 
```

!SLIDE

## Listを別のListに変換するMap


```scala
val list = 2 :: 0 :: 1 :: 4:: Nil
list.map{i => i.toString()}
//List[String] = List(2, 0, 1, 4)
//整数のリストを文字列のリストに変換
```

!SLIDE

## 条件に合う要素のみのListを作るfilter


```scala
val list = 2 :: 0 :: 1 :: 4:: Nil
list.filter{i => i % 2 == 0}
```


!SLIDE

## 条件に合う要素のみのListを作るfilter


```scala
val list = 2 :: 0 :: 1 :: 4:: Nil
list.filter{i => i % 2 == 0}
//2で割った余りが0のもののみを取り出す
// List[Int] = List(2, 0, 4) 
```

!SLIDE

 - こんな感じのメソッドがたくさんある。
 - ぶっちゃけ覚えられないです
 - リファレンス見ましょう

!SLIDE

 - ひたすら紹介したら日が暮れます
 - 何が便利なの？
 - どう便利なの？
 - あとで話します