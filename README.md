# 環境構築

```bash
# entrypointに権限を与える
chmod +x ./USIWSEngine/entrypoint.local.sh
chmod +x ./USIWSEngine/entrypoint.product.sh
```

```bash
# frontendの初期設定(nodemoduleのinstall)
docker build -f ./frontend/Dockerfile.local -t node20_slim_bullseye ./frontend
docker run -it -v $PWD/frontend/:/usr/src/app node20_slim_bullseye bash

# コンテナの中で…
npm install
# ---- installing ----

# コンテナから退出
exit
```

# 起動とリムーブ

```bash
# このコマンドでコンテナを起動(起動したターミナルで ctrl + c で抜ける)
docker-compose -f docker-compose.local.yaml up --build

# このコマンドでコンテナを削除(削除しないと重いよ)
docker-compose -f docker-compose.local.yaml down -v

docker-compose -f docker-compose.local.yaml exec usiwsengine bash
```

<!-- いろいろ -->

```sh
# ==== Format ====
# ${prefix}: 実装の概要を50文字以下で記述 ex)fix:ユーザー情報にnameが足りないのでnameを追加
#
docs: miyamoto.txtを追加した
# コミット本文(50文字で収まらない場合はこちらに)...
gitの練習としてmiyamoto.txtを追加して、pushしてみる

# ==== Prefix ====
# feat     新規機能、新規ファイル追加
# change   仕様変更による機能修正
# test     テスト追加や間違っていたテストの修正
# delete   ファイル削除
# fix      バグ修正
# style    空白、セミコロン、行、コーディングフォーマットなどの修正
# refactor 既存の振る舞いを変更しないコード改善
# perf     パフォーマンスを向上させるコード変更
# chore    ビルド、補助ツール、ライブラリ関連、開発環境変更
# docs     ドキュメントのみ修正

# ==== Emojis ====
# 🔖  :bookmark: バージョンタグ（Version Tag）
#
# ※リリースでバージョンタグを付ける際に使用

# ==== Rules ====
# 1. コミット本文を記述する場合は、概要とコミット本文の間に空行1行あける
# 2. 概要は50文字以下で記述する
# 3. 概要の末尾はピリオドで終わらない
# 4. 概要は命令法で記述する
# 5. 本文は72文字で改行する
# 6. 本文ではhowではなくwhatとwhyを記述する
```
