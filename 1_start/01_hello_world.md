# Анхны Go програм

Аль ч компютерийн хэл нь компютер болон програм зохиогчийн хооронд “гүүр” болох зориулалттай байдаг. Програм зохиогч өөрийн санааг текст засварлагч дээр бичиж файлд хадгална, энэ файлыг _эх файл_ гэнэ. Эх файлыг Go хөрвүүлэгчээр машины код уруу хувиргана. Ингээд компютер түүнийг ойлгож ажиллуулна.

Хамгийн анхны жишээ болгон Hello World програм бичиж үзэцгээе.

```go
package main
import "fmt"

// анхны програм
func main() {
    fmt.Println("Hello, World!")
}
```

[![Run in Playground](res/run.svg)](https://play.golang.org/p/RBSYyNyyVba)

**Алхам-1**. Дээрх эх кодыг текст засварлагч дээр бичээд `hello.go` нэртэй файл болгон хадгална.

Програмын эх кодыг диск төхөөрөмж дээр тодорхой хавтсанд цэгцтэй хадгалвал тохиромжтой байдаг. `src` нэртэй хавтсанд бүх програмаа хадгалж болох юм. Хавтас үүсгэхдээ терминал дээр дараах  командыг бичнэ:

```sh
$ mkdir src
```

Ингээд эх файлаа дотор нь хадгалах хэрэгтэй.

**Алхам-2**. Одоо эх кодоо машины хэл рүү хөрвүүлэх хэрэгтэй. Учир нь дээрх Go хэл дээр бичсэн кодыг машин ойлгохгүй.

```sh
$ go build hello.go
```

Програм амжилттай хөрвүүлэгдсэн бол `hello` \(Windows дээр hello.exe\) нэртэй файл үүссэн байх болно.

Хөрвүүлэлтийн дотоод процессыг дэлгэрэнгүй харахыг хүсвэл `go build` команд дээр `-x` параметрийг нэмж ажиллуулах хэрэгтэй.

Go хөрвүүлэгчээс үүссэн машины кодон дотор програмыг ажиллахад дэмжлэг үзүүлэх, санах ойг удирдах, чөлөөлөх нэмэлт код орсон байдаг. Тиймээс голдуу том хэмжээтэй машины код үүсдэг.

Мөн ямар үйлдлийн систем дээр ажиллаж байгаагаас үл хамааран Go хөрвүүлэгчээр өөр өөр үйлдлийн системд зориулсан програм үүсгэх боломжтой.

Linux үйлдлийн системд зориулж хөрвүүлэх:

```sh
$ GOOS=linux go build hello.go
```

Windows үйлдлийн системд зориулж хөрвүүлэх:

```sh
$ GOOS=windows go build hello.go
```

MacOS X үйлдлийн системд зориулж хөрвүүлэх:

```sh
$ GOOS=darwing go build hello.go
```

**Алхам-3**. Хөрвүүлээд програм маань бэлэн болсон учраас дараах байдлаар ажиллуулж болно.

Linux, Unix, Mac OSX төрлийн үйлдлийн систем дээр:

```sh
$ ./hello
```

Windows  дээр:

```sh
C:\> hello.exe
```

гэж бичээд ENTER товч дарна.

Програмын үр дүнд дэлгэц дээр "Hello World" гэсэн мэдэгдэл хэвлэгдэх ёстой.