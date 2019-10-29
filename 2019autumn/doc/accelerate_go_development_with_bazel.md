# Accelerate Go development with Bazel

Bazel

ベイゼル

protobuf

make みたいな build tool

記法はpython 臭い

並列ビルド

差分ビルド

sandobox 環境で管理

再現性が非常に高い

Monorepo に使える！

google uber dropbox printerset stripe で使われている

キャッシュと差分ビルドにより速度向上

sandobox なので 本質的でない生成ファイルをVCSに含めなくて良い

## bazelbuild/bazel-gazelle

go ファイルの依存関係を解析し、buildファイルを生成する

(自分で書かなくて良い)

## .bazelrc

bazel のコマンドにデフォルトオプションを設定する

## Bazelisk

bazelversion のバージョンを参照してBazelのバージョン管理をするランチャー

実行環境に応じた Bazel をインストール

さらに、Bazelが 適切な Go のバージョンをインストールしてくれる！(sandbox)

## nogo

静的解析ツール

デカイものリポには適すかも
