# Git
### ブランチ
- ブランチ一覧表示
```
$ git branch
```
- 新規ブランチ作成
```
$ git branch -b <branch name>
```

- ブランチ切替
```
$ git checkout <branch name>
```

- ブランチ名変更
```
$ git branch -m <src name> <dst name>
```

- ブランチ削除
```
$ git branch --delete <branch name>
```

### etc
- キャッシュ削除
    - `.gitignore` が適用されない場合に実行
```
$ git rm -r --cached .
```
- ログの確認
    - 終了する場合は `q` を押す
```
$ git log
```

### コミット取り消し
- ワークディレクトリ取り消し
```
$ git reset --hard HEAD^
```
- ワークディレクトリ変更なし
```
$ git reset --soft HEAD^
```


### diff
- add 前
```
$ git diff
$ git diff <file path>
```
- add 後
```
$ git diff --cached
$ git diff --cached <file path>
```

## Reference
- [.gitignoreに記載したのに反映されない件](https://qiita.com/fuwamaki/items/3ed021163e50beab7154)
- [[Git]コミットの取り消し、打ち消し、上書き](https://qiita.com/shuntaro_tamura/items/06281261d893acf049ed)
- [忘れやすい人のための git diff チートシート](https://qiita.com/shibukk/items/8c9362a5bd399b9c56be)
- [さっきの取り消したい！って時のGitコマンドまとめ](https://qiita.com/kansiho/items/2bacecdb95d752cb38b7)