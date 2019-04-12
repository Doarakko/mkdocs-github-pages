# GitHub
- リポジトリ名変更
```
$ open .git/config
```
```
[remote "origin"]
	url = https://github.com/Doarakko/<new repository name>
```

## GitHub Pages
- ユーザページ(`username.github.io`)では、Source を `master branch` 以外に設定できない
- プロジェクトページでは以下のブランチを設定可能
    - `master`
    - `gh-pages`

## Reference
- [User, Organization, and Project Pages](https://help.github.com/articles/user-organization-and-project-pages/)
- [GitHubのリポジトリ名変更方法](https://qiita.com/hisurga/items/583e8dbe4970bc8c25c8)