# Text analysis

## analyzer

### アナライザが使われるタイミング

検索とインデックスのそれぞれで適用される

### アナライザの順番

以下の順番で分析される

- Character filters
  文字ごとの特別な処置など
- Tokenizer
  ngram など
- Token filters
  ステミングなど

### インデックスごとにアナライザを指定できる
