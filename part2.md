---
theme: gaia
_class: lead
paginate: true
backgroundColor: #fff
backgroundImage: url('https://marp.app/assets/hero-background.jpg')
marp: true
---

# 2. Linux概要・操作方法について

---

### Linuxとは？

> Linux® は、オープンソースのオペレーティング・システム (OS) および IT インフラストラクチャ・プラットフォームです。Linux は元々、1991 年に Linus Torvalds 氏が趣味として考案し開発したものです。Linus 氏は大学在学中、Unix の原則と設計に基づいた MINIX オペレーティング・システムの代わりとなる、無料のオープンソース版を作成したいと考えました。その趣味が高じて開発されたシステムは、今や最大のユーザーベースを持つ OS、公開中のインターネット・サーバーで最も使用されている OS、そしてトップ 500 の最速スーパーコンピュータで使用されている唯一の OS となっています。

https://www.redhat.com/ja/topics/linux

---

### Linuxディストリビューション
* RedHat系
  * Red Hat Enterprise Linux（RHEL）
  * CentOS
* Debian系
  * Debian
  * Ubuntu
* その他
  * Android

https://gigazine.net/news/20060827_linux_distributions/

---

### コンテナからLinuxを操作してみよう

https://speakerdeck.com/udzura/inside-out-container-and-its-security?slide=28

### 課題1
* 1. コンテナ内にbashで入ってみましょう
  * `docker run --rm -it rubylang/ruby:2.6.6-bionic bash`（抜けるには `exit`）
* 2. `/tmp/` 以下にカレントディレクトリを移動してみましょう
* 3. `/tmp/` 以下に `example.txt` ファイルを作成してみましょう
* 4. `/tmp/` 以下にディレクトリのファイルを一覧表示してみましょう
---

### 課題2
* 1. `/etc/os-release` から `VERSION_ID` の行だけを表示させてみましょう
* 2. `/etc/os-release` の上から3行だけを表示させてみましょう
* 3. `/etc/os-release` `UBUNTU_CODENAME` の値だけ（`=`の右側のみ）を表示させてみましょう

---

### 課題 回答例

2.

```bash
cd /tmp/
```

3.

```bash
touch /tmp/example.txt
```

4.

```bash
ls /tmp/
```

---

### 課題2 回答例

1.

```bash
grep "VERSION_ID" /etc/os-release
```

2.

```bash
head -n3 /etc/os-release
```

3.

```bash
grep "UBUNTU_CODENAME" /etc/os-release | awk -F= '{print $2}'
```

---

### おすすめ教材

* Linux標準教科書
https://linuc.org/textbooks/linux/

* 新しいLinuxの教科書
https://www.sbcr.jp/product/4797380941/
