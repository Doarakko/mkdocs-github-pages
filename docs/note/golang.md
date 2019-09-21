# Golang

- 変数・メソッドのスコープ
  - 先頭が大文字: 他パッケージから参照可能
  - 先頭が小文字: 他パッケージから参照不可
- 1 回だけの処理を行うための方法

  - `NewHoge` という関数を定義
  - `Sync.once` を使用
    - 複数の goroutine が呼び出しても実行されるのは 1 度だけ

- `.env` のパス指定

```
import "github.com/joho/godotenv"

err := godotenv.Load(".env")
if err != nil {
	log.Fatal("Error loading .env file")
}
```

- `time` 型を文字列に変換

```
beginAt := time.Now().Format(time.RFC3339)
endAt := time.Now().Format(time.RFC3339)
```

## [A Tour of Go](https://tour.golang.org/list)

### Basics

#### Packages, variables, and functions

- rand 関数シード確認: `rand.Seed`
- Exported name

  - begin capital letter

- 関数の引数が同じタイプが複数の場合

```
func add(x, y int) int {
    return x + y
}
```

- 返り値複数の関数

```
func swap(x, y string) (string, string) {
    return y, x
}
```

- named return value
  - 引数に名前をつけられる
  - return に変数指定しなくて OK
  - 長い関数では可読性下がるので控える

```

func split(sum int) (x, y int) {
    x = sum * 4 / 9
    y = sum - x
    return
}
```

- zero value

```
int: 0
float64: 0
bool: false
string: ""
```

- 型変換
  - Go では C と違い明示的な型変換が必須

```
i := 42
f := float64(i)
u := uint(f)
```

- 型推論

```
func main() {
   v := "hello"
   fmt.Printf("v is of type %T\n", v)
}
```

#### Flow control statements: for, if, else, switch and defer

- loop

  - Go のループは for 文のみ
  - {} は必須

- fmt.Sprint

  - フォーマットした結果を文字列で返す

- if 文
  - 条件式の前に statement 入れられる

```
func pow(x, n, lim float64) float64 {
    if v:= math.Pow(x, n); v < lim{
        return v
    }
    return lim
}
```

- switch 文
  - 自動で break 文が入る
  - condition なし = if-the-else

```
func main()  {
    t := time.Now()
    switch {
    case t.Hour() < 12:
        fmt.Println("Good morning")
    case t.Hour() < 17:
        fmt.Println("afternoon")
    default:
        fmt.Println("evening")
    }
}
```

- defer 文
  - 関数が return 後に実行
  - stack

```
func main() {
    fmt.Println("counting")
    for i := 0; i < 5; i++ {
    	defer fmt.Println(i)
    }
    fmt.Println("done")
}
```

```
counting
done
4
3
2
1
0
```

#### More types: structs, slice, and maps

- ポインタ
  - Go にはポインタ演算なし
  - 構造体のポインタ表記面倒なので以下で OK

```
(*p).X equal p.X
```

- リテラル

```
var(
    v1 = Vertex{1, 2}
    v2 = Vertex{Y: 1}
    v3 = Vertex{}
    p = &Vertex{1, 2}
)

func  main()  {
    fmt.Println(v1, p, v2, v3)
    fmt.Println(v1, *p, v2, v3)
}
```

```
{1 2} &{1 2} {0 1} {0 0}
{1 2} {1 2} {0 1} {0 0}
```

- Go の配列はリサイズできない

  - リサイズしたい際には配列ではなく slice を使用

- スライス
  - 参照渡し
  - インデックス注意
  - a[i:j]
    - i から j - 1 番目の要素
  - - [Go Slices: usage and internals](https://blog.golang.org/go-slices-usage-and-internals)

```
primes := [6]int{2, 3, 5, 7, 11, 13}
var s []int = primes[1:4]
fmt.Println(s)
```

```
[3 5 7]
```

- cap(s)

  - 配列の容量
  - 最初の要素からの数
  - `basics/slice-len-cap.go`

- `nil`

  - cap(s) = 0

- `range`

```
// skip index or value
for i, _ := range pow
for _, value := range pow

// index only
for i := range pow
```

### Methods and interfaces

- `v` がポインタでなかった場合は Pointer receiver が自動的に呼ばれる

```
func (v *Vertex) Scale(f float64) {
	v.X = v.X * f
	v.Y = v.Y * f
}

func main() {
    v := Vertex{3, 4}
	v.Scale(2)
}
```

-

```
v := &Vertex{3, 4}
fmt.Printf("v: %v\n", v)
fmt.Printf("+v: %+v\n", v)

[Output]
v: &{3 4}
+v: &{X:15 Y:20}
```

- `interface{}`

  - 空のインターフェース
  - 型はなんでも OK

- 型チェック

```
s, ok := i.(string)
fmt.Println(s, ok)

[Output]
hello true
```

- [`fmt.Sprintf`](https://golang.org/pkg/fmt/#Sprintf)
  - 文字列返す

### Research

- 「<<」 / 「>>」: [Golang のシフト演算](http://ubur1114.hatenablog.com/entry/2017/08/05/204723)

- fmt.Sprint

- sqrt: [Newton's method
  ](https://en.wikipedia.org/wiki/Newton%27s_method)

```
z -= (z * z - x) / (2 * z)
```

- runtime.GOOS
- defer 文: [Defer, Panic, and Recover](https://blog.golang.org/defer-panic-and-recover)

- Function closures
- receiver
