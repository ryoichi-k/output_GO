# go

Goのプログラムは、パッケージ( package )で構成されます。

プログラムは main パッケージから開始されます。
規約で、パッケージ名はインポートパスの最後の要素と同じ名前になります。 例えば、インポートパスが "math/rand" のパッケージは、 package rand ステートメントで始まるファイル群で構成します。

```go
//factoredインポートステートメント
import (
	"fmt"
	"math"
)

```

```go
func swap(x, y string) (string, string) {
	return y, x
}

//戻り値に名前つける。今回はx,y
func split(sum int) (x, y int) {
	x = sum * 4 / 9
	y = sum - x
	return
}
```


変数var
var c, python, java bool

※c,python,java変数をすべてbool型で宣言

変数での暗黙的な型宣言
関数の中では、 var 宣言の代わりに、短い := の代入文を使い、暗黙的な型宣言ができます。

なお、関数の外では、キーワードではじまる宣言( var, func, など)が必要で、 := での暗黙的な宣言は利用できません。
整数の型を使うための特別な理由がない限り、整数の変数が必要な場合は int を使うようにしましょう。

変数を初期値なしで宣言するとゼロ値( zero value )が与えられます。
ゼロ値は型によって以下のように与えられます:

数値型(int,floatなど): 0
bool型: false
string型: "" (空文字列( empty string ))

定数( constant )は、 const キーワードを使って変数と同じように宣言します。
※定数は := を使って宣言できません。
const Pi = 3.14
const World = "世界"


### for

```go
//基本的に、 for ループはセミコロン ; で3つの部分に分かれています
func main() {
	sum := 0
	for i := 0; i < 10; i++ {
		sum += i
	}
	fmt.Println(sum)
}

//ForはGOではwhileにもなる
//セミコロン(;)を省略することもできます。
//↓多言語で言うwhile
func main() {
	sum := 1
	for sum < 1000 {
		sum += sum
	}
	fmt.Println(sum)
}

//無限ループ
//ループ条件を省略すれば、無限ループ( infinite loop )になります。
func main() {
	for {
	}
}
```

### if
```go
if x < 0 {
	return sqrt(-x) + "i"
}
```
### switch
```go
func main() {
	fmt.Print("Go runs on ")
	switch os := runtime.GOOS; os {
	case "darwin":
		fmt.Println("OS X.")
	case "linux":
		fmt.Println("Linux.")
	default:
		// freebsd, openbsd,
		// plan9, windows...
		fmt.Printf("%s.\n", os)
	}
}
```
### defer
defer ステートメントは、 defer へ渡した関数の実行を、呼び出し元の関数の終わり(returnする)まで遅延させるものです。

defer へ渡した関数の引数は、すぐに評価されますが、その関数自体は呼び出し元の関数がreturnするまで実行されません。

```go
func main() {
	defer fmt.Println("world")

	fmt.Println("hello")
}


//実行結果
//hello
//world
```
