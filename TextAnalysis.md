# Text analysis

## analyzer

### アナライザの種類

- index analyzer : 対象データにインデックスを作成されるとき使用される
- search analyzer : 検索キーワードに使用される

### アナライザの順番

以下の順番で分析される

- Character filters
  文字ごとの特別な処置など
- Tokenizer
  ngram など
- Token filters
  ステミングなど

```
GET /_analyze
{
 "tokenizer": "whitespace",
 "text": "Elasticsearch is simple"
}
```

```
GET /_analyze
{
 "tokenizer": "whitespace",
 "char_filter" : ["html_strip"],
 "text": "<p>Elasticsearch is simple</p>"
}
```

### インデックスごとにアナライザを指定できる

インデックスに設定されたアナライザの結果を確認する方法

```
POST {index_name}/_analyze
{
  "analyzer": "{english}",
  "text": "{word}"
}
```

https://dev.classmethod.jp/articles/elasticsearch-starter2/

https://www.elastic.co/jp/blog/how-to-implement-japanese-full-text-search-in-elasticsearch
