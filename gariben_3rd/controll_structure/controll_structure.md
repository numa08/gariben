!SLIDE

## Scalaと制御構文

!SLIDE

## Scalaと制御構文

 - Javaとかでお馴染みのif,for,whileとかはある
 - 意味合いが違ったりするので注意
 - もっと便利なパターンマッチの話とか

!SLIDE

## Scalaのfor

 - いわゆるループ構文
 - コレクションとかの逐次処理
 - ただし式です
 - 値を返せます

!SLIDE

## Scalaのfor


```scala
for( i <- 1 to 20) {
 println(i)
}
```


!SLIDE

## Scalaのfor


```scala
for( i <- 1 to 20) {
//1から20までの繰り返し
 println(i)//とりあえず表示する
}
```


!SLIDE

## Scalaのfor


```scala
val i = List(1, 2, 3, 4, 5)
for( i <- l) {
 println(i)
}
```


!SLIDE

## Scalaのfor



```scala
val i = List(1, 2, 3, 4, 5)
for( i <- l) {
//Listの中身に対しての逐次処理
//まあ、この程度ならList.foreachを使いますが
 println(i)
}
```


!SLIDE

## ちなみに


```scala
1 to 10     //Range(1,2,3...10)
0 until 10  //Range(0,1,2,3...10)
9 to 0 by -1//Range(9,8,7..0)
```


!SLIDE

## for-yield

普通のfor式は返り値は無いが、yieldをつけることで演算結果をコレクションとして返すことができます。

!SLIDE

## for-yield


```scala
val i = for( i < 1 to 20) yield {
　"numa0" + i
}
```


!SLIDE
## for-yield


```scala
val i = for( i < 1 to 20) yield {
　"numa0" + i
}
// Vector(numa01, numa02, numa03, numa04, 
//numa05, numa06, numa07, numa08,
// ...numa019 ,numa020)
```


