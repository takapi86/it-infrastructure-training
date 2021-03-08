---
theme: gaia
_class: lead
paginate: true
backgroundColor: #fff
backgroundImage: url('https://marp.app/assets/hero-background.jpg')
marp: true
---

# 4. Docker Compose概要・環境の構築

---

# Docker Compose とは

> Compose とは、複数のコンテナを定義し実行する Docker アプリケーションのためのツールです。Compose においては YAML ファイルを使ってアプリケーションサービスの設定を行います。コマンドを１つ実行するだけで、設定内容に基づいたアプリケーションサービスの生成、起動を行います。

https://docs.docker.jp/compose/overview.html

---

例えば、こういうコマンドで実行していたものを

```
docker run --rm -v /hoge:/hoge -p 8080:8080 app:latest app start
docker run --rm -v /huga:/huga -p 5432:5432 db:latest db start
```

---

```yaml
version: '3'
services:
  app:
    image: app:latest
    command: app start
    ports:
    - "8080:8080"
    volumes:
    - /hoge:/hoge
  db:
    image: db:latest
    ports:
    - "5432:5432"
    volumes:
    - /huga:/huga
```

```bash
docker-compose up
```

---

### 課題1
* 1. 以下のイメージを使って、redisを起動させてみましょう。
  * `redis:6.0-alpine`
* 2. 以下のイメージを使って、postgresを起動させてみましょう。
  * `postgres:9.6-alpine`
  * 環境変数には以下を設定します
    * POSTGRES_PASSWORD: postgres
* 3. 前章で作成したDockerfileをdocker-composeコマンドでビルドしてみましょう

参考: https://docs.docker.jp/compose/toc.html

---

### 課題2

1. 以下の手順で、ローカルのKubernetes上でmastodon起動してみましょう。

https://github.com/takapi86/docker-mastodon#docker-compose-%E7%92%B0%E5%A2%83%E3%82%A4%E3%83%B3%E3%82%B9%E3%83%88%E3%83%BC%E3%83%AB%E6%89%8B%E9%A0%86

---

### 課題3

1. 自分の好きな開発環境をDocker Composeを使って作ってみましょう

PHP, Node.js, Rails の開発環境など

#### 参考
https://github.com/takapi86/rails-tutorial-in-docker

---

### 課題1 回答例

1.

```yaml
version: '3'
services:
  redis:
    image: redis:6.0-alpine
```

---

2.

```yaml
version: '3'
services:
  db:
    image: postgres:9.6-alpine
    environment:
      POSTGRES_PASSWORD: postgres
```

---

3.

```yaml
version: '3'
services:
  app:
    build: ./ # Dockerfileを同じディレクトリに配置
```
