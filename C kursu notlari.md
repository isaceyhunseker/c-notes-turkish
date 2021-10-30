# C Kursu Notlari

## 1 Programlamaya Giris - C Dilinin Diger Diller ile Karsilastirilmasi

## 2 C Standartlari - Derleme Surecleri - Diagnostic Mesajlari

## 3 Derleyici Optimizasyonu - Sayi Sistemleri - Kod Layout - Genel Terminoloji

## 4 Genel Terminoloji - Expression Tipleri - Degisken Turleri

## 5 Degisken Tanimlama, Atama Metodlari ve Skoplari - Sentaks Kurallari

## 6 Fonksiyonlara Giris

## 7 Fonksiyonlar - Standart Kutuphanelere Giris

## 8 Standart Kutuphane Fonksiyonlari - Sabit Sayi Gosterimleri (u-l-e) - ASCII Tablosu

## 9 Standart Kutuphane Fonksiyonlari (printf - scanf - getchar)

## 10 putchar - undefined, unspecified, implementation-defined behavior - Operatorler Giris

## 11 Operatorler (Relational - Logical - Bitwise - Assignment - Conditional - Special)

## 12 Operatorler - Operatorlerin Kullanim Teknikleri ve Hataları

## 13 Kontrol Deyimleri(if-for) - Bos Deyimler(Null Statement)

## 14 int turu kullanimlari - return - Dongu Deyimleri(while)

## 15 While - For Giris

## 16 For Dongusu - Genel Dongu Uygulamalari - Yorum Satirlari ve Kod Aciklama Yaklasimlari Giris

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

## 21 goto - Implicit Type Conversions(Tur Donusumleri)

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
- Genel olarak yaklasim veri kaybinin engellemeye yoneliktir.
- Degiskenlerin rank siralamasi asagida verilmistir:
    ```
    1. Grup:
    long double 
    double 
    float
 
    2. Grup:
    long long / unsigned long long 
    long / unsigned long
    int /unsigned int

    ----integral promotion bound----
    3. Grup:
    short 
    char/signed char/ unsigned char 
    _Bool 
    ```
- **1. Grup:** Bu uc operanddan birinin oldugu bir islemde diger operandin rank'i bu operanda donusturulur ve islem bu turde yapilir.
- **2. Grup:** Bu uclude:
  - Rankler ayni ve signedness farkli ise isaretsiz olan ture donusulerek islem yapilir.
  - Rank farkli yuksek olan rank isaretsiz dusuk olan isaretli ise islem isaretsiz yuksek rank'te yapilir.
  - Rankler ve isaretler farkli ve buyuk olan rank isaretli kucuk rank isaretsiz ise, isaretsiz kucuk rank buyuk ranke sigiyorsa buyuk rankteki turde yapilir, eger tutamiyorsa isaretsiz olanin bir buyuk rankinde yapilir.
- **3. Grup:** integral promotion, islemdeki bir ya da iki  degiskenin int alti olmasi durumunda(integral promotion bound) bu degisklerin int'e donusturulup islemin burada yapilmasidir.
- Int to double implicit type-cast ornegi asagida verilmistir:(Usual Aritmetic Conversion)
    ```
    int x = 12
    int y =5

    double dval = 1. * x / y 

    /*
    1. ile carpilmasi x'i double yapti x ile carpilmasi y'yi de double yapti. 

    1. ile carpilmadan double turune esitlenseydi sonuc 2.0000 olacakti.
    ```
- `int x = -1;` ve `unsigned int y = 1` icin `x>y` yazar isek x implicit typecast ile 4294967296 degerine donusur.
- Toplama Carpma gibi islemlerde:
  - isaretli turlerde tasma tanimsiz davranis.
  - isaretli turlerde tasma olmaz - moduler aritmetik devreye girer.
- **Truncation**, buyuk bir rankteki degerin kucuk bir ture donusturulurken buyuk bitlerinin kaybedilmesi olayidir.
- Gercek bir sayidan tamsayiya donusum yapildiginda onlalikli kisim gider, geri kalan kisim tamsayiya sigarsa sorun yoktur, sigmaz ise tanimsiz davranis olur.
- Buyuk turden kucuk ture atama yapilmamalidir, yapilir ise de tur donusturme operatoru ile yapilmasi gerekir.
- Explicit expression = (target type)expr;
    ```
    int x = 10;
    int y = 3;

    double dval = (double)x / y;
    ```

## 27 Pointer Giris

- Pointer adres anlamina gelen bir sozcuk.
- Pointer'lar ikiye ayrilir, Object Pointers ve Function Pointers.
- Nesnenin bellekte nerede oldugu bilgisi, nesnenin adresidir.
- Degiskenin turu ne ise adresi de * tur seklinde gosteriliyor. Haliyle nesne turu kadar adres turu vardir.

    ```
    int *int
    double *double
    ```
- `int *ptr` ptr is a pointer to int...
- Tokenlar arasindaki bosluk karakterlerinin bir etkisi olmadigi icin asterix atomunun nereye bitisik oldugu cok onemli degil.
- * sadece bir sonraki degiskeni niteler: `int *pointer, non-pointer` gibi. Burada ikinci degisken `int` turundedir.
- pointer turlerinin hepsi 4 byte buyuklugundedir, *char'da *long long da ayni buyukluktedir.
- `&` `address of` operatorudur, (adres operatoru)
- `*` `dereferencing / indirection` operatorudur, (icerik operatoru)
- `[ ] index / subscript` operatoru
- `->` `member selection op.` (arrow operator) ok operatoru.
- Ornek kullanim:
    ```
    int x = 10;
    int y = 30;

    int *p = &x;
    p = &y;
    ```
- adres degiskeninin icindeki deger `printf("&x = %p\n", &x)` ya da `printf("ptr = %p\n", ptr)` seklinde yazdirilabilir.
- array decay, array to pointer conversion: Bir dizinin ismi bir ifade icinde kullanildiginda derleyici otomatik olarak o ismi dizinin ilk elemaninin adresine donusturuyor. Asagidaki iki satir bu ozellikten dolayi ayni anlama gelmektedir.
    ``` 
    int *ptr = &a[0];
    int *ptr = a;
    ```
- Bu durum sizeof operatorunde gecerli degildir. Iki degisken farkli iki sonuc uretir.
- Bir nesnenin adresi degistirilemez. Nesne bellekte bir yerden bir yere tasinamaz.
- Derefencing-Indirection Operatoru(*): Icerik operatoru: Adresi verilen degiskenin degerini verir.
- Icerik operatorunun operandi bir adres olmali.
- Bir kodun karmasik gorunmesi icin yapilmasina obfuscation denir, anlami deg ismeden anlasilmaz hale getirilmeye yarar.
- Icerik operandi dizinin ilk elemanini gosterir.Asagidaki kodda a[0] 100 degerini alir.
    ```
    int a[] = {10,20,30,40};
    *a = 999;
    ``` 
- pointee pointerin gosterdigi nesnedir.
    ```
    int *ptr
    ptr pointer
    *ptr pointee
    ```
- C de pointerlar call by reference cagri modelinde kullaniliyor. Bu temel fonksiyonudur.
- scanf call by reference bir fonksiyon cunku aldigi argumanin degerini degistiriyor.

## 28 Pointer - Call by Reference vs Call by Value - Pointer Aritmetigi

- Call by Reference = kendisini cagiran fonksiyona kendisine verilen degeri geri iletmeye calisan fonksiyonlar.
- Bunu yapmanin pointersiz yolu return etmektir. Buna geri donus mekanizmasi denir. Bazi durumlarda pointer kullanmamak daha kolay daha yalin ve pratiktir.
- Ancak komplike senaryolarda call by reference kullanmak daha avantajlidir.
- Bir senaryo: Geri donus degeri fonksiyonun basari degerini donerken pointer ile gecilen arguman da hesaplanan degeri tutuyor olabilir bu durumda yine hesaplanan degeri call by reference ile almak faydalidir.
- Call by reference ile calismak daha az maliyetlidir. Cunku call by value'da return edilen degeri tutan bir degisken ve asil degisken varken diger durumda sadece bir degisken vardir. Kopyalama yapilmaz. Iste bu kopyalama maliyeti call by referenceyi cazip kilmaktadir.
- Degiskenin - Yapinin boyutu ne kadar buyuk olursa olsun, pointerin boyutu degismemektedir. Bu sekilde cikti veren fonksiyonlarin yanina `//out` yazilir, `void foo(T *ptr)//out`;
- Call by Reference ile alinan adreslerdeki degerler sadece input olarak kullanilacaksa fonksiyon declarasyonunda onlarin basina `const` anahtar sozcugu kullanilir. Bu sekilde bu degisken sadece salt okuma amacli kullanilir.
    ``` 
    void add_two_num(const int* pleft, const int* pright, int* presult);   
    
    void func(int *ptr); //output-param
    void foo (const int *ptr); //input-param
    ```
- Input parametresi kucuk boyutlu ise(20 byte sinir olabilir) call by value ile alabilir, eger buyuk bir input ise call by reference ile alinmasi tercih edilmelidir.
- Dizilerin dogrudan call by value olarak fonksiyona gonderilmeleri mumkun degildir. Donus degeri de dizi olamaz. C dilinde Bir fonksiyonun
    - Parametresi dizi olamaz
    - Geri donus degeri bir dizi olamaz.
    
- **Pointer Aritmetigi:** C'de bir adres ile bir tamsayi toplanabilir adresten tamsayi cikartilabilir. Tamsayidan adres cikartilasi syntax hatasidir.
- Bu islemlerin sonucu adrestir, adres ile tamsayi isleme girdiginde cevap adrestir.
- Dizinin bir elemaninin adresini 1 ile toplarsak bir sonraki elemanin adresini elde ederiz. Bu pointer aritmetigi sayesinde ptr'nin 1 artamasi icin sizeof(int) ile toplamak yerine 1 ile toplayabiliyoruz.
- Haliyle `a[10]` dizisi icin `a+i` ile `&a[i]` i'nin artan degerleri icin ayni sekilde dizi icinde ilerler.`a[b] = *(a+b)` ve `b[a] = *(a+b)`
- Pointer degiskenin bir artmasi gosterdigi dizi elemanindan bir sonrakisini gostermesi anlamina geliyor.
    ```
    for (int i = 0; i < 10; ++i){
        printf("%d %d %d\n", *ptr, a[i], *(a+i));
        ++ptr;
    }    
    ```
- `++cnt` cnt degerinin degeri 1 artar iken `++ptr` ptr gostericisinin dizinin bir sonraki elemaninin adresini gostermesi demektir.
- Pointer aritmetiginde iki adres toplanamaz. Syntax hatasidir.
- Iki adres birbirinden cikartilirsa isaretli bir tamsayi elde edilir `(a+5) - (a+3)` `2` tamsayi degerine esittir. Ancak ayni dizi elemanlarini tutan adreslerde kullanmak mantiklidir.
- a dizisinin i elemanina erisirken olan:`a[i]` a adresi + i tamsayisi ise `i[a]` da i tamsayisi + a adresi oldugu icin ayni anlama gelir.
- p adres olmak uzere `*p` ile `p[0]` arasinda hicbir farklilik yoktur. `p[-3]` ile `*p[p-3]` de aynidir.
- Dizinin olmayan bir elemanina erismeye calismak syntax hatasi degil ancak tanimsiz bir davranistir. 
- C dilinde pointer degisken ya `valid` ya da `invalid` `state`'dedir. invalid pointeri sadece atama yapmak icin kullanilmalidir.
- Cop degerdeki(ilk deger atanmamis) pointerlar gecersiz pointerlardir. Bu pointera ilk deger adresi atamak disinda baska kullanilamaz.Bu pointer'lara `wild pointer` denir.
- Bir nesnenin adresi olmayan bir pointer'da gecersiz pointerdir. 5 elemanli bir dizinin son elemani `a[4]` iken, `a[5]` gecerlidir ancak kullanmak istersek derefence edersek tanimsizdir.
- Bir adres hayati devam eden bir nesnenin adresi ise gecerlidir, ayrica dizinin bittigi yerden sonraki adres gecerlidir ancak icerik operatorunun operandi olarak kullanildiginda tanimsizdir *bu durum daha detayli incelenecektir.*

## 29 

