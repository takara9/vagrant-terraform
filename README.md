# vagrant-terraform

この Vagrantfile は、Terraformによって IBM Cloud の仮想サーバーをプロビジョニングして、Ansibleで自動設定するためのワークステーション（仮想サーバー）を起動するためのものです。これを利用するためには、Vagrant と VirtualBox がインストールされたパソコンが必要です。


## 仮想サーバーのSSH鍵の準備

このワークステーションが起動した後に、Terraform と Ansible に必要な仮想サーバーのSSH鍵を生成して、クラウドに登録しなければなりません。もちろん、事前に鍵ペアが作られ、公開鍵がクラウドに登録され、秘密鍵が手元にあれば、それを利用することができます。

この鍵の生成と、クラウドへの登録方法は、keys ディレクトリへ書いてありますので、参照ください。


## インストールするパッケージ

vagrant up することで、次のパッケージがインストールされて、仮想サーバーが起動します。

* ansible
* python-minimal, python-pip
* unzip
* terraform
* terraform-provider for IBM Cloud
* 仮想サーバーの秘密鍵（認証鍵）
* IBM Cloud CLI (Git,Docker,Helm,kubectl,curl,IBM Cloud Developer Tools plugin, IBM Cloud Functions plugin, IBM Cloud Container Registry plugin, IBM Cloud Kubernetes Service plugin, sdk-gen plugin が含まれます)

仮想サーバーの秘密鍵は、keys/key として配置してください。そうするこで、仮想サーバーのvagrantのホームディレクトリにコピーして、必要なパーミッションとユーザーとグループを設定します。


## 起動とログイン、初期動作確認


次のように起動して、ログイン後に、環境を確認できます。


~~~
$ git clone https://github.com/takara9/vagrant-terraform
$ cd vagrant-terraform
$ vagrant up
＜中略＞

$ vagrant ssh
＜中略＞

$ terraform --version
Terraform v0.12.14
+ provider.ibm v1.2.5

$ ibmcloud --version
ibmcloud version 1.1.0+cc908fe-2020-04-29T04:06:12+00:00

$ ansible --version
ansible 2.9.9
~~~



