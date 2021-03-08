---
theme: gaia
_class: lead
paginate: true
backgroundColor: #fff
backgroundImage: url('https://marp.app/assets/hero-background.jpg')
marp: true
---

# 第2回 インフラ講座

---

# 本講義の流れ
* 今回の講義の範囲について、環境の確認
* 1. コンテナ技術とは？
* 2. Linux概要・操作方法
* 3. Docker概要・環境の構築
* 4. Docker Compose概要・環境の構築
* 5. kubernetes概要・環境の構築

---

Webアプリケーションを開発・運用していくにはどういった知識が必要でしょう？？

---

* フロントエンド => HTML, CSS, JS
* サーバサイド => PHP, Ruby
* データベース => MySQL, Oracle, PostgreSQL
* セキュリティ => Webアプリケーション、インフラ
* クラウド => AWS, GCP, Azure
* ミドルウェア => Ningx, Postfix, BIND
* OS => Windows、Linux、Unix
* ネットワーク => ルーティング、ファイアーフォール

などなど・・・

---

### 今回の講義の範囲

* ミドルウェア
* OS(Linux)
* ネットワーク

これらアプリケーションを動作させるための基盤をコンテナ技術と使いながら学んでいきましょう

---

### 環境の確認

* Docker
  * 【Macの方】Docker Desktop for Mac
  * 【Windowsの方】Docker Desktop for Windows
  * Kubernetesの機能を有効化しておいてください `Preferences` => `Kubernetes` => `Enable Kubernetes` にチェック
* Docker Composer
* 【WIndowsの方】コンテナの操作などwsl2を使って行いますので事前に設定をお願いします。
