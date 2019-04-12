# Golang
- 1回だけの処理を行うための方法
    - `NewHoge` という関数を定義
    - `Sync.once` を使用
        - 複数の goroutine が呼び出しても実行されるのは1度だけ

## Research
- シグネチャ