# Heroku
## Requirements
- heroku/7.19.4


- アプリケーション作成
    - アプリケーション名を指定しない場合はランダム
```
$ heroku create <app name>
```

- ログイン
```
$ heroku login
```

- Push
```
$ git push heroku master
```

- スケジューラ追加
    - 設定はダッシュボード上で行う
```
$ heroku addons:create scheduler:standard
```

- 環境変数確認
```
$ heroku config
```

- アプリケーション名変更
```
$ heroku apps:rename <newname> --app <oldname>
$ git remote rm heroku
$ heroku git:remote -a <newname>
```


- アドオン確認
```
$ heroku addons
```

## Postgres
- 詳細情報確認
```
$ heroku pg -a <app name>
```
- SQL ファイルを流す
```
$ heroku pg:psql --app <app name> < <file path>
```

- Reset database
```
$ heroku pg:reset DATABASE
```

## Reference
- [Renaming Apps from the CLI](https://devcenter.heroku.com/articles/renaming-apps)
- [Heroku コマンド・設定 メモメモ](https://qiita.com/pugiemonn/items/0e69b7a29a384b356e65)
- [how to execute a .sql script on heroku?](https://stackoverflow.com/questions/15237366/how-to-execute-a-sql-script-on-heroku)