# Go GC algorithm 101

Refs: <https://speakerdeck.com/taxio/go-gc-algorithm-101>

garvage collection

中村さんの
ガーベジコレクションのアルゴリズムと実装はわかりやすい

## gc の基礎的な理論

gc

goではruntimeに搭載されている

mattnさんのgcのqiita参照

- オブジェクと
  - ヘッダ
  - フィールド

- ミユーテータ

root オブジェクトの参照関係を追うための始点

Rootに存在するオブジェクトをrootオブジェクトという

死んでいるオブジェクト
rootから辿れないオブジェクト

## mark & sweep gc

- 生きているオブジェクトを探すmark
- 死んでいるオブジェクトを探すsweep

デメリット

メモリの断片化

stop the world の影響でlatencyが大きい

stop the world mark 中にsweepしない

allcate

## bitmap marking

mark をオブジェクトのヘッダにするのではなく、別の領域にまとめる

- seepが早い
- mark flagを戻すのが楽

## concurrent mark & seep gc

ミューテータとgcを平行に動作させる

3色marking

探索中のmarkがある

goではqueueで実装されている

stw 削減

write barrier によってスループットが低下


