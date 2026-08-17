## Docker コンテナで Residence CMS を動かす

1. リポジトリをクローンする
```shell
git clone https://github.com/kirakira-nana/ResidenceCMS.git
cd ResidenceCMS
```

2. `.env.local` を作り、`MAILER_DSN` を Mailpit 向けに更新する
```shell
cp .env .env.local
sed -i 's/MAILER_DSN=.*/MAILER_DSN=smtp:\/\/mailer:1025/' .env.local
```

3. コンテナをビルドして起動する
```shell
docker compose build --no-cache
docker compose up --pull always -d --wait
```

4. アプリをインストールする
```
docker compose exec -T php bin/console app:install
docker compose exec -T php bin/phpunit
```

5. ブラウザで `https://localhost` を開き、[自動生成された TLS 証明書を許可](https://stackoverflow.com/a/15076602/1352334) する

---

追加サービス:

- PhpMyAdmin http://localhost:8081
- Mailpit http://localhost:8025

詳細は https://github.com/dunglas/symfony-docker を参照してください。
