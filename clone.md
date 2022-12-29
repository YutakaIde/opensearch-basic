# 異なるインスタンスにクローンする

## 前提事項

- IAM ロール の 作成 と IAM ユーザーにロールをアタッチする

  - IAM ポリシーのアタッチ
  - 信頼関係を編集する

- コピー元とコピー先で手動スナップショットレポジトリを登録する (Python)

- コピー元で手動スナップショットを作成する

  ```
  curl -XPUT 'domain-endpoint/_snapshot/repository-name/snapshot-name'
  ```

## クローン

- コピー先で手動スナップショットから復元する

  スナップショットの確認

  ```
  curl -XGET 'domain-endpoint/_snapshot/repository-name/_all?pretty'
  ```

  インデックスの削除

  ```
  curl -XDELETE 'domain-endpoint/_all'
  ```

  スナップショットの復元

  ```
  curl -XPOST 'domain-endpoint/_snapshot/repository-name/snapshot-name/_restore'
  ```

# リファレンス

https://aws.amazon.com/jp/premiumsupport/knowledge-center/opensearch-migrate-domain/

https://docs.aws.amazon.com/ja_jp/opensearch-service/latest/developerguide/managedomains-snapshots.html#managedomains-snapshot-curator
