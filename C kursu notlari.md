# C Kursu Notlari

## 17 Yorum Satiri - Fonksiyon Definition, Declaration - Makrolara Giris

- Nested Looplarda loopun kapali parantezinin sonuna yorum olarak hangi loopa ait oldugu yazilabilir.
- Name-Lookup: ilgili degiskenin belirli aralikta definition’inin taranmasi.
- Fonksiyonun tanimi linkeri ilgilendiren, derlemede linker asamasinda hata verdiren bir durumdur.
- Fonksiyon bildirimi(fonksiyon declaration) fonksiyondan once gelebilir, derleyicinin parameter vs hatasini kontrol eder. Fonksiyon definition derleyici tarafindan bilinmez, linker bilir onu.
- Derleyici declaration gorunce tur donusumunu yapiyor.
- Cagirdigimiz her fonksiyon icin derleyici ya definition yada declaration gormesi gerekir.
- Declarationlar include komutu ile eklenen h dosyasinda yapilir. Bazen de direk definitionlar yapilir.
- Declarationda isim vermek zorunlu degil ama definition’da zorunlu.
- C++ da (void) ve () ayni iken, C’de () bu parameter degiskeninin oldugunu fakat bilinmedigini soyluyor. Bu yuzden () yerine (void) kullanmaliyiz.
- Function redeclaration C’de mumkundur hata vermez.
- DLL Dynamic Link Library.
- C’de static tanimlanan fonksiyonlar sadece o .c de cagirilacagi icin .h’a declaration yazilmaz
- Diyezle baslayan satirlarin hepsi onislemci komutudur, derleyiciye dogrudan verilmez
- Conditional compiling onislemci komutlari ile saglanir.
- #Include: ismi verilen dosya icindeki bildirimlerin .c dosyasina yapisitirilmasi
- Include<> : default directoryde arar- ide ya da compiler tarafindan belirlenen yer- include directorysi – hazir baslik dosyalari standard baslik dosyalari vs
- Include” ” : kaynak dosyanin bulundugu dizinde arar, bulamazsa standard include directory arar
- Include baslik dosyasi icinde karsilastigi tum on islemci komutlarini calistirir, geri kalan c kodlarini direk kopyalar ve yazildigi yere yapistirir.

## 18 Makrolar - Define

- #define ile tanitilan isimlere macro denir. En temel isim bu. Object-like macro functional macro symbolic constant manifest constant gibi alt isimleri de var.
- Soyle bir define olabilir #define forever for (;;)
- Stdbool.h bool true false’i vs icerir.
- Embedded systemde macrolar adresleri tutmak icin de kullanir.
- Fonksiyonel makroda makro isminden sonra  hemen parantez tokeninin gelmesi gerekiyor.
- Islem onceligi durumundan kacmak icin fonksiyon makrolarinda degiskeni () icinde yazmaktayiz
    ```
    #define ISLEAP(x)  ((y) % 4 == 0 && ((y) % 100 || (y) % 400 == 0)) 
    ```
- Kodu kucuk ve sik cagirilan fonksiyonlar cagirildiginda fonksiyon yazmak maliyeti daha fazladir. Bu durumda makrolar daha anlamlidir(fonksiyonel makrolar)
- Fonksiyonel makronun icine baska bir makro yazilabilir.

## 19 Makrolar - Preprocessor Expressions

- Fonksiyonel makro kodun fonksiyona gidip return etmesinden cok daha hizli calisir.
- Makrolarin icine fonksiyonlar da yazilabilir, makro sadece yer degistirme olarak gorulmelidir.
- Makrolar statement iceriyorsa sonuna ; koymak gerekir.
- Makrolari kullanirsak fonksiyon pointeri gibi bir durum kalmiyor.
- Makrolarin ciktisi olarak tanimsiz ifadeler olusabilir - kodlama hatasina musait.
- #a onu makroda kullanilirsa a'yi cift tirnak icine alir. Haliyle bu asagidaki iki komut ayni anlama gelir:
    ```
    #define iprint(x) pritnf("%d\n", x)
    #define iprint(x) printf(#x)
    ```
- Kosullu derleme makrolari:
    ```
    #undef
    #if
    #else
    #elif
    #endif
    #ifdef
    #ifndef
    ```
- Farkli donanimlar icin bazi komutlar derleyiciye verilmeli bazi komutlar ve bildirimler verilmemeli bu yuzden bu makrolarla hangi bildirimlerin derleyiciye verilecegini secmemizi saglar.
- Farkli donanimin yaninda farkli os farkli dil versiyon ve lokalizasyon da bu makrolarin kullanim sebepleri arasinda gorulebilir.
- Bu ifadelere preprocessor expressions deniyor.
- On islemcinin gormeyecegi ifadeler silik sekilde yazilarak gosterilir.
- Bu #if logic operasyonlari da icerebilir. Derleyici ile ayni mantik calismakta. **Ancak burada degisken kullanilamaz.** Degisken derleyicinin oldugu yerde kullanilabilir
- Makro programa dahil olmadigi icin program tarafindan degistirilemez
- `defined()` bir makronun tanimli olup olmadigina bakar
- Yapi bildirimi gibi bazi bildirimlerin ikinci kez gorulmesi syntax hatasidir.
- **Multiple Inclusion Guard:** Bildirimin tekrarlanmasini engellemek istiyoruz, cunku derleyici birden fazla gorurse bu bildirimi syntax hatasina sebep oluyor. Bunu engellemek icin kullanilan bir metod.
- Bir baslik dosyasinin birden fazla kez dahil edilmesini engelleyen idiomatic yapidir. `#ifndef`, `#define` ve `#endif` kullanilarak yapilir.
    ```
    #ifndef NUTILITY_H
    #define NUTILITY_H
    ...
    typedef int Word;
    ...
    #endif
    ```
- `#pragma once` da bu isi yapmak icin gelistirilmistir ancak butun derleyiciler tarafindan desteklenmemektedir, **standart degildir**
- `#ifndef` yerine `#if !defined(NUTILY_H)` ayni seydir.
- `#undef` bir makronun tanimini ortadan kaldirir, makroyu tanimsiz hale getirir.

## 20 Makrolar - Switch Case

- Makroyu yeniden tanimlamak icin once onu `#undef` etmek gerekmektedir.
- predefined symbolic constant(ontanimli sembolik sabitler): bir define komutu ile tanimlanmamis olmalarini karsin onislemci tarafindan tanimli kabul edilen, dil tarafindan onceden belirlenmis onislemci isimleri. __ ile baslarlar. `__LINE__`,`__FILE__`, `__DATE__`,  `__TIME__` bunlar, bulunduklari yerin degerlerini alirlar, ornegin `__LINE__`makrosununu kullanildigi yerde line makrosunun oldugu satir numarasi icersine yazilir.
- bunun disinda `__cplusplus` gibi yapilar da kullanilabilir, ornegin:
    ```
    #ifndef __cplusplus
        #error this program only builded by C++ Compiler
    #endif
    ```
-  #pragma standart bir on islemci komutu ama hangi anlami yuklenecegi derleyiciler tarafindan belirlenmistir.
- `#pragma warning(disable: 4244)`: 4244 numarali warningin verilmesini engeller. Derleyiciye bagli bir durumdur.
- Makronun icinde ; olabilir, fonksiyonel makro parantez icinde yazilmis olabilir, bu parantez oncelik problemine cozum olarak koyulmus olsa dahi burada da dikkat edilmelidir.
- Fonksiyonel makrolarda if while gibi conditional statementler yazilabilir.
- Switch deyiminin govdesinde n tane case deyimi olabilir, 0 da olabilir.
- Switch icindeki degere esit olan Case'e gore programin akisi oraya yonlenir ve oradan devam eder.
- case label'lari ile go to label'lari arasinda lojik olarak hicbir fark yoktur.
- case labellari, break deyimi ile sonlanmalidir. ayrica bir default labeli da yazilmalidir.
- case ifadesi bir sabit ifadesi ve tamsayi olmak zorundadir.
- else if merdivenleri sadece tam sayi degeri esitligiyle yazilmaz(x == 7), bu yuzden else-if in scopu daha genistir.
- return degeri enum olan fonksiyonlarda switch case kullanilmasi daha derli toplu gozutmesini saglar.
- switch case'de jump table'lar kullanildigi icin else if merdivenine gore optimizasyon sansi daha yuksektir.
- switch case yapilarinda genelde case ifadeleri ya makro ya da enum secilir.
- olusma sikligi daha yuksek olan case'leri yukariya yazmakta fayda var.
- case'lerin icinde uzun uzun islem yapmak guzel bir kod aliskanligi degildir, bunun icin bu statementlar, bir fonksiyonda toplanip fonksiyon cagirilabilir.
- bazen case'lerden sonra asagidaki satirin da calismasi gerekir, bu durumda `case 1: foo();//fallthrough` diye comment olarak belirtilmelidir.
- fallthrough ornegi
    ```
    int day_of_year(int d, int m, int y)
    {
        int sum = d;

        switch(m - 1){
            case 11: sum += 30; //fallthrough
            case 10: sum += 31; //fallthrough
            case 9: sum += 30; //fallthrough
            case 8: sum += 31; //fallthrough
            case 7: sum += 31; //fallthrough
            case 6: sum += 30; //fallthrough
            case 5: sum += 31; //fallthrough
            case 4: sum += 30; //fallthrough
            case 3: sum += 31; //fallthrough
            case 2: isleap(y) ? 29 : 28; //fallthrough
            case 1: sum += 31; //fallthrough
        }

        return sum;
    }
    ```
    
## 21 goto - Type Conversions(Tur Donusumleri)

- goto statement, iki farkli sekilde yapilabilir: long jump ve local jump(near jump)
- long jump baska bir fonksiyondaki frame stackine giden goto statementtir.
- local jump ayni fonksiyon icerisindeki bir frame stackine gidilmesidir.
- C'de sadece local jump mumkundur. Sadece fonksiyon icerisinde kullaniliyor.
- Programin akisini gotolar ile yapmak programin test edilmesini zorlastiriyor, bu yuzden insanlar kullanmamaya yatkin. Ancak bazen tek cozum o oluyor.
- goto bir labeldir(etiket). Labellar `labelname:` seklinde tanimlanir. Ve her label muhakkak bir statement icermelidir.
- goto labellari function scope denen ozel bir tanim araligina sahiptir. Fonksiyon icindeki her alanda kullanilabilir.
- goto syntaxi:
  ```
  goto label;

  label:
    //statement;  
  ```
- goto kontrol deyimi ile fonksiyonda daha yukaridaki bir deyime programin akisi yonlendirilmemelidir.
- cok ic ice tasarlanan dongulerde butun donguden cikmak icin goto kullanilabilir. goto kullanilmaz ise flag set edilip bu flagin degerine gore breakler calistirilir, bu durum goto kullanmaktan cok daha komplikedir.
```
for ...{
    //statement
    while...{
        //statement
        for ...{
            //statement
            if ...{
                //statement
                goto out;
                  }
               }
            }
        }
out:
    //statement       
```
- Type Conversion bir ifadenin dogrudan degil farkli bir turde ifade edilerek o turde kullanilmasina verilen addir.
- implicit type conversion: implicit ortulu demek ustu kapali bir sekilde tur donusumu yapilmasidir. Implicit donusum icin bir talimat verilmiyor, derleyici dilin kurallari geregi tur donusumunu otomati yapiyor.Mesela bir int val ile double val ile toplama islemi yaparsak int val bu toplama islemnine double value olarak girer. Bunu derleyici otomatik olarak yapar.
- explicit type conversion: burada acikca derleyiciye bir operator tarafindan turu donusturmesi gerektigi soyleniyor, bu operatorun adi **type-cast** operatorudur.
- implicit type conversion, usual arithmetic conversion'da operatorlerin kullanilmasi sonucu otomatik olarak yapilan ortulu donusumlerdir. Operatorler = +->< vs
- bir diger implicit type conversion, atama esnasinda yapilan donusumlerdir. Atama veya kopyalama yapilirken tur otomatik olarak degistirilir. 
    - `int ival = 3.4` degerinin 3 olarak alinmasi gibi.
    - Fonksiyon cagrisindaki parametre gonderilen parametreden farkliysa yine otomatik olarak degistirilmesi gibi.
    - `return ival;` statementinda da otomatik olarak degistirilir.

1. saatte kaldim. 
