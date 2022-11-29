# 概要

ReactベースのフレームワークNext.jsでFirebase上に確認環境を作成します.

Next.js自体はサーバーサイドレンダリングもできますが、Reactの動作確認やデザイン用と使用するので
ここではCSR（Client Side Renderingのみに限定します）

## 環境

* node v18.12.1 (作成時)

* node

## 流れ

1. Firebaseにプロジェクト作成
2. Next.jsで静的ファイル書き出し
3. Firebase Storageにデプロイ
4. 以降 2-3をループ


## Firebaseプロジェクト作成

1. [プロジェクト追加](https://console.firebase.google.com/?utm_source=firebase.google.com&utm_medium=referral&hl=ja)
2. 任意の名前を入力
3. Google アナリティクス -> 有効にしない -> プロジェクトを作成
4. しばらくするとプロジェクトが作成が完了

## Next.js開発

通常開発時
```terminal
yarn dev
```
で http://localhost:3000がブラウザで確認可能

トップページのファイルはpages/index.tsxファイルを編集で変更可能

書き出し
```terminal
yarn build
```

outディレクトリに静的ファイルが書き出される

## Firebase初期化 (一度のみ)

* 一度のみ firebase-cli をインストール

```terminal
yarn global add firebase-tools
```

完了後 firebaseにログイン

```terminal
firebase login
```

1. terminalでエンターを入力ブラウザが立ち上がり認証 -> 許可
2. terminalで認証が完了したと表示されます

# Firebaseプロジェクトと紐付け

1. .firebase.sample をコピーして、.firebaseを作成
2. Firebase上に作成したプロジェクトidをdefaultに入力

(idはFirebase上のプロジェクト概要の歯車で設定から確認できます)

## デプロイ

```terminal
firebase deploy
```

上記実行でHosting URLにアクセスすると書き出したoutディレクトリを確認することができます。

以降、書き出し -> デプロイを繰り返し


## その他

* pagesディレクトリにxxxx.tsx というファイルを作成すると /xxxxというページが書き出し時に作成されます。[参考 ファイルベースルーティング](https://nextjs-ja-translation-docs.vercel.app/docs/routing/introduction)
* scssを使用可能 (styles ディレクトリに配置)
