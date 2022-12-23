# Search

## Query

### Query と Filter

https://www.elastic.co/guide/en/elasticsearch/guide/master/_queries_and_filters.html

As a general rule, use query clauses for full-text search or for any condition that should affect the relevance score, and use filter clauses for everything else.

一般的なルールとして、フルテキスト検索か関連するスコアに影響する条件があるときは クエリ を使い、それ以外はフィルタを使う.

### Filtered Query

query と filter を組み合わせることができます.
aggregations をフィルタすることも可能です.

フィルタは スコアを数値計算せず、マッチしたか否かを返すだけなので、処理を高速化することができます.

ユースケース

- 日付が範囲内であるものを抽出する

### Post Filter

aggs はそのままで検索結果をフィルタしたい

ユースケース

- ファセットは 選択したタグでは絞り込まず、検索結果は ファセットで 選択したタグで絞り込む (同一ファセットの OR 条件)
