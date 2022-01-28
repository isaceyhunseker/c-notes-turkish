# C Notlari

BETTER LATE THAN NEVER

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
- Islem onceligi durumundan kacmak icin fonksiyon makrolarinda degiskeni () icinde yazmaktayiz.

    ```c
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

    ```c
    #define iprint(x) pritnf("%d\n", x)
    #define iprint(x) printf(#x)
    ```

- Kosullu derleme makrolari:

    ```c
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

    ```c
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

    ```c
    #ifndef __cplusplus
        #error this program only builded by C++ Compiler
    #endif
    ```

- #pragma standart bir on islemci komutu ama hangi anlami yuklenecegi derleyiciler tarafindan belirlenmistir.
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
- fallthrough ornegi:

    ```c
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

    ```c
        goto label;

        label:
        //statement;  
    ```

- goto kontrol deyimi ile fonksiyonda daha yukaridaki bir deyime programin akisi yonlendirilmemelidir.
- cok ic ice tasarlanan dongulerde butun donguden cikmak icin goto kullanilabilir. goto kullanilmaz ise flag set edilip bu flagin degerine gore breakler calistirilir, bu durum goto kullanmaktan cok daha komplikedir.

    ```c
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

    ```c
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

    ```c
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

    ```c
    int x = 10;
    int y = 3;

    double dval = (double)x / y;
    ```

## 27 Pointer Giris

- Pointer adres anlamina gelen bir sozcuk.
- Pointer'lar ikiye ayrilir, Object Pointers ve Function Pointers.
- Nesnenin bellekte nerede oldugu bilgisi, nesnenin adresidir.
- Degiskenin turu ne ise adresi de * tur seklinde gosteriliyor. Haliyle nesne turu kadar adres turu vardir.

    ```c
    int *int
    double *double
    ```

- `int *ptr` ptr is a pointer to int...
- Tokenlar arasindaki bosluk karakterlerinin bir etkisi olmadigi icin asterix atomunun nereye bitisik oldugu cok onemli degil.
  - `*` sadece bir sonraki degiskeni niteler: `int *pointer, non-pointer` gibi. Burada ikinci degisken `int` turundedir.
- pointer turlerinin hepsi 4 byte buyuklugundedir, *char'da*long long da ayni buyukluktedir.
- `&` `address of` operatorudur, (adres operatoru)
- `*` `dereferencing / indirection` operatorudur, (icerik operatoru)
- `[ ] index / subscript` operatoru
- `->` `member selection op.` (arrow operator) ok operatoru.
- Ornek kullanim:

    ```c
    int x = 10;
    int y = 30;

    int *p = &x;
    p = &y;
    ```

- adres degiskeninin icindeki deger `printf("&x = %p\n", &x)` ya da `printf("ptr = %p\n", ptr)` seklinde yazdirilabilir.
- array decay, array to pointer conversion: Bir dizinin ismi bir ifade icinde kullanildiginda derleyici otomatik olarak o ismi dizinin ilk elemaninin adresine donusturuyor. Asagidaki iki satir bu ozellikten dolayi ayni anlama gelmektedir.

    ```c
    int *ptr = &a[0];
    int *ptr = a;
    ```

- Bu durum sizeof operatorunde gecerli degildir. Iki degisken farkli iki sonuc uretir.
- Bir nesnenin adresi degistirilemez. Nesne bellekte bir yerden bir yere tasinamaz.
- Derefencing-Indirection Operatoru(*): Icerik operatoru: Adresi verilen degiskenin degerini verir.
- Icerik operatorunun operandi bir adres olmali.
- Bir kodun karmasik gorunmesi icin yapilmasina obfuscation denir, anlami deg ismeden anlasilmaz hale getirilmeye yarar.
- Icerik operandi dizinin ilk elemanini gosterir.Asagidaki kodda a[0] 100 degerini alir.

    ```c
    int a[] = {10,20,30,40};
    *a = 999;
    ```

- pointee pointerin gosterdigi nesnedir.

    ```c
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

    ```c
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

    ```c
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

## 29 Pointer - Const - Diziler Ustunde Islem Yapan Fonksiyonlar

- Bir pointerin tuttugu nesnenin hayati bittiginde o pointerin da gecerliligi ortadan kalkar.
- C'de diziler buyuyen varliklar degildir kac elemani varsa o kadar kalacaktir, haliyle diziyi tasan pointer bu anlamda kullanilamaz.
- Dizinin buyuklugunu tutmak icin belki kullanilabilir, ancak derefence edilemez.
- `int* p = NULL` p gecerli ancak hicbir nesneyi gostermiyor, Null pointer.
- Const anahtar sozcugu bir degiskenin taniminda kullanildiginda o degiskenin degerinin degismeyecegini adeta bir sabit gibi kullanilacagini gosteriyor. Degistirilmeye calisirsa syntax hatasi olur.
- `const variable` bir oksimorondur. Degismeyecek olan degisken demektir. Okuma amacli kullanilacak olan degiskenler ve diziler icin kullanilir.
- `int const` ile `const int` ayni anlama gelmektedir.
- Degeri degismeyecek degiskenleri `const` ile tanimlayinca hem okunabilirlik artiyor hem de derleyici tarafinda optimizasyon saglaniyor.
- Sembolik sabit makrolari,`define` ile `const` arasinda farklar vardir:
  - const degiskenleri scopu vardir.
  - nesne olduklari icin adresleri pointer degiskenlerde tutulabilir.
  - Omur kategorisi degisebilir. Sembolik sabit sadece bir sabit degeridir.
  - Case dizi indisi gibi yerlerde ancak makro sabitler kullanilabilir.
- Dizinin sadece 5 indisli elemanina deger verip digerlerini sifir ondegeri ile tanimlamak: `int a[100] = {[5] = 459}`
- const nesnelerin ilk degeri sabit olmak zorunda degildir runtime'da belirlenir `const int y = func();`
- static omurlu degiskenlere ilk deger veren ifadenin sabit bir ifade olmasi gerekir.
- const bir degiskeni bir sekilde degistirsek dahi bu tanimsiz bir davranis olur.
- `int * const ptr = &x` demek: ptr'nin degerinin hic degismeyecegini ve hep x'i gosterecegi anlamina gelir. `ptr = &y` syntax hatasidir. `*ptr` degeri degisebilir yani x'in degeri degisebilir ancak bu ptr hep o adresi tutacaktir. Boyle pointerlara **const to pointer** denir. top level const ve right const' da denir.
- `const int * ptr = &x` ve ayni anlama gelen `int const * ptr = &x` ptr yoluyla ptr'nin gosterdigi degiskenin sabit olacagi anlamina gelir. `ptr` `x`'i salt okuma amaci ile gosteriyor. `*ptr  = y` hata verecektir ancak ptr baska bir degeri gosterebilir, `ptr = &y` ifadesi mumkundur. Bu sekilde tanimlanmis pointerlara **pointer to const** denir. low level const ve left const' da denir.
- Kisacasi const hangi ifadeden once gelirse const olan odur.  
- `const int* const ptr` sabit olan bir degerin adresini surekli tutacak olan bir pointerdir.
- Cogunlukla low level const kullanilir. Salt okunacak olan sabit degeri tutan bir pointer.
- const dogrulugu: const ile tanimlanmasi gereken butun degiskenler const anahtar sozcugu ile tanimlanmis olmalidir.
- access fonksiyonlarinda erisilen degiskenin const olarak tanimlanmamasi cokca yapilan hatalardandir.
- `void func(int * p)` ben bu fonksiyonda p'nin tuttugu degiskeni set edecegim demek iken `void func(const int *p)` ben bu fonksiyonda p'nin tuttugu degiskeni sadece okuyacagim demektir.
- `const int*` degerinin `int*` degerine typecast edilmesi yanlis iken `int*` degerinin `const int*` degerine donusturulmesi hat degildir.

    ```c
    int x = 10;
    const int* ptr = &x; //burada bir hata yok.
    ```

    ```c
    const int x = 10;
    int* ptr = &x; //burada bir hata olur. const olan x'i gosterdiginin const olmadigini soyleyen ptr ile gostermeye calistik.
    ```

- Dizi ustunde islem yapan fonksiyonlar dizinin adresini ve boyutunu isterler. Bu cagriyi yapacak fonksiyon bu iki degeri geciyor olmalidir. `void printArray(const int* p, size_t size)`.
- Dizinin belirli kismi yazdirilmak istenirse mesela 5. elemandan itibaren 3 elemena yazilmak istenen a dizisi icin `printArray(a+5, 3)` notasyonu kullanilir. `a+5` yerine `&a[5]` yazilabilir.
- Bir ornek kod: ortalama alma fonksiyonu aldigi pointeri yine bir baska fonksiyon olan dizi toplama fonksiyonuna vermekte:

    ```c
    int sum_array(const int* p, int size)
    {
        int sum = 0;

        while(size--){
            sum += *p;
            ++p;
        }

        return sum;
    }

    double get_mean(const int* p, int size)
    {
        return(double)sum_array(p, size)/size;
    }

    int main()
    {
        int a[SIZE];

        randomize();
        set_array_random(a, SIZE);
        print_array(a, SIZE);

        printf("mean value of array = %f\n", get_mean(a, SIZE));    
    }
    ```

## 30 Pointer - Pointer Parametreli Fonksiyonlar - Pointer Idiomlari - typedef 1

- Birden fazla geri donuse ihtiyaci olan fonksiyonun bunu yapmasi icin ilk metod call by reference'dir. `void get_array_max_min(const int* array, int size, int* max, int*min)` seklinde max ve min return edilmek yerine doldurulur.
- Adres alan fonksiyonlar bu adreslerdeki degiskenleri baska fonksiyonlara verebilirler.
- Bir fonksiyona bir arrayin iki elemaninin pointer uzerinden gecmek icin iki notasyon vardir.

    ```c
    swap(&p[k], &p[k+1]); 
    swap(p+k, p+k+1);
    ```

- Pointer degiskeni fonksiyona parametre olarak vermenin bir yolu `int *p` iken diger yol `int p[]` dir.
- `void sort(int p[], int size)`'deki konvensiyon p eger bir dizinin ilk elemani ise tercih edilir, bu bir zorunluluk degildir ancak her ikisi de kullanilabilmektedir. `p[]` yaygin degildir. **Unutulmamalidir ki bir fonksiyon bir diziyi parametre alamaz.** `p[]` ilk elemandir.
- `*p++` p'nin gosterdigi nesneye eris, ardindan p'yi bir arttir. Array islemlerinde cokca kullanilir. En yaygin idiomlardan biridir.

    ```c
    #define SIZE 100
    void copy_array(int *pdest, const int *psource, int n)
    {
        while(n--)
            *pdest++ = *psource++;     
    }    
    ```

- Bir ornek kod: a dizisinin A indisli elemanindan baslayarak b dizisinin B indisli elemanindan baslayana yere N tane eleman kopyalayan fonksiyon:

    ```c
    void copy_partial_array(int *pdest, const int *psource, int n)    
    {
        while(n--)
            *pdest++ = *psource++;     
    }

    int main()
    {
        int a[];
        int b[];

        copy_partial_array(b+B, a+A, N); //1.method
        copy_partial_array(&b[B], &a[A], N); //2.method
    }    
   ```

- ++ ve -- operatorunun operandi bir dizi olamaz. Dizinin ismi burada kullanilamaz.
- Bir ornek `++*p++` sagdan sola oncelik seviyesi ile okursak `(++(*(p++)))` demek yani dongude ise her elemanin degerini 1 artirarak ilerler.
- `px == py` icin adreslerin ya ayni nesnenin adresi olmasi gerekiyor ya ayni dizinin bittigi yerin adresi olmasi gerekiyor ya da null pointer olmasi gerekiyor.
- a dizinin bittigi yerin adresi `pe = a+SIZE` olarak tanimlayip, diziyi donerken karsilastirma olarak kullanilabilir `while(ps != pe)`. Buna range denir, `[p1 p2)` gibi bizim durumda `[ps,pe)`.
- `px == py` x'i ve y'yi gosteren iki farkli adresi karsilastirirken `*px == *py` x'in ve y'nin tuttugu adreslerin icindeki degerleri karsilastirir.
- Bir turu temsil eden alternatif bir turu - tur ismini olusturmak mumkundur. Buna **alias** takma isim denir.
- **typedef** bir ture esisim olacak yeni bir tur ismi bildirimidir `int` yerine `tamsayi` gibi bir isim vermek gibidir. Derleyici artik tamsayi'yi taniyacaktir.

    ```c
    typedef int Word; // artik Word int yerine gececektir.

    Word x = 5; // bu sekilde tanimlama yapilabilir.
    Word func(int...); // return degeri Word yani int olan bir fonksiyon
    ```

- `typedef int* IPTR` int* turu yerinie IPTR denebilir. `IPTR p = &x`. Scope'u belirlemek icin makrolar yerine kullanilir. Ayrica birden fazla pointeri tek satirda tanimlamak yine typedef ile mumkundur.

    ```c
    define IPTR int*

    typedef int* Iptr;

    int main()
    {
        IPTR p1, p2; //int *p1, p2;
        Iptr p1, p2; //int *p1, *p2;
    }
    ```

- typedef tanimlama yol haritasi
  - hangi ture es isim verecekseniz o turden bir degisken tanimlayin. `int x;`
  - tanimlamanin basina typedef anahtar sozcugunu yerlestirin. `typedef int x;`
  - degiskene verdiginiz ismi o degiskenin turune vereceginiz es isimle degistiriniz. `typedef int Myint;`
- Dizi icin `typedef int INTA[10];` 10 elemanli bir dizinin typedef'idir. `INTA10 a, b, c;` icin `int a[10], b[10], c[10];`
- typedef bildiriminin avantajlari
  - Karmasik bildirimleri okumasi daha kolay bir hale getirir.
  - Ara degisken basliklari yaratarak ana tur isimlerini kullanmak yerine bu ara degiskenlerden turetmeler yapilir. `typedef double Dollar` diyip ardindan dolarla ilgili degiskenlerin bu degikenden turetilerek kullanilmasi gibi `Dollar sum_account, expenditure` gibi.
  - Ilerde Dollar turunun tuttugu dolar degerlerinin turunu degistirmek istersek sadece typedef bildirimini degistirerek yapabiliriz.
- typedef bildirimiyle olusturulan isim baska bir typedef turu olusturuluken kullanilabilir `typedef int Word` icin `typedef Word* Wordptr`
- standart kutuphanelerde `int32_t` `uint16_t` gibi typedefler vardir.

## 31 Standart kutuphene ve typedef bildirimleri - size_t - Adres Donduren Fonksiyonlar

- Bir typedef ornegi: `typedef int Bool` boylece derleyici `Bool` turunde calisabilecek.
- Standart kutuphane typedef bildirimlerini okunabilirlik ve tasinabilirlik amacli kullaniyor.
- `size_t` sizeof operatorunun urettigi degerin turudur. `typedef unsigned int size_t` seklinde tanimlanabilir. Ancak bu tanim derleyiciye birakilmistir. `unsigned int` olmak zorunda degildir. Gercek tur yerine typedef kullanildiginda bu gibi durumlarda derleyiciye hareket alani birakiliyor. `size_t`'nin buyuklugu derleyicideki int degerinin buyuklugune gore degisebiliyor.Ya da onu `long` turune atayabiliriz.
- Bununla beraber, `ptrdiff_t`, `time_t`, `clock_t`, `fpos_t` ve `ldiv_t` gibi standart typedefler de vardir.
- `strlen`, `malloc`, `memcpy` gibi fonksiyonlar `size_t` parametresini kullanan bazi standart C fonksiyonlarinda tasinabilirlik amaciyla bu method kullanilmistir.
- standart kutuphanenin `size_t` kullandigi yerde(parametre turu ya da geri donus degeri turu olarak) biz de `size_t` ile o degiskeni almak zorundayiz ki tasinabilirlik sorunumuz olmasin.
- Standart kutuphane `size_t` tur es isminin istenildigi durumlar:
  - Bir dizi boyutu isteyen fonksiyon parametrelerinin turu olarak.
  - Yazi uzunlugu turu olarak.
  - sizeof degeri isteyen parametreler.
  - tane(adet) turu.
- `stddef.h` kutuphanesi bir cok makro ve typedef iceren cok buyuk olmayan bir kutuphanedir.
- `size_t` degerinin printf'de yazdirmak icin `%zu` set edilmistir: `printf("sizeof(int) = %zu\n", sizeof(int))`.
- **Functions Returning Pointers**, Adres donduren fonksiyonlar C'de en cok kullanilan yapilardan biridir. Fonksiyonun geri donus mekanizmasi ile bir nesneyi teslim etmesi demektir.
- `int *func(void)` seklinde tanimlanir. `int *xptr = func()` seklinde kullanilabilir. `return &x` gibi donebilir.
- Bu sekilde pointerin hangi adresi tutacagini dogrudan vermek yerine fonksiyonun ciktisina gore belirleyebiliyoruz.
- Otomatik omurlu degisken, bu kodun yurutulmesi surecinde hayatta olan ve kod blogu bitince sifirlanan kodlardir. Otomatik omurlu degiskenin adresini fonksiyon disina return eden pointer, invalid pointer olur.

    ```c
    int* foobar(void)
    {
        int sum = 0;

        for(int i = 0; i<10; ++i){
            sum +=i
        }
        
        return &sum;
    }

    int main()
    {
        int* ptr = foobar(); // foobar yerel bir degisken donmektedir. Haliyle bu degiskenin omru bittigi icin undefined behaviour.
    }
    ```

- Ancak sum degiskeni `static int sum = 0` olarak tanimlansa idi bir undefined behaviour olmazdi, cunku static omurlu `sum` degiskeni program calistigi surece var olacakti. Haliyle global degiskenler, static anahtar sozcugu ile tanimlanan yerel degiskenler ve string literaller `"string literal"`
- Adres donduren bir fonksiyon asla ve asla otomatik omurlu bir nesnenin adresini dondurmemelidir.
- Bir fonksiyon static omurlu nesne adresi donduruyorsa fonksiyona yapilan her cagri ayni adresi donuyor olmali.
- Fonksiyon kendisini cagiran koddan bir nesnenin adresini alir adresini aldigi nesnenin adresini dondurur.
- Bir kod ornegi: Bir dizinin en buyuk elemaninin adresini donduren fonksiyon:

    ```c
    #define SIZE 20
    int* array_max(const int* pa, size_t size)
    {
        int* pmax = (int *) pa;// const cast - const'tan int'te atama yapilamayacagi icin.
        for (size_t k = 1; k < size; k++)
        {
            if(pa[k] > *pmax)
                pmax = (int *)&pa[k];
        }
        return pmax;// bu adres pa dizisinden cekildigi icin otomatik omurlu degildir, dizinin icindeki global adreslerden biridir.
    }

    int* array_min(const int* pa, size_t size)
    {
        int* pmin = (int *) pa;// const cast - const'tan int'te atama yapilamayacagi icin.
        for (size_t k = 1; k < size; k++)
        {
            if(pa[k] < *pmin)
                pmin = (int *)&pa[k];
        }
        return pmin;// bu adres pa dizisinden cekildigi icin otomatik omurlu degildir, dizinin icindeki global adreslerden biridir.
    }
    
    int main()
    {
        int a[SIZE];

        randomize();
        set_random_array(a, SIZE);
        print_array(a, SIZE);

        int *pmax = array_max(a, SIZE);
        int *pmin = array_min(a, SIZE);

        printf("max = %d\n", *pmax);
        printf("indis of max = %d\n", pmax-a); //pmax - a pmax elemaninin bulundugu indisi verir
        *pmax = -1;// en buyuk elemani -1'e esitledik, boylece test edebilecegiz kodumuzun dogru calistigini
        print_array(a, SIZE);
        print_array(a, pmax - a + 1); //dizinin basindan en buyuk elemani kadar ve o eleman dahil yazdirir.
        print_array(pmax, SIZE - (pmax - a)); //dizinin en buyuk elemanindan sonuna kadar yazdirir.

        if(pmax > pmin){// max'in adresi min'den buyuk mu max dizide daha once mi geliyor.
            print_array(pmax, pmin - pmax + 1);// max onceyse maxtan mine kadar yazdir
        }
        else{
            print_array(pmin, pmax - pmin + 1);// min onceyse minden maxa kadar yazdir.
        }

        print_array(pmax < pmin ? pmax : pmin, abs(pmax - pmin));// yukardaki islemin aynisini yapan tek satir kod blogu
        swap(array_min(a, SIZE), array_max(a, SIZE));// dizinin max ve min degerlerinin yerlerini degistirir. 
    }
    ```

## 32 Pointer - Null Pointer - Char Pointeri

- **Otomatik omurlu bir nesnenin adresiyle asla donulmemelidir.**
- `NULL` bir object-type makrodur. Bir anahtar sozcuk degildir. Identifier vs degildir. NULL standart bir makrodur.(`stdio.h`, `stdlib.h`, `stddef.h`, `stddef.h`, `time.h`)
- NULL pointer herhangi turden bir pointer degiskene atanabilen, ilk deger olarak verilebilen bir sabit ifadesidir.
- NULL pointer semantik(mantiken-syntax degil) olarak hic bir nesneyi gostermeyen bir pointer'dir.
- Degeri **NULL** olan bir pointer degiskeni dereference etmek **undefined behaviour**'dur.
- Bir pointerin adresinin null olup olmadigi `if(p == NULL)` gibi yazarak sinanabilir.
- C'de Pointer olmayan degiskenlere `NULL` atamasi yapilamaz, sadece pointer degiskenlerde `NULL` makrosu kullanilabilir.
- C'de lojik ifade beklenen yerlerde(lojik operatorler, dongu karsilastirma operatorleri vs..) adres ifadeleri de kullanilabilir.
  - `if(ptr != NULL)` ve `if (ptr)`
  - `while(ptr)`
  - `ptr ? x : y`
- Aritmetik turden static omurlu degiskenlere ilk deger verilmediginde bunlar hayata 0 degeri ile baslar ve de Aritmetik turden static omurlu degiskenlerin ilk deger verilmediginde bunlar da hayata `NULL` pointer degeri ile baslar.
- Bir pointer degiskene tam sayi sabiti olarak 0 atanirsa bu gecerlidir, ve bu durumda derleyici 0 tam sayi sabitini `NULL` pointer'a donusturur `ptr = 0`. Ancak  `ptr = NULL` tercih edilir.
- `int a[5]` icin a'nin turu `int[5]`, double `da[20]` nin turu `double[20]`'dir. `int[5] = {1,2,4}` icin nasil `int[3]` ve `int[4]` 0 oluyorsa. Pointer arrayde'de `int *p[20] = {&x, &y}` gibi bir tanimda geri kalan 18 eleman `NULL` pointer olur.
- `int *p[20]` 20 tane `int*` turunden pointer iceren bir pointer arrayidir.
- Bazi geri donus degeri pointer olan fonksiyonlarin basarili olduklarinda donus degeri nesne adresi iken hata durumunda `NULL` doner. Mesela fopen() fonksiyonu basarili olursa *FILE donerken basarisiz olursa `NULL` doner. Bu basarisiz olan pointer return eden fonksiyonlar `NULL` donmesi durumu standart kutuphanelerde ve bizim yazacagimiz kutuphanelerde de cokca kullanilir.
- Arama fonksiyonlari(search - find fonskiyonlari.) da arama sonucu olarak bulunan nesnenin adresini donmektedir, yani pointer doner. Eger aranilan deger bulunamazsa `NULL` pointer doner.
- Bir kod ornegi: Bir int dizide bir deger arayan search_in_array isimli bir fonksiyon tanimlayin

    ```c
    int* search_in_array(const int* p, size_t size, const int val)
    {
        for (size_t i; i < size; i++)
        {
            if (*p == val)
                return (int*)p;
            p++;
        }

        return NULL;
    }
    ```

- Bizden nesne adresi eden fonksiyona null pointer gecmemeliyiz`void func(int* p)` Ancak bazi fonksiyonlar pointer parametresine null parametresini alabilir, bu fonksiyonlar null pointer icin de iceride opsiyonu olan fonksiyonlardir. Mesela fflush fonksiyonu null pointeri alirsa ayri bir is yapar null pointer gecmezsek ayri bir is yapar.
- NULL pointeri ayrica flag gibi de kullanilabilir, bir pointer basta NULL tanimlanarak mesela if'te nesne adresi ataniyorsa buradan if'e girip girmedigi kontrol edilebilir.
- Dinamik omurlu nesne adresi tutan bir pointerin, nesnesinin omru bittiginde `NULL` pointera atanir.
- C dilinde yazilar char dizilerde tutuldugu icin `strlen`, `strspn`, `strpbrk` gibi fonksiyonlar char pointer `const char*` ya da `char *` parametresi alir.
- C'de yazilar null terminated olarak tanimlanir. Haliyle stringin yani char dizisinin son elemani NULL oldugu icin diger arraylerde oldugu gibi boyutunun fonksiyona verilmesine gerek yoktur. for loopu `\0`(null karakter) ile karsilasinca duracak sekilde doner.

    ```c
    void print_str(const char* p){
       for(int i = 0; p[i] != '\0`; ++i){
        printf("%c", p[i]);
        }
    }
    ```

## 33 Pointer - Standart Kutuphane String Fonksiyonlari

- `putchar` aldigi karakteri standart output device'a basar.
- `sgets` fonksiyonu icindeki stringe standart inputtan alinan yaziyi yazar.
- NULL karakter `'/0'` 0 sayisina tekabul etmektedir. Bir stringin sonunda olan bu karaktere karar diziyi donmek icin `(while *p != '\0')` gibi yapilar kullanilabilir.
- Bir fonksiyon aldigi adresteki diziye veya bu dizideki yaziya yazacagi, buradaki yaziyi yazip degistirecek ise. yani `const` ile verilmemis bir pointer ile cagirilan bir fonksiyonun diziyi tasma riski vardir.
- Burada cagiran fonksiyonun bu durumu takip ediyor olmasi gerekir, bu sorumlulugu fonksiyonu cagiran kod bloguna birakir.(std. kutuphaneler boyledir.)
- Diger secenek ise diziyi verirken boyutunu da fonksiyona vermektir.
- strlen: `size_t strlen(const char *p)` strlen cagrisina verdigimiz dizi size_t turunden bir degiskende tutulmalidir.
- Bir kod ornegi strlen: Alinan stringi tersten yazdiran fonksiyon, `revprint`

    ```c
    void revprint(const char* p){
        for (int i = (int)(strlen(p) -1); i >= 0; --i){
            putchar(p[i]);
        }
    }
    ```

- `strchr` dizideki aranacak karakteri ilk buldugunda bu elemanin adresini dondurur `char* strchr(const char *p, int ch)`.
- `strrchr` dizideki aranacak karakteri son buldugunda bu elemanin adresini dondurur `char* strrchr(const char *p, int ch)`.
- str structindaki p pointerinda tutulan karakterin indisini `p - str` isleminin ciktisi olan tamsayi verir.
- Elimizde bir yaziyi gosteren bir pointer degisken var, bu pointer degiskenin degerini yazinin sonundaki null karakter ile degistirmemiz gerektigini dusunelim. Bunu yapmaya yonelik bir cok farkli kodlar vardir.

    ```c
    while(*p != '\0')
        ++p;
    ```

    ```c
    while(*p)
        ++p;
    ```

    ```c
    while(*p++)
        ;
    --p;
    ```

    ```c
    p += strlen(p);
    ```

    ```c
    p = strchr(p, '\0');
    ```

- `NULL pointer` ile `null character` karistirilmamalidir.
- `NULL` bir makrodur ve adres sabitidir, pointerlara atanmalidir. Pointeri degeri hicbir nesnenin adresi olmayan bir adrese ceker.
- `null character` = '/0' bir tamsayi sabitidir, ya int ya da char turden bir degiskene atanabilir. Bu bir degiskendir, dizinin sonunda olmasi dizinin sonlandirilmasi anlamindadir.
- Bir C idiomu `NULL` poiter ile `null` karakteri ayni ifade icinde kullaniyor, eger ptr yaziyi gosteriyor ve ptr'nin gosterdigi yazi bos degil ise ifadesi:`if (ptr != NULL && *ptr != '\0')` burada `short circuit` davranisindan faydalanilir. Bu sekilde `NULL` pointeri derefence etmemis oluyoruz. Bu ifadeyle `if(ptr && *ptr)` ayni ifadedir.
- Bir diziye bir yazi `struct name = "name"` seklinde yapamayiz onun yerine strcpy ile yapilir.
- Standart kutuphanede fonksiyonlar her zaman hedef adres kaynak adresten once alinir.
- `strcpy` boyut almadigi icin kullanirken dikkat etmek gerekir tasma olup olmadigi developerin sorumlulugundadir.
- `while(*pdest++ = *psource++)` null karaktere kadar kopyalamayi yapar.
- strcpy fonksiyonunun kesisen bloklar(overlapped) uzerinde calismasi tanismizdir. `strcpy(str+2, str)` ile ali alali yapmaya calismak gibi durumlar burada kast edilmektedir. Bunun icin `memmove` gibi bir fonksiyon kullanilabilir.
- `strcat` bir yazinin sonunda bir yazi eklemek icin kullanilir.

## 34 Pointer - Standart Kutuphane String Fonksiyonlari 2

- `strcmp` buyuk olan degere sahip olani buyuk doner. `lexicographical` compare denir buna. Burada gelen ilk karsilikli ogenin hangisi buyukse o buyuk olur. Boyuta karsilikli ogelerin hepsinin ayni oldugu durumda bakilir. Sozlukteki gibi karsilastirilir.
**- 0.30'da kaldim.**

## 35 Pointer -String Literals - Pointer Dizileri

- C'de string literal const degildir ancak Cpp'da const'tur. Her iki dilde de const gibi ele alinir. Static omurlu degiskenlerdir.
- **atladim.**
- **36nin ilk 5 dksini izlemedim. bu konuyla ilgilidir.**

## 36 Pointer to Pointer - Pointer to Pointer & `const` Keyword - `void` Giris

- Pointer to Pointer, gosterici gosteren gostericiler demektir.
- Pointerin kendi adresinin tutuldugu pointerlardir.
- Bir ifade bir `T` turunden bir nesnenin adresini gosteriyorsa turu `T*`dir. Bu durumda `T*`'i tutan pointerin turu de `T**` olacaktir.
- `**p` ile gosterilir, bunu `*(*p)` gibi dusunebiliriz.

    ```c
    int x = 23;
    int* p = &x;
    int** q = &p; //int * turundeki p pointerinin adresini tutan int** turunden degisken. &p'nin turu int**dir.
    ```

- ****ptr'ye kadar kullanilabilir.
- swap ornegi, swap yapan fonksiyonun int* turunden degiskenlerin adreslerini aldigi duruma ornek olacaktir.

    ```c
    void pswap(int** ptr1, int** ptr2)// takes address of pointer
    {
        int* ptemp = *ptr1;
        *ptr1 = *ptr2;
        *ptr2 = ptemp;
    }

    int main
    {
        int x = 10;
        int y = 20;
        int* p1 = &x;
        int* p2 = &y;

        pswqp(&p1,&p2); // x ve y'nin degerleri degismez onlari gosteren gostericiler degisir.
        pswap(p1,p2); //x ve y'nin degerleri degisir.
    }
    ```

- Daha karmasik bir senaryo incelemek gerekirse: Bir dizinin hem en buyuk elemanin hem de en kucuk elemanin adresinin hesaplayan fonksiyon.

    ```c
    void get_min_max(const int* pa, size_t size, int** ptr_min, int** ptr_max)
    {
        *ptr_min = *ptr_max = (int *)pa;

        for (size_t i = 1; i < size; ++i){
            if(pa[i] > **ptr_max)
                *ptr_max = (int *)pa[i];
            else if(pa[i] < **ptr_min)
                *ptr_min = (int *)pa[i];
        }
    }

    int main()
    {
        int a[SIZE];
        //
        randomize();
        set_array_random(a, SIZE);
        print_array(a, SIZE);

        int* pmin, *pmax;
        get_min_max(a,SIZE, &pmin, &pmax);
        swap(pmin,pmax);// changed vaules of variables
    }
    ```

- Pointer to Pointer boyutu pointer ile aynidir.
- Pointer to Pointer'a da NULL ilk atama yapilabilir.
- Bu adresler bir dizi de olabilirdi:

    ```c
    void foo(int** pa, size_t size);

    int a = 12, b = 23, c = 34, d = 56;
    
    int main()
    {
        int* pa[] = {&a, &b, &c, &d};//pointer array.
        foo(pa, asize(pa));
    }
    ```

- Derleyici acisindan `void func(int *p, int size)` ile `void func(int p[], int size)` arasinda fark yoktur. Ikiside bir pointeri gosterir. Dogal olarak `void func(int **p, int size)` ile `void func(int *p[], int size)` aynidir. Ancak `*p[]` dizinin ilk elemanini gosteren pointerlar icin tercih edilir genelikle.
- `**p` pointeri dereference yapip tekrar deference etmek `double derefencing` veya `double indirection` denir.
- [*ptr](5) ile *ptr[5] farkli anlamlara geliyor [*ptr](5); ptr'nin gosterdigi gostericinin besinci elemanini dereference eder.
- `int *const p = &x` durumumda p'nin degeri degistirilirse sentaks hatasi verilir. const pointer to int.
- `int const *p = &x` durumunda p'yi gosteren pointerin degeri degistirilirse sentaks hatasi verir. pointer to const int.
- `*` ne'den once gelirse const olan odur.
- `int** const ptr = &q` icin `ptr = &q` hata verir.
- `int* const *ptr = &q` icin `*ptr = &q` hata verir.
- `int const **ptr = &q` icin `**ptr = &q` hata verir.
- Dogal olarak const anahtar sozcugunun ve *'larin yerlesimi tamamen lojik tasarima baglidir.
- const anahatr sozcugu birden fazla da kullanilabilir, mesela: `int const * const * const ptr` yukaridaki uc durumun da degistirilemez oldugu anlamina gelen gecerli bir ifadedir.
- Salt okuma amacli kullanimlarda fonksiyon prototiplerinde yazmayi unutmamak gerekir.
- void pointers. `char *strncpy(char *pdest, const char *psource, size_t n)` buradaki aradaki `n` n karakterin uzerinden islem yapilmasini saglar. strcpy'den farki budur. Ayni durum `strcat, strncat` ve `strcmp, strncmp` icin de gecerlidir.
- strncpy sona null karakteri koymasi icin n parametresinin yazinin boyutundan buyuk olmasi gerekiyor. Eger yazi daha kucukse null karakterin manuel olarak son elemana set edilmesi gerekmektedir.
- `strncpy(dest, source, 3)[3] = '\0';` kopyalamayi ilk 3 elemanda yapip 3 indisli elemana null karakteri ekler.
- Yazidan kucuk elemani kopyalamada otomatik olarak NULL karakterinin eklenmemesi soyle kullanilabilir: 012uga6789 yaratimi ornegi:

    ```c
    char source[100] = "tugay";
    char dest[100] = "012345678";
    //012uga6789

    printf("(%s)\n", dest);
    strncpy(dest + 3, source + 1, 3);
    printf("(%s)\n", dest);// burada uga'yi 345 yerine koydu.
    ```

- `void` de bir turdur ancak bazi kisitlamalari vardir:
  - Bir nesnenin turu `void` olamaz.
  - Dizinin elemanlarinin turu de `void` olamaz dogal olarak.
- Bir ifadenin turu `void` olabilir. Bu durum iki farkli sekilde karsimiza cikar:
  - Geri donus degeri olmaya fonkisyonun donus degeri yerine yazilir, bu fonksiyonlara `void function` denir.
  - Bir ifade void turune cast edilebilir. Tur donusturme operatorunun (`typecast`) hedef turu `void` olabilir: `(void) (x + 5)` gibi. Bu durum geri donus degeri olmasina karsin bu degerin istenmedigi - discard edildigi durumlarda kullanilir. Bu durumda bu geri deger donmemeyi bilerek yaptigimizi gostermek icin bu gosterimi kullaniriz. Fonksiyonu cagirdim ama geri donus degerini kullanmak istemiyorsam - `(void)getchar();` gibi burada `getchar` normalde `int` donecektir ancak bu sekilde onu kullanmayacagimizi gostermis olduk.

## 37 Void Pointers - Memory Uzerinde Islem Yapan Fonksiyonlar

- `int func(void);` func fonksiyonu parametre almiyor demek iken `int func()` fonksiyonun parametreleri hakkinda bilgi verilmedigi anlamina gelir.
- `void*` turu bir pointer/adres turudur. `void` ile karistirilmamalidir.
- `void* vptr` icin `vptr` herhangi turden bir nesnenin adresini tutabilir. Asagidaki atamalar gecerlidir:

    ```c
    int x = 10;
    double dval = 2.31;
    char str[] = "oguz";

    void* vptr = &x;
    vptr = &dval;
    vptr = &str;
    ```

- void pointer'da dereferencing islemi gecersizdir `*vptr = 20;` veya `vptr[2]` gibi.
- `vptr + 5` gibi pointer aritmetigi de calismaz.
- void pointerla yapilabilecek islemler:
  - ilk deger veya atama yoluyla ilk deger atanabilir: `vptr = &x;` Tam sayi gercek sayi atanamaz.
  - NULL pointer degeri atanabilir `vptr = NULL;` veya `vptr = 0;` gibi.
  - `vptr == str` seklinde adres kontrollerinde kullanilabilir.
- `T` herhangi bir tur olmak uzere: C dilinde `T*` turunden `void*` turune ve void turunden `T*` turune otomatik donusumu vardir. Bu donusumler otomatik(implicit) oldugu halde `int* iptr = (void*)vptr` gibi explicit olarak da yapilabilir.
- `Generic programlama` Turden bagimsiz programlama demektir. `void*` burada cogunlukla kullanilir.
- Ture bagli olmayan fonksiyonlar yaratmak onlarla calismak icin generic programlamadan yararlanilir.
- Ornek vermek gerekirse: herhangi turden iki degiskenin takas edilebilmesi icin bir fonksiyon yazma:

    ```c
    void gswap(void * vp1, void * vp2, size_t n) //generic swap
    {
        char *p1 = vp1; //char because it has 1 byte magnitude
        char *p2 = vp2; //char because it has 1 byte magnitude We will swap byte one byte right now.

        while(n--)
        {   
            char temp = *p1;
            *p1++ = *p2;
            *p2++ = *temp;
        }
    } 

    int x = 56443;
    int y = 34566;

    double d1 = 32.553;
    double d2 = 33.123;

    gswap(&x, &y, sizeof(int)); //sizeof used for determining type of variables from their sizes. 
    gswap(&d1, &d2, sizeof(double));
    ```

- Fonksiyonlarin icine gonderilen adresin, bir diziye mi ait oldugu veya ait ise o dizinin boyutu hakkinda fikir vermesinin olasiligi yoktur.
- a(int) dizisinin ilk 4 elemani ile b(int) dizisinin son 4 elemanini takas etmek icin soyle bir fonksiyon cagirilabilir:

    ```c
    gswap(a, b + SIZE - 4, 4* sizeof(int));
    ```

- `string.h`'daki fonksiyonlar sadece stringler uzerinde calismaz, bellek bloklari uzerinde islemler yaparlar.
- `memset`, `memcpy`, `memmove`, `memchr` ve `memcmp` bu fonksiyonlardir.
- `memset` bellek blogunu bir tamsayi ile doldurur.
- `void *memset(void *vp, int val, size_t size);` icin `vp` bellek blogunun baslangic adresi, `val` doldurulacak deger, size ne kadar bellek alaninin(kac tane byte) doldurulacaginin boyutunu verir.
- Bellekte size ile calisirken genel pratik `eleman sayisi * sizeof(elemanin_turu)` olmali, 10 elemanli bir `int` dizi icin `10 * sizeof(int)` olmali.
- `void*` ile const void* icin diger turlerdeki durum gecerlidir. Salt okuma icin kullanilacak degiskenler fonksiyona `const void*` ile alinir.
- `memcpy` generic bir kopyalama islemini yapan fonksiyondur. Bir bellek blogunu bir yerden baska bir yere kopyalamak icin `memcpy` fonksiyonunu cagirabiliriz.
- `void *memcpy(void *vpdest, void *vpsource, size_t n);` n tane byte kopyalar.
- Turden bagimsiz atama operatoru gibi dusunulebilir.
- Elimizde iki bellek blogu varsa biri okuma biri yazma icinse, ve okuma icin olan yazma icin olanla cakisiyorsa buna `overlapped blocks` denir.
- `memcpy` fonksiyonu `strcpy` gibi `overlapped block`larda tanimsiz davranis olusturabilir, boyle bir durumda kullanilmamalidir.
- Boyle durumlari belirtmek icin fonksiyon overlapped olmayan degiskenler almasi gerektigini belirtmek gerekir. `restrict` anahtar sozcugu ile tanimlanir, `restrict` degiskenler overlapped etmeyen bellek bloklarini almak zorundadirlar.
- Bir dizinin elemanlarini 10 tane yana kaydirmak `overlapped block` durumuna ornek olabilir.
- `overlapped block` olan durumlarda kullanilmasi gereken fonksiyon `memmove`dur.
- `memchr` bir bellek blogunda belirli bir tamsayi degerine sahip bir byte arar.
- `void *memchr (void * ptr, int value, size_t n);` prototipine sahiptir, value degerini ptr adresinden itibare n byte icinde arar.
- `memcmp` turden bagimsiz iki bellek blogunu karsilatiran ve karsilastirma sonucunu donen fonksiyodur.
- `int memcmp ( const void * ptr1, const void * ptr2, size_t num );` prototipine sahiptir.
- Karsilatirmalar isaretsiz olarak yapilir.

## 38 Void Pointers 2 - Fonksiyon Pointer'lari(Callback) - Generic Fonksiyonlara Giris(`qsort`)

- `void pointer` temelde generic fonksiyonlar tasariminda kullanilir, generic fonksiyon turden bagimsiz fonksiyon demektir.
- Turden bagimsiz olarak bir diziyi reverse edecek fonksiyon buna ornek olabilir: `void * greverse(void* vpa, size_t* size, size_t sz)` `vpa` ilk elemanin adresi ve `size` dizinin boyutu iken `sz` bir ogenin boyutunu tutar.
- Buradaki ornekte dikkat edilmesi gereken onemli bir nuans vardir: `gswap` fonksiyonuna elemanlar boyutlarini belli edecek sekilde verilmelidir, bu sekilde farkli boyutlarda calisabilmesi mumkun olacaktir:

    ```c
    void * greverse(void* vpa, size_t* size, size_t sz)
    {
        char* p = (char*)vpa;
        
        for(size_t i = 0; i < size / 2; ++i) {
            gswap(p + i * sz, p + (size - 1 - i) * sz, sz); //step size is i * sz for this swap operation. 
    ```

- `memcmp`ile turden bagimsiz siralama fonksiyonu yazmak mumkun degildir, cunku bizim bellek karsilastirma fonkisyonumuz, byte byte calisir. Sadece esitligi kontrol edebiliriz bu sebeple buyuk kucuk karsilastirip siralayamayiz.
- Turden bagimsiz dizilerde siralama icin standart kutuphanedeki `qsort` fonksiyonu kullanilabilir.
- `void **` turu generic bir pointer turu degildir. `void **` turu sadece `void *` turden bir nesne adresi anlamina gelen ifadenin turunu tutabilir.
- **Callback mekanizmasi:** Bir fonksiyona baska bir fonksiyonu arguman olarak gondermektir: **Function Pointers**
- `C`,`Cpp` ve `java` gibi dillerde bir fonksiyona arguman olarak bir fonksiyon gonderilebilir.
- Soyle somutlastirilabilir: a fonksiyonu b fonksiyonunu cagiriyor ve b'ye c fonksiyonunu arguman olarak veriyor.
- *Call-back: I sent you a function and you will call it back* olarak da aciklanabilir.
- Bu callback yapisi adres semantigiyle yani fonksiyon pointerlari gerceklenir.
- Bir fonksiyon adresinin turu geri donus degerinin ve parametrelerinin turu ile birlikte belirlenir.
- Dogal olarak `int foo(in t)`, `int bar(double)` ve `int baz(void)` fonksiyonlarinin adreslerinin turleri farklidir.
- `int toupper(int)` ve `int isalpha(int)` ayni turden fonksiyon adres turune sahiptir.
- `int foo(int)` turunden bir fonksiyonun adresinin turu: `int(*)(int)` seklinde gosteririlir. Bu notasyon `donus turu(*(*)(argumanlarin turleri)` seklinde gosterilir.
- Geri donus degeri `int` olan iki stringi karsilastiran `strcmp` fonksiyonun adresinin turu `int(*)(const char* const char*)` olur.
- Fonksiyonun adresini elde etmenin ilk yolu `&` islevini kullanmaktir: `&foo`, `&strlen` gibi.
- Diger yol ise `function to pointer` conversion'dur. Bu donusum `array decay/array to pointer` conversion'a benze yani dizinin ilk elemanin adres olarak kullanilmasi metodu `&a[0] = a` esitligidir.
- `function to pointer` conversion'u bir fonksiyonun isminin bir ifade icinde kullanildiginda derleyici fonksiyon ismini fonksiyonun adresine donusturur.
- `int foo(double);` icin: asagidaki ikinci ifade`foo` de birincisi gibi`&foo` adrese donusturulerek kullanilir.

    ```c
    int foo(double);
    
    int main()
    {
        int (*fptr)(double);//foo's function pointer type.
        &foo
        foo

        fptr = &foo; //valid
        fptr = foo; //valid

    }
    ```

- `int (*fptr)(double)` gostericisi ile `int func(int)` fonksiyonun adresini tutmaya calismak: `fptr = &func` C'de yanlis C++'da sentaks hatasidir.
- Bir fonksiyon pointeri, global yerel yada statik/otomatik omurlu olabilir.
- Fonksiyonlarin parametreleri ve geri donus degerleri funtion pointer olabilir.
- Sistemde butun nesne gostericilerin boyutu nasil ayniysa, butun fonksiyon gostericilerinin de boyutu birbiriyle aynidir. Ancak nesne gostericisi ile fonksiyon gostericisinin boyutu ayni olmak zorunda degildir.
- Fonksiyon cagirma operatoru `function call operator = ()` fonksiyonun ismiyle kullanildigi gibi ile de kullanilabilir. `func()` olarak cagirilan fonksiyon `(&func)()` yazildiginda da cagirilir. Oyleyse `func` fonksiyonunun adresini bir fonksiyon pointerina atayip onla da cagirabilirdik.

    ```c
    void func(void);

    int main ()
    {
        void(*fp)(void) = &func; //fp points func now. 
        fp();//calls the func
    }
    ```

- Fonksiyon cagrisinin fonksiyon gostericisi uzerinden yapilmasi cok sik kullanilan bir metoddur.  
- Fonksiyon pointeri en son hangi fonksiyonun adresini almissa, fonksiyon pointeri ile o fonksiyon cagirilir.
- Haliyle fonksiyon pointer'i ismine bakarak hangi fonksiyonun cagirilacagi runtime'da belli olur.
- `void func(int (*)(int))`: `func` fonksiyonun parametresi geri donus degeri ve aldigi arguman `int` olan bir fonksiyon gostericisidir:

    ```c
    int square(int a)
    {
        return a * a;
    }  

    int multiply_2(int a)
    {
        return a * 2;
    }  

    void func(int (*fp)(int))
    {
        int result = fp(20);// equals to `square(20)` or `multiply_2(20)` funcs return vals. 
    }

    int main()
    {
        func(&square);//pass square func as an function argument
        func(square); //pass square func as an function argument too
        func(multiply_2) // pass multiply_2 func as an function argument
    }
    ```

- Yukaridaki ornekte `func` fonksiyonunun hangi ciktiyi uretecegi tamamen onun cagirildigi yerde kendisine verilen argumana baglidir, `square` argumanini alir ise 400 `multiply_2` argumanini alir ise 40 doner, haliyle algoritmayi `func` fonksiyonu degil onu cagiranlar belirler. Fonksiyon hangi algoritmayi implemente edecegine karar veremez, sadece ona verileni implemente eder. Bu mekanizma siklikla kullanilir.
- Fonksiyon bildirimleri cogunlukla `typedef` bildirimleri ile fonksiyon adresi turlerine verilen es isimlerle kullanilir. Bunun sebebi aksi turlu cok karmasik bildirimlerin gerekmesi. Gorsel karmasiklik artar hata yapma  riski yukselir.

    ```c
    typedef int (*FPTR)(const char*,const char*); 
    void *bar(int (*fpx)(const char*,const char*),int (* fpy)(const char*,const char*)); //without typedef
    void bar(FPTR fpx, FPTR fpy); //with typedef
    ```

- Sonuc olarak genellikle function pointer'lar typedef(es isim) ile kullanilmalidir.
- Fonksiyonlar function pointer ile cagirilirken `*` kullanilmasi sart degildir `*fp() = fp()` ancak `*fp()` ile cagirmak `fp` isminin fonksiyon ismi degil adres ismi oldugunu vurgulamak icin kullanildigini gosterir.
- Yukaridaki duruma uygun sekilde bir function pointer ile fonksiyonu cagirirken operatorlerin oncelik tablosu dikkate alinmalidir. Sozgelimi fonksiyon cagirma operatoru `()` icerik operatorunden `*` oncelikli oldugu icin icerik operatoru ile cagirilan fonksiyon `*fp()` seklinde degil `(*fp)()` seklinde cagirilmalidir.
- Fonksiyon pointerlarinin en sik kullanildigi yerlerden birisi generic fonksiyonlardir - turden bagimsiz fonksiyonlar
- `qsort` bu fonksiyonlara ornek ve en sik kullanilanlardan biridir. Turden bagimsiz olarak bir diziyi siralar.
- `qsort`'un tanimi soyledir:

    ```c
    void qsort(void *vpa, // adress of array that will be sorted
            size_t size, // size of array         
            size_t sz, // size of element type of array    
            int(*fp)(const void *, const void *) //used to compare two of elements of array - has sa me convention with strcmp
                )
    ```

- Dorduncu parametre olan fonksiyonu biz yaziyoruz, yani `qsort` generic ancak kullandigi compare foksiyonu customdir.
- Haliyle dizinin turune gore bir compare fonksiyonu yazilir bu fonksiyon `qsort`'a verilmelidir. Fonksiyonun prototipi void * eleman alsa da iceride ilgili typecast islemi yapilmalidir

## 39 Fonksiyon Pointer'lari(Callback) - 2

- Fonksiyonu cagiran fonksiyonlara `client` denir.
- Callback mekanizmasinda cagiran fonksiyon soyle dusunulebilir: Ben parametreler ve bu parametreleri kullanacak fonksiyonun alirim ve generic olarak her tur parametre ve onlari kullacak olan fonksiyonun adresini alabilirim, islemi bana verilen fonksiyona yaptiririm ve onun bana verdigi donus degerini dogrudan ya da dolayli olarak cikti ederim.
- Function pointer array, mantiksal iliskiye sahip olan dizileri gruplandirmak ve onlarin arasinda dolasmak icin kullanilan bir yapidir.
- Ayni nesne ustunde farkli fonksiyonlar ile operasyon yapmak icin kullanilmaktadir.
- `int (*a)(int)` turunden elemanlari olan bir fonksiyon arrayi `int (*a[10])(int)` ile tanimlanir.
- Bunu typedef ile yapmak icin `typedef int(*FPTEST)(int)` tur es ismi ile adlandirilmis fonksiyon pointer'dan `FPTEST[10]` diyerek ayni ture sahip birden fazla fonksiyonun adresini bir dizide tutabiliriz. `FPTEST a[] = {&isupper, &islower,...}` gibi. Bu diziden 5 indisli fonkisyona `a[5]('A')` sekli nde erisilebilir.
- Kutuphanelerde cok sik kullanilan bir Callback kullanim ornegi: Bir fonksiyon default davranis olarak bir fonksiyonu cagiriyor. Ornegin `terminate` fonksiyonu default olarak abort islevini cagirir. Ancak kutuphane ismi `set_terminate` olan bir islev verir. `set_terminate` islevinin yaptigi fonksiyonu degistirmek icin kullanilabilir, boylece kutuphanedeki default davranisi degistirmek mumkun olur.
- 1.13'te kaldim
