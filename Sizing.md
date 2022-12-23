# サイジングにおいて知っておくべきこと

ElasticSearch のシャードは インデックスを分割して分散して保持できる単位です.

- ヒープ領域 1 GiB あたり 20 シャード未満に保つことが推奨されています.
- ヒープ領域は インスタンスのメモリの 50%が割り当てられ、最大は 32GiB となります.

m6g xlarge では メモリが 16GiB のため、ヒープ領域は 8GiB のため、1 インスタンスで 160 シャードを保持できることになります.

- 1 シャードあたり 検索レイテンシーが主要なパフォーマンス目標の場合、10 から 30 GiB とすることが推奨されています.

各 インデックス ごとに シャードをいくつにするか設定できるので、１つのインデックスが上記のサイズに収まるのであれば、1 シャードとしてください. そうでなければ シャードの数を増やしていく必要があります.

なお、ノードあたりのシャードの上限もありますが、こちらは上記を踏まえるとあまり気にする必要はなさそうです.

- ノードあたり 1,000 シャードが上限である.

# リファレンス

Amazon OpenSearch Service ドメインのサイジング
https://docs.aws.amazon.com/ja_jp/opensearch-service/latest/developerguide/sizing-domains.html

Auto-Tune
https://docs.aws.amazon.com/opensearch-service/latest/developerguide/auto-tune.html

Elasticsearch クラスターのシャード数はいくつに設定すべきか？
https://www.elastic.co/jp/blog/how-many-shards-should-i-have-in-my-elasticsearch-cluster
