# Golang
- 変数・メソッドのスコープ
    - 先頭が大文字: 他パッケージから参照可能
    - 先頭が小文字: 他パッケージから参照不可
- 1回だけの処理を行うための方法
    - `NewHoge` という関数を定義
    - `Sync.once` を使用
        - 複数の goroutine が呼び出しても実行されるのは1度だけ

- `.env` のパス指定
```
import "github.com/joho/godotenv"

err := godotenv.Load(".env")
if err != nil {
	log.Fatal("Error loading .env file")
}
```

## Research
- シグネチャ
- `chan`


