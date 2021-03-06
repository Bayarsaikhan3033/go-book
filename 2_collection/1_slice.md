# Массив \(slice\)

Массив бол ижил төрлийн, тодорхой урттай, дугаарлагдсан өгөгдлийн дараалал юм. Санах ойд энэ бүтэц нь үргэлжилсэн хайрцгууд болж байрладаг. Нэг хайрцгийг нь элемент гэж нэрлэнэ. Элементийн тоог массивын хэмжээ гэнэ.

Go хэлэнд массив зарлалт нь дараах байдалтай:

```go
/* бүхэл тоон массив */
var data_list []int
```

эсвэл

```go
data_list:=[3]{1, 2, 3}
```

Дээрх жишээнд 3 элемент бүхий `data_list` массив үүсгэсэн байна. `data_list[0]`, `data_list[1]`, `data_list[2]` нь тусдаа хувьсагчид гэж төсөөлж болно. Массивын нэг элементэд хандахад массивын нэрний ард тухайн элементийн дугаарыг дөрвөлжин хаалтад `[ ]` бичиж заана. Go хэлэнд энэ дугаарлалтыг `0`-ээс эхэлдэг онцлогтой. Тиймээс дээрх гурван элемент маань `0`, `1`, `2` гэж  дугаарлагдана.

Дараах жишээнд массивт байгаа 5 тооны дунджийг олсон байна.

```go
package main
import "fmt"

func main() {
    data:=[]float32{ 34.0, 27.0, 45.0, 82.0, 22.0 }

    total:= data[0] + data[1] + data[2] + data[3] + data[4]
    average:=  total / 5.0
    fmt.Printf("Нийт %f Дундаж %f\n", total, average)
}
```

Програмын гаралт:

```sh
Нийт 210.000000 Дундаж 42.000000
```

## for давталт

Массив нь дугаарлагдсан цуваа өгөгдөл учраас давтах заавар ашиглахад тохиромжтой байдаг. Тухайлбал давтах зааврыг дараах тохиолдлуудад түгээмэл хэрэглэдэг:

* массивын элементүүдэд эхний утга оноох
* массивын элементүүдийг хэвлэх
* массивын элемент бүрээр давтаж болосвруулалт хийх

Жишээлбэл массивын элементүүдийн дунджийг олох бол дараах  байдлаар `for` зааврыг ашиглаж болно.

```go
for i:=0; i<len(data); i++ {
  total += data[i]
}
average:= total / len(data)
```

## make ба хувьсах урттай массив

`make` функцийг ашиглан хувьсах урттай массив үүсгэж болно. Жишээ нь 5 байтын массив үүсгэх бол дараах байдлаар дуудна:

```go
s := make([]byte, 5)
```

Хувьсах урттай массивын уртыг `len()` функцээр тодорхойлно:

```go
len(s) == 5
```

## Олон хэмжээст массив

Go хэлний массив нь нэг хэмжээстэй буюу шугаман массив байдаг. Хэрэв хоёр хэмжээстэй массив үүсгэх бол дараах байдлаар үүсгэж болно:

```go
var matrix [3][3]float64
```

Хоёр хэмжээст массивын элементэд хандахын тулд дараах тэмдэглэгээг ашиглана:

```go
matrix[1][2] = 10
```

Элементүүдээр гүйхийн тулд хоёр давхар `for` заавар ашиглана:

```go
for y := 0; y < 3; y++ {
  for x := 0; x < 3; x++ {
    matrix[x][y] = 0
  }
}
```

Олон хэмжээст массивын хэмжээ тодорхойгүй \(ажиллах явцад тодорхой болох\) бол `make` ашиглан үүсгэж болно. Жишээ нь `n x n` хэмжээтэй квадрат массив үүсгэе.

```go
a:= make([]int, n)
for i:=0; i<n; i++ {
  a[i] = a([]int, n)
}

// a[x][y] гэж хандаж болно
```

## Функцэд массив дамжуулах

Функцэд хувьсагч дамжуулахад түүний утга нь функцийн стек мужид хуулагддаг тухай бид өмнө үзсэн. Тэгэхлээр том хэмжээтэй массивыг функцэд дамжуулвал их хэмжээний санах ой “иддэг” гэсэн үг юм. Үүнийг шийдэхийн тулд нэг бол массивыг таслаж \(слайс\) дамжуулах эсвэл заагч ашиглаж болно.

Заагчаар дамжуулах:

```go
array := [5]float64{7.0, 8.5, 9.1, 1.1, 3.4}
result := Sum(&array) // хаягийг дамжуулж байна
```

`Sum()` функцэд массивын хаягийг дамжуулж байна, ө.х бүтэн массивыг хуулах шаардлагагүй, зөвхөн массив байрлаж байгаа хаягийг дамжуулж байна гэсэн үг. Тийм учраас дахин дахин хуулж санах ой үрэх шаардлагагүй болно.

Слайс дамжуулах: Слайс нь массивын тодорхой нэг үргэлжилсэн хэсгийг заадаг заагч юм. Үргэжилсэн хэсэг нь массив бүхэлдээ эсвэл түүний дэд хэсэг байж болно.

```go
result := Sum(array[:]) // бүтэн слайс дамжуулж байна
result := Sum(array[:2]) // слайс дамжуулж байна (0,1 элементүүд )
result := Sum(array[2:]) // слайс дамжуулж байна (2,3,4 элементүүд )
```

## Слайс үйлдлүүд

Слайс нь цаад зааж байгаа массивын хэмжээнд тултал сунаж болно. Жишээлбэл хэмжээг 1-ээр нэмэгдүүлэх бол дараах зааврыг бичиж болно:

```go
sl = sl[0:len(sl)+1]
```

Хэрэв цаад массивын хэмжээнээс давсан том хэмжээтэй слайс хэрэгтэй бол шинэ массив үүсгэх хэрэгтэй. Илүү том хэмжээтэй шинэ массив үүсгээд хуучныгаа шинэ том массив уруу хуулах хэрэгтэй.

```go
sl_from := []int{1,2,3}
sl_to := make([]int,10)
n := copy(sl_to, sl_from)
```

Үүнийг мөн өөрөөр `append()` функцээр гүйцэтгэж болно.

```go
sl3 := []int{1,2,3}
sl3 = append(sl3, 4, 5, 6)
```

Дараах хүснэгтэд слайс дээр түгээмэл хэрэглэгддэг үйлдлүүдийг хэрхэн гүйцэтгэхийг харуулсан байна.

| Үйлдэл | Хэрэгжүүлэх |
| --- | --- |
| Хоёр слайс залгах | `a=append(a, b...)` |
| Слайс хуулах | `b = make([]T, len(a)); copy(b, a)` |
| Өгөгдсөн i байрлал дахь элементийг хасах | `a = append(a[:i], a[i+1:]...)` |
| Дэд хэсгийг хасах | `a = append(a[:i], a[j:]...)` |
| Элемент өгөгдсөн байрлалд x элементийг оруулах | `a = append(a[:i], append([]T{x}, a[i:]...)...)` |
| Оройн элементийг авах | `x, a = a[len(a)-1], a[:len(a)-1]` |
| Оройд элемент нэмэх | `a = append(a, x)` |



