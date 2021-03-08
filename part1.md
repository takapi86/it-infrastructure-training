---
theme: gaia
_class: lead
paginate: true
backgroundColor: #fff
backgroundImage: url('https://marp.app/assets/hero-background.jpg')
marp: true
---

# 1. コンテナ技術とは？

---

### Linuxコンテナ

仮想化技術

* [ハイパーバイザ型仮想化](https://speakerdeck.com/udzura/inside-out-container-and-its-security?slide=12)（Virtualbox, VMware Playerなど）
* [コンテナ型仮想化](https://speakerdeck.com/udzura/inside-out-container-and-its-security?slide=13)（Docker, LXC, HACONIWA）
  * Linuxの持つ機能で実現している（Linux Namespace, cgroupなど）
  * 1つの[プロセス](https://speakerdeck.com/udzura/the-skelton-of-whales?slide=15)として動いている

Linuxコンテナは直接WindowsやMac上では動きません！

---

### え？WindowsやMacで動かしているけど・・・？

実はDocker Desktop for Mac/WindowsがDocker用のVM（Linux）を構築していて、そのカーネルを共有して使っている。

---

### コンテナだと何が嬉しいのか

ハイパーバイザ型仮想化に比べ

* 起動が高速・軽量
* リソースを細かく制御可能

-> クラウド、IoTに向いている

近年注目されている技術

---

### コンテナランタイム
* Docker
* LXC
* Haconiwa

https://speakerdeck.com/udzura/inside-out-container-and-its-security?slide=15

---

### コンテナの内部的なお話

詳しくは

コンテナは友だち！ /friends-who-are-good-at-containers
https://speakerdeck.com/udzura/friends-who-are-good-at-containers

ペパボ新卒研修座学、コンテナのお話 /the-skelton-of-whales
https://speakerdeck.com/udzura/the-skelton-of-whales

---

### カラーミーショップでのコンテナ活用例

#### 開発環境の刷新
* [カラーミーショップの開発環境をすべてDockerに移行しました](https://tech.pepabo.com/2019/12/10/upgrade-colorme-dev/)

#### 本番環境の刷新

* [カラーミーショップのクラウドネイティブに向けた取り組み](https://speakerdeck.com/takapi86/karamisiyotupufalsekuraudoneiteibunixiang-ketaqu-rizu-mi)

* [SREが取り組むカラーミーショップへのk8s導入](https://speakerdeck.com/ch1aki/sregaqu-rizu-mukaramisiyotupuhefalsek8sdao-ru)
