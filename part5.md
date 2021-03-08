---
theme: gaia
_class: lead
paginate: true
backgroundColor: #fff
backgroundImage: url('https://marp.app/assets/hero-background.jpg')
marp: true
---

# 5. kubernetes概要・環境の構築

---

# kubernetesとは何か？

> Kubernetes または k8s (k + 8 文字 + s)、もしくは短縮形の「kube」とは、Linux コンテナの操作を自動化するオープンソース・プラットフォームのことです。Kubernetes を使用すると、コンテナ化されたアプリケーションのデプロイとスケーリングに伴う多くの手動プロセスをなくすことができます。

https://www.redhat.com/ja/topics/containers/what-is-kubernetes

=> もともとはGoogle内部で使っていたプラットフォームをOSS化したもの

---

# Kubernetesを使うと何が出来るのか

いろんな良いことがある
https://kubernetes.io/ja/docs/concepts/overview/what-is-kubernetes/

---

# マネージドKubernetes
* Amazon（AWS）
  * Amazon EKS
* Google（GCP）
  * Google Kubernetes Engine
* Microsoft（Azure）
  * Azure Kubernetes Service (AKS)

---

# Pod

https://kubernetes.io/ja/docs/tutorials/kubernetes-basics/explore/explore-intro/

---

### 宣言的な構成管理

例えば、Aの値を5にしたい

#### 命令的、手続き的
[人] ----> [命令(+2)] ---> [サーバ(現在Aは3)]
現在のAが3であれば、+2と命令しなければならない
=> 今の状態を把握する必要がある（操作が煩雑になりやすい）

#### 宣言的
[人] ----> [宣言] ---> [サーバ]
現在のAが2だろうが、3だろうが、5であるべきという宣言をすると5になってくれる => 状態を意識しなくても良くなる

---

### 宣言的な構成管理の例

```yaml
apiVersion: apps/v1
kind: Deployment
spec:
  replicas: 3 # ここにあるべきPodの数を記述して適用するとその通りになる
  selector:
    matchLabels:
      app: nginx
  template:
    metadata:
      labels:
        app: nginx
    spec:
      containers:
      - name: nginx
        image: nginx:1.14.2
```

---

### 課題

1. 以下の手順で、ローカルのKubernetes上でmastodon起動してみましょう。

https://github.com/takapi86/docker-mastodon#docker-compose-%E7%92%B0%E5%A2%83%E3%82%A4%E3%83%B3%E3%82%B9%E3%83%88%E3%83%BC%E3%83%AB%E6%89%8B%E9%A0%86

2. appのReplicaの数を増やしてみましょう
3. appのReplicaの数が増えていることを確認しましょう

参考:
https://kubernetes.io/ja/docs/reference/kubectl/cheatsheet/

---

### すべて課題が終わった方
* 前章 `自分の好きな開発環境をDocker Composeを使って作ってみましょう` で作成したコンテナをkubernetes上で動作させてみましょう
