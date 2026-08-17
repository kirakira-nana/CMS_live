![GitHub](https://img.shields.io/github/license/mashape/apistatus.svg)

ResidenceCMS は [Symfony 7][1] 上の、軽量で高速な物件管理システムです。

![GitHub](https://raw.githubusercontent.com/Coderberg/ResidenceCMS/master/docs/images/screenshot.png)

作者：[Nana](https://github.com/kirakira-nana)

## 必要環境

- PHP 8.2.0 以上
- PDO PHP 拡張
- GD PHP 拡張
- MySQL >= 5.7
- その他 [Symfony の通常の要件][2]

## インストール

1. Composer をインストールする（http://getcomposer.org/download を参照）

2. [Composer][3] でプロジェクトを作る

   ```
   $ composer create-project coderberg/residence-cms mywebsite.loc
   ```
3. 作成したフォルダへ移動する

   ```
   $ cd mywebsite.loc
   ```

4. Web サーバーのドキュメントルートを `public` ディレクトリに設定する。

5. `.env` から `.env.local` を作り、データベース接続を記入する

    ```
    DATABASE_URL=mysql://db_user:db_password@127.0.0.1:3306/db_name
    ```

6. 次を実行する

    ```
    $ php bin/console app:install
    ```

7. http://mywebsite.loc/ja/admin を開き、ログインする。

   ```
   login: admin
   password: admin
   ```

8. 問い合わせフォームを使う場合は、`.env.local` の `MAILER_DSN` を設定する。

## テスト

1. `.env.test.local` の `DATABASE_URL` を変更する

   ```
   DATABASE_URL=mysql://db_user:db_password@127.0.0.1:3306/db_name
   ```

2. ChromeDriver を入れる

   ```
   vendor/bin/bdi detect drivers
   ```

3. テストを実行する

   ```
   php bin/phpunit
   ```

## 追加ドキュメント
- [Docker コンテナで Residence CMS を動かす][4]

[1]: https://symfony.com/
[2]: https://symfony.com/doc/current/setup.html#technical-requirements
[3]: https://getcomposer.org/doc/03-cli.md#create-project
[4]: docs/docker.md
