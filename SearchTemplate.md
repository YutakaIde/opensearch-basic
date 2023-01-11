## search template

登録されている search template の確認方法

```
GET _cluster/state?filter_path=metadata.stored_scripts
```

```json
POST _render/template
{
  "source": {
    "query": {}
  },
  "params": {}
}
```

```
POST _render/template
{
  "id": "play_search_template",
  "params": {
    "play_name": "Henry IV"
  }
}
```

## リファレンス

https://opensearch.org/docs/1.3/opensearch/search-template/
