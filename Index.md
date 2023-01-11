# インデックス

インデックスの作成に 設定 と マッピング を行います

## 設定

設定では

- アナライザ
- シャードの数

などの指定をします.

**Note**
インデックスの設定は、基本 動的に変更できません.
すでに存在する設定を変更しようとすると `Can't update non dynamic settings` とエラーになります.
アナライザの追加においてはエラーにならず、`ignoring non dynamic index level settings for open indices: `というワーニングが表示されます.

すでに存在する設定を変更する場合には、インデックスをクローズしてから変更し、再度オープンする必要があります.
追加の場合は、インデックスをクローズし、再度オープンすると変更が反映されます.

## マッピング

マッピングでは インデックスの構造を定義します

インデックスのフィールドとその型を定義し、使用するアナライザーを定義します

フィールドの方には keyword、text、integer などが使用することができます.

特殊な型として、以下が使用することができます.

- マルチフィールド

  多言語のデータが含まれるデータを格納するのに使用します.

- Nested フィールド

  タグオブジェクトなどの情報を保持するのに使用します.

## 作成方法

以下の API で作成できます.

```json
PUT /{index name}
{
    "settings": {
        "number_of_shards": 1
    },
    "mappings": {
        "properties": {
            "fields1": { "type": "text" }
        }
    }
}
```

**インデックステンプレート**

インデックステンプレートを使用して、インデックスの作成を効率化することが可能です.

```
PUT _index_template/template_1
{
    "index_patterns": ["te*", "bar*"],
    "template": {}
}
```

## 補足

ElasticSearch は スキーマレスなので、マッピングは必須ではありません.

スキーマレスでも 実際には アナライザを適切に使用するには スキーマが必要で、最適なパフォーマンスを得るには Schema on Write で 利用する必要があります.

https://www.elastic.co/jp/blog/schema-on-write-vs-schema-on-read

ドキュメントによって、スキーマが異なることが可能になっているので、検索フィールドがインデックスに存在しなくてもエラーにはなりません.

## リファレンス

インデックスの作成について

https://blog.johtani.info/blog/2020/04/27/note-updating-dictionary/
https://gist.github.com/lukas-vlcek/5143799

多言語

https://www.elastic.co/guide/en/elasticsearch/guide/master/mixed-lang-fields.html

https://kazu.tv/blog/2016/12/03/i18n-elasticsearch-part-2/

https://dev.classmethod.jp/articles/elasticsearch-starter5/

```
GET _cat/indices/m*?v&h=index,store.size&s=index:asc&bytes=mb
```
