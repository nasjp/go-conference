# OSS Performance Tuning Tips

## Tuning の進め方

- 不満のハードルを下げる

- プラグインは基本遅いものと考える

- 気軽に調査できるような仕組みを作る

- cli で profile を取る

github.com/pkg/profile

main に 追加するだけ

めちゃくちゃ長い場合は

net/http/pprof のほうがよいかも

disasm

## benchmark

最適化で消えてないか確認する

benchmark を書くと profile が簡単に取れる

go help testflag を読む

## どうやればマージされるか

変更が少ない

相手のコストを増やさない

破壊的変更がない(重要!!!)

保守が難しくなる実装がない

使用ライブラリはアクティブか

テストが絶対に書いてある

## 最初のベンチのとり方

go test -bench . -count=10 -timeout=300000s > old.out

## ソースとプロファイルの関係がわからなくならないようにする

## 多くのプロファイルがあるとどれがどれだかわからなくなる

go tool pprof --diff

## 引き出しを増やす

メモリ使用量は問題になりがち

適切なhashを選択する

src-d/go-git

io.Copy は大量に呼ばれるときは ios.CopyBuffer にするとメモリを削減できる場合がある

GoogleContainerTools/kaniko

mmcloughlim/avo

go asm をはきだしてくれる

go generate
