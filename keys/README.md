
## 認証鍵の生成

次は、vagrant up 前に、パソコン上で認証鍵を生成して、keysディレクトリに鍵ペアを配置しておきます。

~~~
ssh-keygen -t rsa -f ./keys/key -N ''
~~~



## キーの登録と確認

この仮想サーバーにログインした後に次のコマンドで登録して、リストを表示できます。

~~~
bx login
bx sl init
bx sl security sshkey-add tf -f keys/key.pub  --note 'test'
bx sl security sshkey-list
~~~~