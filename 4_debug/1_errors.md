# Алдааны төрлүүд

Програмд төрөл бүрийн алдаанууд гарч байдаг. Програм хэдийгээр логикын хувьд бүрэн зөв хийгдсэн ч гадаад хүчин зүйлээс хамааран алдаа гарах эрсдэл байсаар байдаг. Эдгээрийг рантайм алдаа, файл системийн алдаа, өгөгдлийн сангийн алдаа, сүлжээ, холболтын алдаа гэж ангилж болох юм.

**Рантайм алдаа** гэдэг нь програм ажиллаж байх үед гарч байгаа алдааг хэлнэ. Рантайм алдаа гарсан үед програмын ажиллагаа шууд зогсдог. Тиймээс рантайм алдааг олох, засахад харьцангуй хялбар байдаг. Гэхдээ бодит хэрэглээнд нэвтэрсэн програмд рантайм алдаа гарах нь ихээхэн хор уршигтай байдаг.

Зарим рантайм алдаануудыг дурдвал:
* *Segmentation Violation*. Програм зөвршөөрөлгүй санах ойн мужид (буруу хаягтай заагчаар дамжуулан) хандалт хийхийг оролдох үед үүснэ.
* *Stack Overflow*. Програмд хэтэрхий олон тооны локаль хувьсагчид ашигласан үед энэ алдаа гарна. Ихэвчлэн маш том массивыг локаль байдлаар зарлах, эсвэл төгсгөлгүй рекурсив дуудалтын үед тохиолддог.
* *Divide by Zero*. Тоог 0-д хуваах алдаа.

Рантайм алдаатай жишээ програм үзэе.

```go
package main

func main() {
    i:=1; j:=0;
    println("Хуваахын өмнө...");
    i = i / j;  /* 0-д хуваах алдаа */
    println("Дараа нь")
}
```

Энэ програмыг ажиллуулахад "Divide by Zero" рантайм алдаа гарна. Ө.х `i = i / j` заавар дээр `j=0` байх учраас рантайм алдаа гарч програм тасрана.

```sh
$ go run runtime_error.go
Хуваахын өмнө...
panic: runtime error: integer divide by zero
[signal 0x8 code=0x1 addr=0x400c5d pc=0x400c5d]

goroutine 1 [running]:
runtime.panic(0x421520, 0x4572bd)
	/go/src/pkg/runtime/panic.c:266 +0xb6
main.main()
	/go-book/src/runtime_error.go:6 +0x5d
exit status 2
```

**Файл системийн алдаа** нь байхгүй эсвэл зөвшөөрөгдөөгүй файлд програм хандах, бичихийг оролдох үед үүсдэг.

**Өгөгдлийн сангийн алдаа**: Үүнд өгөгдлийн серверээс холболт тасрах, нэвтрэх эрх буруу, өгөгдөлтэй ажиллах команд буруу, өгөгдлийн уялдаа алдагдах, өгөгдөл давхардах зэрэг багтана.

**Сүлжээний алдаа**: сүлжээний холболт тасрахад төгсгөлийн цэгүүд дээр ажиллаж байгаа програмуудад харилцан адилгүй нөлөөлж байдаг. Жишээ нь клиент талаас санаачлан холболтыг хүчээр таслахад клиент дээр алдаа гарахгүй боловч сервер талын програмд урьдчилан тооцоогүй нөхцөл байдал үүсэж болно. Тиймээс сүлжээний орчны програмын алдааг шинжлэхэд нэлээд төвөгтэй байдаг.

**Үйлдлийн системийн алдаа**: үйлдлийн системийн санах ой, CPU, дискийн багтаамж зэрэг нөөц хүрэлцэхгүй байх тохиолдлуудыг хэлнэ. Үйлдлийн системийн алдаа гарсан үед түүнээс үүдээд олон дагавар алдаанууд гарч байдаг.