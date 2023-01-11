# Synonym Token Filter

Synonym Token Filter を使用すると 類義語でヒットさせることができます.

Synonym Token Filter は、インデックス作成時と検索時のいずれかのアナライザーで使用することが可能です.

アナライザーの設定例は以下となります.

```
{
  "analyzer": {
    "my_synonyms": {
      "tokenizer": "whitespace",
      "filter": [
        "synonym"
      ]
    }
  },
  "filter": {
    "synonym": {
      "type": "synonym",
      "synonyms_path": "synonyms.txt",
      "updateable": true
    }
  }
}
```

シノニム辞書を S3 に登録し、パッケージとしてドメインに関連付けし、OpenSearch から参照できるようにできます.

https://docs.aws.amazon.com/ja_jp/opensearch-service/latest/developerguide/custom-packages.html

このファイルをアナライザーの synonyms_path に設定すると使えるようになります。

シノニムは １ワードでも複数ワードでも問題ありません.
phrase マッチでも シノニムで検索することが可能です.

## リファレンス

https://www.elastic.co/jp/blog/boosting-the-power-of-elasticsearch-with-synonyms

https://techblog.zozo.com/entry/search-performance-improvement

https://dev.classmethod.jp/articles/synonym-in-amazon-elasticsearch-service/

https://blog.johtani.info/blog/2020/04/27/note-updating-dictionary/

https://www.opensearchserver.com/documentation/faq/querying/how_to_use_synonyms.md
