# Go で"超高速"な経路探索エンジンをつくる

DeNA.go 11/1 beego goa

カーナビ の経路探索

グラフ

重み付き有向グラフ

ダイクストラ

出発地点から近い順(コストが低い順)に最短経路を列挙していく

数100万件を N(2)では 時間がかかりすぎる

Bidirectional Dijkstra

ダイクストラをゴールからもやると早くなったりする

Constraction Hierarchy

OSRMでも採用されている

Priority Queue(優先度付きキュー)

<https://golang.org/pkg/container/heap> で簡単に使える

Refs: <https://golang.org/blog/go-slices-usage-and-internals>

slice のベストプラクティス

- length や capasity を指定して作成する

makeで!

- メモリアロケートをなるべく少なくする

```go
make([]*Hoge, 0, 1e5) -> メモリしかアロケートされない
make([]Hoge, 0, 1e5) -> フィールドすべてがアロケートされる
```

- length を延長し allocate 済みの領域を使う

Refs: <https://speakerdeck.com/avvmoto/go-conference-2019-autumn-go-ch>

Refs: <https://www.ardanlabs.com/blog/2013/12/macro-view-of-map-internals-in-go.html>

map も capacity hint に適切な値を渡してmake!
