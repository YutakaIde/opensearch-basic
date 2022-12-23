# インデックス

インデックスには、設定とマッピングを定義します.

## インデックスに対する設定

アナライザ や シャードの数を定義します

注意.
インデックスの設定は、基本 動的に変更できません.
すでに存在する設定を変更しようとすると Can't update non dynamic settings とエラーになります.
アナライザの追加においてはエラーにならないようですが、ignoring non dynamic index level settings for open indices: というワーニングが表示されます.

すでに存在する設定を変更する場合には、インデックスをクローズしてから変更し、再度オープンする必要があります.
追加の場合は、インデックスをクローズし、再度オープンすると変更が反映されます.

以下を参考にしてください.
https://blog.johtani.info/blog/2020/04/27/note-updating-dictionary/
https://gist.github.com/lukas-vlcek/5143799

## インデックスのマッピング (構造)

インデックスの構造を定義します
