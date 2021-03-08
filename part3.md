---
theme: gaia
_class: lead
paginate: true
backgroundColor: #fff
backgroundImage: url('https://marp.app/assets/hero-background.jpg')
marp: true
---

# 3. Docker概要・環境の構築

---

# Dockerとは？

コンテナランタイムの一つ
（他にはHaconiwa、LXCなど）

スローガン

> Build, Ship, and Run Any App, Anywhere

どこでも、あらゆるアプリを構築、出荷、実行

http://docs.docker.jp/v1.11/engine/understanding-docker.html#id27

---

### Build

Dockerfileを使って、コンテナイメージをビルドすることができる。

コンテナイメージ => コンテナの元となる
（イメージとしては、クラスとインスタンスのような関係性）

```Dockerfile
FROM nginx

RUN apt install -y vim
COPY .env /tmp/.env

CMD nginx start
```

```bash
docker build ./ -t sample
```

---

### Ship

Dockerレジストリと呼ばれるイメージ配布用のサーバを使って、
イメージをアップロード・ダウンロードできる。
=> 他のコンピュータでも動かすことができる。

* [Docker コンテナー、イメージ、レジストリ](https://docs.microsoft.com/ja-jp/dotnet/architecture/microservices/container-docker-introduction/docker-containers-images-registries)
* [Docker レジストリ の理解](https://docs.docker.jp/registry/introduction.html)

---

### Run

コンテナを通じて、プログラムを実行可能

* Rubyのスクリプトを実行する

```bash
docker run --rm rubylang/ruby:2.6.6-bionic ruby -e '5.times { |i| print i }'
01234
```

* PostgreSQLサーバを立ち上げる

```bash
docker run --rm -e POSTGRES_PASSWORD=postgres -p 5432:5432 postgres:9.6-alpine
```

---

## Dockerを使ってみよう

以下のドキュメントを見ながら、dockerの操作を行いましょう
http://docs.docker.jp/engine/reference/commandline/

---

よく使うコマンド一例

```
docker run --rm -it rubylang/ruby:2.6.6-bionic bash
```

* run・・・コンテナを作成、startする
* --rm・・・コンテナ終了時、自動的に削除
* -it・・・インタラクティブに操作できるようにする（標準入力を受け付ける、疑似ttyの割当）
* rubylang/ruby:2.6.6-bionic・・・コンテナイメージ、タグ
* bash・・・コンテナ内で実行するコマンド

---

### 課題1

1. `rubylang/ruby:2.6.6-bionic` のイメージを使って文字を出力してみましょう（ヒント: echo コマンド）
2. `rubylang/ruby:2.6.6-bionic` のイメージを使ってRubyのスクリプトを実行してみましょう（ヒント: ruby -e）

---

### 課題2

以下の条件でDockerfileを作りビルドしてみましょう

* `rubylang/ruby:2.6.6-bionic` をベースとすること
* 以下の System packages, Node.js, Yarn をインストールしていること
  * https://docs.joinmastodon.org/admin/install/
  * Yarnは `npm install --global yarn` でインストールしましょう

Dockerイメージの作り方参考:
http://docs.docker.jp/engine/reference/builder.html

---

### 課題1 回答例

1.

```bash
docker run --rm rubylang/ruby:2.6.6-bionic echo "hoge"
```

2.

```bash
docker run --rm rubylang/ruby:2.6.6-bionic ruby -e '5.times { |i| print i }'
```

---

### 課題2 回答例

以下の36行目まで
https://github.com/takapi86/docker-mastodon/blob/master/docker/web/Dockerfile

---

### おすすめ教材

#### 公式ドキュメント
http://docs.docker.jp/engine/reference/commandline/
http://docs.docker.jp/engine/reference/builder.html

#### コンテナ未経験新人が学ぶコンテナ技術入門
https://www.slideshare.net/KoheiTokunaga/ss-122754942

#### イラストでわかる DockerとKubernetes
https://gihyo.jp/book/2020/978-4-297-11837-2
