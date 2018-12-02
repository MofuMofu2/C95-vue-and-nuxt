# デプロイと反省

配信先は[Netlify](https://www.netlify.com/)としました。GitHubと連携できる点・すぐにデプロイができる点・無料でHTTPS対応をやってくれる点・VueでもNetlifyを利用したデプロイが考慮されているからです。

## アカウントの作成

Netlifyは基本的にホスティングされたGitリポジトリをビルド・デプロイします。アカウントを作るときにGitリポジトリをホスティングするサービスが基本となっている点からも特徴を伺うことができますね。今回はGitHubの``MofuMofu2``というアカウントをNetlifyに連携したいと思います。

![連携するアカウントを選択する](../images/chapter7/signup.png)

次に、どのGitリポジトリを連携するか選択します。今回は``portfolio-vue``リポジトリだけをデプロイする予定なので、``Only select repositories``を選択します。

![特定のGitリポジトリを連携する](../images/chapter7/select_repo.png)

すると、次のような画面が表示されます。

![ログイン後](../images/chapter7/select_repo.png)

## デプロイする

はじめに、どのGitリポジトリをデプロイするか決定します。今回はGitHubのリポジトリをデプロイします。

![どのリポジトリをデプロイするか決める](../images/chapter7/create_new_site_01.png)

次に、デプロイするために必要な情報を記載します。

- デプロイする対象のブランチ[^deploy-branch]
- ビルドコマンド
- 公開用ディレクトリ名（``dist``）

今回はnpmでパッケージ管理をしているので、ビルドコマンドは``npm run build``となります。デプロイコマンドは自身の環境によって異なるため、Vue CLIの[公式ドキュメント](https://cli.vuejs.org/guide/deployment.html)（``https://cli.vuejs.org/guide/deployment.html``）を確認してください。AWSやGitHub Pagesへのデプロイ方法もしっかりと記載があります。

![デプロイコマンドなどの指定](../images/chapter7/create_new_site_02.png)

[^deploy-branch]: git-flowに沿って開発をするのであれば、masterブランチをデプロイするのが一般的だと思います。

これだけでデプロイすることができます。デプロイ後はURLの変更・独自ドメインの設定などをすることが可能です。

これでやっとアプリケーションは完成！となりました。

## 一連の作業を振り返る

この実装を一通り終えるのに3週間前後かかりました。初めてのWebアプリケーション開発にしてはまあまあちゃんとしたWebサイトを作ることができました。これはVueのエコシステムがしっかりしていること、ユーザーフレンドリーであることが大きいと思います。

### よかった点

まず、**完成してデプロイできた**ということでしょう。諦めずに最後まで取り組んだだけでも十分だと思います。次に、SPAとして動的なWebサイトを作れたことです。難しいことはしていませんが、それなりにきちんと動くものができる。これはVueのすごいところだと思います。
取り組み方で良かった点は、詰まったときに落ち着いて処理の流れを追いかけ、エラーログと照らし合わせながらデバッグができたことでしょうか。うまくいかないと焦ってしまう傾向があるのですが、今回はVueのデバッグツールと標準出力を組み合わせて、どこかが意図していない処理の結果になっているのかを推測できました。コードを書いた歴が長い人ほど、エラーが出たときに実装内容を確認する時間の方が長い気がしています。これは、今後も意識して取り組みたいです。

### 改善点

時間がなくて手が回らなかった部分です。issuesに記載していますので、順次対応していこうと思います。特にレスポンシブ対応はやりたいです。かなり崩れが発生するので…。独自ドメインはお金がかかるので一旦保留ですね。設定方法はわかるのですが…。また、テストもぜひやりたいです。業務でテスト書かない現場ばかりだったので…。

- トップページの実装
- アプリ内のページ遷移の実装
- 画面のURL表示をタイトル表示に切り替える
- レスポンシブ対応
- フォントの埋め込み
- 独自ドメインの取得
- コンポーネントへのテストを記載する
- Nuxt.jsで同じ実装をするとどうなるのか比較する

### 総括

KUSO感を醸し出しつつ、それなりに動くアプリケーションができました。２か月後にはKUSOなサイトからまともなサイトに変更したいですね！

## 参考URL

### Deployment

- https://cli.vuejs.org/guide/deployment.html