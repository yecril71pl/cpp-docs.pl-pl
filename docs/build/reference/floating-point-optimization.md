---
title: Microsoft Visual C++ zmiennoprzecinkowa optymalizacji | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 03/09/2018
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 35c9263fa6252469124eefb0dfd575ef5bd2ac34
ms.sourcegitcommit: 5e932a0e110e80bc241e5f69e3a1a7504bfab1f3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/21/2018
ms.locfileid: "34422748"
---
# <a name="microsoft-visual-c-floating-point-optimization"></a>Microsoft Visual C++ optymalizacji liczb zmiennoprzecinkowych

Uzyskać dojścia do dotyczące optymalizacji liczb zmiennoprzecinkowych kodu za pomocą kompilatora Microsoft C++ metodę zarządzania semantykę zmiennoprzecinkową. Tworzenie programów szybkiego przy jednoczesnym zapewnieniu jej wykonanie tylko bezpiecznych optymalizacji kodu liczb zmiennoprzecinkowych.

## <a name="optimization-of-floating-point-code-in-c"></a>Optymalizacji liczb zmiennoprzecinkowych kodu w języku C++

Optymalizacja kompilatora C++ nie tylko tłumaczy kodu źródłowego na kod maszynowy, tworzy instrukcje maszyny w taki sposób, aby zwiększyć wydajność i/lub zmniejszyć rozmiar. Niestety wielu typowych optymalizacje nie są zawsze bezpieczne, gdy jest stosowany do obliczenia liczb zmiennoprzecinkowych. Dobrym przykładem może być widoczny z następującego algorytmu podsumowania pobranych z Kowalski Dominik, "Co co komputer naukowca powinien wiedzieć o Floating-Point arytmetycznego", *obliczeniowych ankiet*, marca 1991 pg. 203:

```cpp
float KahanSum( const float A[], int n )
{
   float sum=0, C=0, Y, T;
   for (int i=0; i<n; i++)
   {
      Y = A[i] - C;
      T = sum + Y;
      C = T - sum - Y;
      sum = T;
   }
   return sum;
}
```

Ta funkcja dodaje n **float** wartości w tablicy wektor `A`. W treści pętli algorytm oblicza wartość "naprawa", która jest następnie stosowany do następnego kroku podsumowanie. Ta metoda, znacznie ogranicza zbiorczą błędów zaokrąglania porównaniu proste podsumowanie, zachowując O(n) czasu złożoności.

Kompilator języka C++ prosty może przyjęto założenie, że zmiennoprzecinkowe arytmetyczne postępuje te same zasady algebraicznych jako liczba rzeczywista arytmetyczne. Takie kompilator może następnie błędnego stwierdzą, że

> C = T - sum - Y == > (suma + Y) - sum - Y == > 0;

Oznacza to, że wartość postrzegana c jest zawsze stałą równą zero. Jeśli ta wartość stałej jest następnie propagowany do kolejnych wyrażenia, treści pętli zostanie zmniejszona do prostych podsumowania. Aby była precyzyjna,

> Y = [i] - C == > Y = [i]<br/>T = Suma + Y == > T = suma + [i]<br/>Suma = T == > Suma = suma + [i]

W związku z tym w kompilatorze prostego, logiczną transformacji `KahanSum` byłoby funkcji:

```cpp
float KahanSum( const float A[], int n )
{
   float sum=0; // C, Y & T are now unused
   for (int i=0; i<n; i++)
      sum = sum + A[i];
   return sum;
}
```

Mimo że przekształcone algorytm jest szybsze, *wcale nie jest dokładne reprezentację zamiar programisty*. Korekcja błędów dokładnie przygotowanego ma całkowicie usunięte, a możemy są pozostawione z algorytmem podsumowania proste i bezpośrednie jego skojarzony błąd.

Oczywiście zaawansowane kompilatora C++ wiedział, że algebraicznych reguły z rzeczywistym arytmetyczne nie zwykle dotyczą arytmetyczne zmiennoprzecinkowych. Jednak nawet zaawansowane kompilatora C++ może nadal niepoprawnie zinterpretować zamiar programisty.

Należy wziąć pod uwagę wspólnej optymalizacji, podejmowanych w celu przechowywania dowolną liczbę wartości w rejestrach, jak to możliwe (o nazwie "rejestracja" wartość). W `KahanSum` przykład tego rodzaju optymalizacji może podejmować wielokrotne próby przebiegała zmienne `C`, `Y` i `T` ponieważ są używane tylko w treści pętli. Jeśli dokładność rejestru 52bits (dwa razy) zamiast 23bits (jeden), tego rodzaju optymalizacji skutecznie typu wspiera `C`, `Y` i `T` na typ **podwójne**. Jeśli zmienna sum nie jest również zarejestrowany, pozostanie zakodowanym w pojedynczej precyzji. Przekształca to semantykę `KahanSum` dla następujących

```cpp
float KahanSum( const float A[], int n )
{
   float sum=0;
   double C=0, Y, T; // now held in-register
   for (int i=0; i<n; i++)
   {
      Y = A[i] - C;
      T = sum + Y;
      C = T - sum - Y;
      sum = (float) T;
   }
   return sum;
}
```

Mimo że `Y`, `T` i `C` teraz są obliczane w wyższej dokładności mniej dokładne wynik, w zależności od wartości w nowe kodowanie może powodować `A[]`. Nawet pozornie w związku z tym nieszkodliwe optymalizacje może mieć konsekwencje ujemna.

Tego rodzaju optymalizacji problemów nie są ograniczone do kodu zmiennoprzecinkowe "trudnych". Nawet prostego algorytmy zmiennoprzecinkowej może zakończyć się niepowodzeniem, zoptymalizowane niepoprawnie. Należy wziąć pod uwagę algorytm proste i bezpośrednie podsumowania:

```cpp
float Sum( const float A[], int n )
{
   float sum=0;
   for (int i=0; i<n; i++)
      sum = sum + A[i];
   return sum;
}
```

Ponieważ niektóre jednostki zmiennoprzecinkowe są w stanie jednocześnie wykonania wielu operacji, wybrać Uwzględnij optymalizacji skalarne zmniejszenie kompilatora. Tego rodzaju optymalizacji skutecznie przekształca prostych funkcji Sum z powyższych w następujących czynności:

```cpp
float Sum( const float A[], int n )
{
   int n4 = n-n%4; // or n4=n4&(~3)
   int i;
   float sum=0, sum1=0, sum2=0, sum3=0;
   for (i=0; i<n4; i+=4)
   {
      sum = sum + A[i];
      sum1 = sum1 + A[i+1];
      sum2 = sum2 + A[i+2];
      sum3 = sum3 + A[i+3];
   }
   sum = sum + sum1 + sum2 + sum3;
   for (; i<n; i++)
      sum = sum + A[i];
   return sum;
}
```

Funkcja obsługuje teraz udostępnia cztery oddzielne, które mogą być jednocześnie przetwarzane w każdym kroku. Zoptymalizowane funkcji ma teraz znacznie szybsze, ale zoptymalizowane wyniki mogą być zupełnie różne, niezoptymalizowaną wyników. W wprowadzeniem tej zmiany, kompilator zakłada, że asocjacyjnej dodanie zmiennoprzecinkowe; oznacza to że te dwa wyrażenia są równoważne: `(a + b) + c == a + (b + c)`. Jednak kojarzenie nie zawsze ma wartość true dla liczb zmiennoprzecinkowych. Zamiast obliczania podsumowania jako:

```cpp
sum = A[0]+A[1]+A[2]+...+A[n-1];
```

Po przekształceniu funkcja teraz oblicza wynik w postaci

```cpp
sum = (A[0]+A[4]+A[8]+...)
    + (A[1]+A[5]+A[9]+...)
    + (A[2]+A[6]+A[10]+...)
    + (A[3]+A[7]+A[11]+...);
```

Dla niektórych wartości `A[]`, inną kolejność operacji dodawania może dać nieoczekiwane wyniki. Do dalszego skomplikować sprawach, niektóre programistów wybrać przewidzieć takie optymalizacji i odpowiednio skorygować ich. W takim przypadku program można utworzyć tablicy `A` w innej kolejności, tak aby suma zoptymalizowane tworzy oczekiwanych rezultatów. Ponadto w wielu sytuacjach dokładność zoptymalizowane wynik może być "wystarczająco blisko". Jest to szczególnie istotne podczas optymalizacji zalety atrakcyjnych szybkości. Gier, na przykład wymagać znacznie przyspieszyć, jak to możliwe, ale często nie wymagają bardzo dokładne obliczeń zmiennoprzecinkowych. Osoby podejmujące decyzje kompilatora musi w związku z tym mechanizm umożliwiający deweloperom sterowanie często różnych celów szybkość i dokładność.

Niektóre kompilatory rozpoznać zależności między szybkość i dokładność, podając oddzielne przełącznika każdego rodzaju optymalizacji. Dzięki temu deweloperzy mogą wyłączyć funkcje optymalizacji, które powodują zmiany zmiennoprzecinkowe dokładność dla określonej aplikacji. Gdy to rozwiązanie może oferować wysokiego stopnia kontroli nad kompilatora, wprowadzono kilka dodatkowych problemów:

- Nie często jest jasne, który zmienia, aby włączyć lub wyłączyć.
- Wyłączanie pojedynczego optymalizacją może niekorzystnie wpłynąć na wydajność kodu z systemem innym niż zmiennoprzecinkowych.
- Każdy dodatkowego przełącznik wiąże się z wielu nowych połączeń przełącznika; liczbę kombinacji szybko staje się niewygodna.

Dlatego podczas zapewnienie oddzielnymi przełącznikami dla każdego optymalizacji mogą wydawać się atrakcyjne, za pomocą takich kompilatory może być skomplikowane i zawodnych.

Oferują wiele kompilatorów C++ *spójności* model zmiennoprzecinkowy (za pośrednictwem **/Op** lub **/fltconsistency** przełącznika) który umożliwia deweloperom tworzenie programów zgodne z ścisłą semantykę zmiennoprzecinkową. Wykonujących, ten model zapobiega użyciu większości optymalizacje na obliczenia liczb zmiennoprzecinkowych zezwalając te optymalizacje dla kodu z systemem innym niż punkt zmiennoprzecinkową kompilatora. Jednak model spójności ma ciemny po stronie. Aby zwracają wyniki przewidywalną na różnych architektur FPU niemal wszystkich wdrożeń **/Op** round wyrażenia pośredniego użytkownikowi określona precyzja; na przykład, należy wziąć pod uwagę poniższe wyrażenie:

```cpp
float a, b, c, d, e;
// . . .
a = b * c + d * e;
```

Aby można było utworzyć spójne i powtarzalne wyniki, w obszarze **/Op**, to wyrażenie jest obliczane tak, jakby zostały wdrożone w następujący sposób:

```cpp
float x = b  *c;
float y = d * e;
a = x + y;
```

Wynik końcowy teraz odczuwa błędów zaokrąglania pojedynczej precyzji *w każdym kroku obliczenie wyrażenia*. Chociaż ten interpretacji ściśle nie Podziel żadnych reguł semantykę języka C++, praktycznie nigdy nie jest najlepszym sposobem obliczać wyrażeń zmiennoprzecinkowych. Jest zazwyczaj bardziej pożądane obliczeniowe pośrednich wyników w możliwie dokładność jak jest to możliwe. Na przykład byłoby lepiej można obliczyć wyrażenia `a = b * c + d * e` w większą dokładność, podobnie jak w

```cpp
double x = b * c;
double y = d * e;
double z = x + y;
a = (float)z;
```

lub jeszcze lepiej

```cpp
long double x = b * c;
long double y = d * e
long double z = x + y;
a = (float)z;
```

Podczas obliczania wyników pośrednich w większą dokładność, wynik końcowy jest znacznie bardziej dokładne. Ironically przyjmując modelu spójności prawdopodobieństwo wystąpienia błędu zwiększa się mówiąc, gdy użytkownik próbuje zmniejszyć błędu przez wyłączenie optymalizacji niebezpieczne. W związku z tym modelem spójności poważnie może zmniejszyć wydajność przy jednoczesnym zapewnieniu żadnej gwarancji, zwiększenia dokładności. Programistom numeryczny poważny to wygląda podobnie jak bardzo dobre zależnościami i jest główną przyczyną czy modelu nie ogólnie również Odebrano.

Począwszy od wersji 8.0 (Visual C++ 2005®), Microsoft C++ kompilatora zapewnia znacznie lepszą alternatywę. Umożliwia deweloperom wybierz jedną z trzech trybów zmiennoprzecinkowe ogólne: fp: precise, fp:fast i fp: strict.

- W obszarze fp: precise, tylko optymalizacje bezpieczne odbywa się na kod zmiennoprzecinkowych i, w odróżnieniu od **/Op**, pośrednie obliczenia spójnie są wykonywane na najwyższym dokładność praktyczne.
- Tryb FP:Fast zwalnia zmiennoprzecinkowe reguły, co zapewnia bardziej agresywną optymalizacji kosztem dokładności.
- FP: tryb z ograniczeniami zawiera ogólne poprawność fp: precise podczas włączania semantyki fp wyjątek i uniemożliwia niedozwolony przekształcenia obecności zmian środowiska FPU (np. zmiany dokładność rejestru, zaokrąglania kierunek itp.).

Semantyka wyjątek zmiennoprzecinkowy, którego można kontrolować niezależnie przez przełącznik wiersza polecenia lub pragma kompilatora; Domyślnie semantyki zmiennoprzecinkowych wyjątków są wyłączone w obszarze fp: dokładne i włączona w obszarze fp: strict. Kompilator również zapewnia kontrolę nad FPU środowisko czułość i niektórych zmiennoprzecinkowe optymalizacje określonych, takich jak skrótów. Ten model proste zapewnia deweloperom dużą kontrolę nad kompilacji kodu zmiennoprzecinkowe bez ponoszenia odpowiedzialności za dużo przełączniki kompilatora lub Perspektywa niepożądane skutki uboczne.

## <a name="the-fpprecise-mode-for-floating-point-semantics"></a>Fp: tryb dokładne semantykę zmiennoprzecinkową

Domyślny tryb semantykę zmiennoprzecinkową jest fp: precise. Po wybraniu tego trybu kompilator ściśle działa zgodnie z zestawem zasad bezpieczeństwa podczas optymalizacji operacji zmiennoprzecinkowych. Te zasady pozwalają na kompilator, aby wygenerować kod maszynowy wydajne przy zachowaniu dokładność obliczeń zmiennoprzecinkowych. Aby ułatwić produkcji fast programów, fp: model dokładne wyłącza semantyki wyjątków dotyczących liczb zmiennoprzecinkowych (chociaż są one może być jawnie włączone). Wybrany fp przez firmę Microsoft: dokładne jako domyślny tryb liczb zmiennoprzecinkowych, ponieważ tworzy on zarówno szybkich i dokładnych programów.

Jawnie żądać fp: trybie ścisłym przy użyciu kompilatora wiersza polecenia, użyj [/FP: precise](fp-specify-floating-point-behavior.md) przełącznika:

> Cl/FP: precise source.cpp

To nakazuje kompilatorowi używanie fp: dokładne semantyki podczas generowania kodu dla pliku source.cpp. Fp: dokładne modelu również może być wywoływana na poszczególnych funkcji funkcji przy użyciu [pragma kompilatora float_control](#the-float-control-pragma).

W obszarze fp: trybie ścisłym kompilator nigdy nie wykonuje wszystkie funkcje optymalizacji, które perturb dokładność obliczeń zmiennoprzecinkowych. Kompilator zawsze zaokrągla poprawnie w przypisania, typecasts i wywołania funkcji i pośredniego zaokrąglania spójnie odbędzie się w tej samej precyzji jak rejestruje FPU. Optymalizacje bezpieczne, takich jak skrótów, są domyślnie włączone. Semantyka wyjątku i FPU środowisko czułość są domyślnie wyłączone.

|FP: dokładne semantyki|Wyjaśnienie|
|-|-|
|Zaokrąglanie semantyki|Jawne zaokrąglania w przypisania, typecasts i wywołania funkcji. Zostaną obliczone wyrażenia pośredniego na dokładność rejestru.|
|Algebraicznych przekształcenia|Ścisłego przestrzegania z systemem innym niż łączny, podziału algebraiczną liczb zmiennoprzecinkowych, chyba że transformację jest zawsze gwarancji działają tak samo.|
|Skrótów|Dozwolone domyślnie. Aby uzyskać więcej informacji, zobacz sekcję [fp_contract pragma](#the-fp-contract-pragma).|
|Kolejność obliczania liczb zmiennoprzecinkowych|Kompilator może zmienić kolejność obliczania wyrażeń zmiennoprzecinkowych, pod warunkiem, że wyniki końcowe nie zostały zmienione.|
|Dostęp do środowiska FPU|Domyślnie wyłączone. Aby uzyskać więcej informacji, zobacz sekcję [fenv_access pragma](#the-fenv-access-pragma). Przyjęto, że domyślna dokładność i tryb zaokrąglania.|
|Semantyka wyjątków dotyczących liczb zmiennoprzecinkowych|Domyślnie wyłączone. Aby uzyskać więcej informacji, zobacz [/FP: except](fp-specify-floating-point-behavior.md).|

### <a name="rounding-semantics-for-floating-point-expressions-under-fpprecise"></a>Zaokrąglanie semantyka wyrażeń liczb zmiennoprzecinkowych w obszarze fp: precise

Fp: dokładne modelu zawsze wykonuje obliczenia pośredniego na najwyższym dokładność praktyczne, jawnie zaokrąglania tylko w niektórych punktach Obliczanie wyrażenia. Precyzji określony użytkownik zawsze Zaokrąglenie w czterech miejscach: () w przypadku przydziału, (b) podczas rzutowanie typu, (c) podczas wartość zmiennoprzecinkowa jest przekazywany jako argument do funkcji oraz (d) Jeśli wartość zmiennoprzecinkowa jest zwracana z Funkcja. Ponieważ pośredniego obliczenia są zawsze wykonywane na dokładność rejestru, dokładność pośrednich wyników jest zależne od platformy (chociaż dokładności będzie zawsze równa co najmniej precyzyjne jako użytkownik określony dokładności).

Należy wziąć pod uwagę wyrażenia przypisania w poniższym kodzie. Wyrażenie po prawej stronie przypisania operatora "=" zostanie obliczony na dokładność rejestru i jawnie zaokrąglona na typ po lewej stronie przypisania.

```cpp
float a, b, c, d;
double x;
...
x = a*b + c*d;
```

jest obliczana jako

```cpp
float a, b, c, d;
double x;
...
register tmp1 = a*b;
register tmp2 = c*d;
register tmp3 = tmp1+tmp2;
x = (double) tmp3;
```

Aby jawnie zaokrąglona wynik pośredni, należy wprowadzić typecast. Na przykład, jeśli poprzedni kod jest modyfikowany przez dodanie jawne rzutowanie typu, pośrednie wyrażenia (c * d) zostanie zaokrąglony typ typecast.

```cpp
float a, b, c, d;
double x;
// . . .
x = a*b + (float)(c*d);
```

jest obliczana jako

```cpp
float a, b, c, d;
double x;
// . . .
register tmp1 = a*b;
float tmp2 = c*d;
register tmp3 = tmp1+tmp2;
x = (double) tmp3;
```

Jeden wpływ tej metody zaokrąglania jest niektórych transformacji pozornie równoważne nie faktycznie identyczne semantyki. Na przykład następujące przekształcania dzieli wyrażenia jednej do dwóch wyrażeń przypisania.

```cpp
float a, b, c, d;
// . . .
a = b*(c+d);
```

NIE jest odpowiednikiem

```cpp
float a, b, c, d;
// . . .
a = c+d;
a = b*a;
```

Podobnie:

```cpp
a = b*(c+d);
```

NIE jest odpowiednikiem

```cpp
a = b*(a=c+d);
```

Te kodowania nie ma semantykę równoważne, ponieważ każdy drugi kodowania wprowadziły operatora przypisania dodatkowe, a tym samym dodatkowe zaokrąglania punktu.

Gdy funkcja zwraca wartość zmiennoprzecinkową, wartość zostanie zaokrąglony typu funkcji. Jeśli wartość zmiennoprzecinkowa jest przekazywany jako parametr do funkcji, wartość zostanie zaokrąglony typ parametru. Na przykład:

```cpp
float sumsqr(float a, float b)
{
   return a*a + b*b;
}
```

jest obliczana jako

```cpp
float sumsqr(float a, float b)
{
    register tmp3 = a*a;
    register tmp4 = b*b;
    register tmp5 = tmp3+tmp4;
    return (float) tmp5;
}
```

Podobnie:

```cpp
float w, x, y, z;
double c;
...
c = symsqr(w*x+y, z);
```

jest obliczana jako

```cpp
float x, y, z;
double c;
...
register tmp1 = w*x;
register tmp2 = tmp1+y;
float tmp3 = tmp2;
c = symsqr( tmp3, z);
```

### <a name="architecture-specific-rounding-under-fpprecise"></a>Zaokrąglanie architektury w obszarze fp: precise

|Procesor|Zaokrąglanie dokładności dla pośredniego wyrażeń|
|-|-|
|x86|Pośredni wyrażenia są obliczane w domyślnej 53-bitowa precyzja z rozszerzonego zakresu zapewnionego przez wykładnik 16-bitowych. Gdy te wartości 53:16 są "rozrzucone" do pamięci (co może się zdarzyć podczas wywołania funkcji), rozszerzone wykładnika zakres będzie zawężony do 11 bitów. Oznacza to rozlanej wartości są rzutowane na format standardowe podwójnej precyzji z wykładnik 11-bitowych.<br/>Użytkownik może przełączyć się do rozszerzona dokładność 64-bitowych zaokrąglania pośredniego, zmieniając przy użyciu programu word zmiennoprzecinkowe kontroli `_controlfp` i włączając dostęp do środowiska FPU (zobacz [fenv_access pragma](#the-fenv-access-pragma)). Jednak gdy rozszerzona dokładność wartości rejestru są rozrzucone pamięci, wyniki pośrednie zostanie nadal zaokrąglony podwójnej precyzji.<br/>Jest to określonego semantycznego może ulec zmianie.|
|amd64|FP na amd64 semantyka nieznacznie różnić się od innych platform. Ze względu na wydajność pośrednia operacje są obliczane w najszerszym dokładność którykolwiek argument operacji zamiast na dokładność najszerszych dostępne.  Wymuszenie obliczenia ma zostać obliczony przy użyciu większą dokładność niż argumenty, użytkownicy muszą wprowadzić operacji rzutowania na co najmniej jeden argument wyrażenia podrzędnego.<br/>Jest to określonego semantycznego może ulec zmianie.|

### <a name="algebraic-transformations-under-fpprecise"></a>Algebraicznych przekształcenia w obszarze fp: precise

Gdy fp: trybie ścisłym jest włączone, kompilator nigdy nie będzie wykonywać transformacje algebraicznych *o ile wynik końcowy jest zgodność identyczne*. Wiele znanych reguł algebraicznych arytmetyczne liczba rzeczywista nie zawsze mają dla liczb zmiennoprzecinkowych arytmetyczne. Na przykład poniższe wyrażenia są równoważne dla Reals, ale niekoniecznie w przypadku elementów przestawnych.

|Formularz|Opis|
|-|-|
|`(a+b)+c = a+(b+c)`|Reguła asocjacyjnej do dodania|
|`(a*b)*c = a*(b*c)`|Reguła asocjacyjnej mnożenia|
|`a*(b+c) = a*b + b*c`|Dystrybucji mnożenia przez dodanie|
|`(a+b)(a-b) = a*a-b*b`|Algebraicznych Factoring|
|`a/b = a*(1/b)`|Dzielenie przez odwrotność multiplicative|
|`a*1.0 = a`|Tożsamość mnożenia|

Jak pokazano w przykładzie wprowadzenie przy użyciu funkcji `KahanSum`, kompilator może zechcieć wykonywania różnych przekształceń algebraicznych powodować programy znacznie krócej. Chociaż optymalizacje zależy od takich przekształceń algebraicznych prawie zawsze są niepoprawne, istnieją sytuacji, w których są doskonale bezpieczne. Na przykład czasami jest pożądane, aby zastąpić dzielenie przez *stałej* wartości z mnożenia przez mnożenia odwrotność stałej:

```cpp
const double four = 4.0;
double a, b;
...

a = b/four;
```

Może być konwertowana

```cpp
const double four = 4.0;
const double tmp0 = 1/4.0;
double a, b;
...
a = b*tmp0;
```

Jest to transformację bezpieczne, ponieważ Optymalizator można określić w czasie kompilacji x / 4.0 == x*(1/4.0) dla wszystkich zmiennoprzecinkowych wartości x, w tym infinities i NaN. Zastępując operacji dzielenia mnożenia, kompilator może zapisać kilka cykli — szczególnie w przypadku FPUs bezpośrednio nie implementują dzielenia, które wymagają kompilatorowi Generowanie kombinację zbliżenia odwrotność i dodać mnożenia instrukcje. Kompilator może wykonywać optymalizacji, w obszarze fp: dokładne tylko wtedy, gdy mnożenia zastępczy tworzy dokładnie takie same powoduje jako podziału. Kompilator może także przeprowadzić trivial przekształcenia w obszarze fp: precise, zakładając, że wyniki są identyczne. Należą do nich następujące elementy:

|Formularz|Opis
|-|-|
|`(a+b) == (b+a)`|Reguła przemienne do dodania|
|`(a*b) == (b*a)`|Reguła przemienne mnożenia|
|`1.0*x*y == x*1.0*y == x*y*1.0 == x*y`|Mnożenie przez 1.0|
|`x/1.0*y == x*y/1.0 == x*y`|Dzielenie przez 1.0|
|`2.0*x == x+x`|Mnożenie przez 2.0|

### <a name="contractions-under-fpprecise"></a>Skrótów w obszarze fp: precise

Kluczową funkcją architektury wiele nowoczesnych jednostki zmiennoprzecinkowe jest możliwość wykonywania mnożenia, następuje dodanie jako jedna operacja z pośredniego błąd zaokrąglania. Na przykład firmy Intel Itanium architektura zawiera instrukcje dotyczące każdej z tych trójargumentowy operacji łączenia (*b + c), (* b-c) i (c-a * b), w jednej instrukcji zmiennoprzecinkowych (fma, fms i fnma odpowiednio). Te instrukcje o pojedynczej są szybciej niż wykonywania oddzielnych mnożenia i dodać instrukcje i są bardziej dokładne, ponieważ nie istnieje, bez pośredniego zaokrąglania produktu. Tego rodzaju optymalizacji można znacznie przyspieszyć funkcje zawierające kilka przeplatana mnożenie i Dodaj operacji. Rozważmy na przykład następujący algorytm Oblicza iloczyn dwóch wektorów n wymiarowej kropki.

```cpp
float dotProduct( float x[], float y[], int n )
{
   float p=0.0;
   for (int i=0; i<n; i++)
      p += x[i]*y[i];
   return p;
}
```

Te obliczenia można wykonać szereg mnożenia — Dodawanie instrukcji w postaci p = p + x [i] * y [i].

Optymalizacja zmniejszenia można sterować niezależnie przy użyciu `fp_contract` pragma kompilatora. Domyślnie fp: dokładne model pozwala na skrótów, ponieważ ich poprawić dokładność i szybkości. W obszarze fp: precise, kompilator będzie nigdy nie kontraktu wyrażenia z jawnym zaokrąglania.
Przykłady

```cpp
float a, b, c, d, e, t;
...
d = a*b + c;         // may be contracted
d += a*b;            // may be contracted
d = a*b + e*d;       // may be contracted into a mult followed by a mult-add
etc...

d = (float)a*b + c;  // won't be contracted because of explicit rounding

t = a*b;             // (this assignment rounds a*b to float)
d = t + c;           // won't be contracted because of rounding of a*b
```

### <a name="order-of-floating-point-expression-evaluation-under-fpprecise"></a>Kolejność obliczania wyrażenia liczb zmiennoprzecinkowych w obszarze fp: precise

Funkcje optymalizacji, które zachowują kolejność obliczania wyrażenia zmiennoprzecinkowe zawsze są bezpieczne i w związku z tym są dozwolone w obszarze fp: trybie ścisłym. Należy wziąć pod uwagę następujące funkcję, która oblicza iloczyn dwóch wektorów n wymiarową w pojedynczej precyzji. Pierwszy blok kodu poniżej początkowe funkcje jak mogą być kodowane przez programistę, następuje taką samą funkcję po częściowej optymalizacji rozkręcające pętli.

```cpp
//original function
float dotProduct( float x[], float y[], int n )
{
   float p=0;
   for (int i=0; i<n; i++)
      p += x[i]*y[i];
   return p;
}

//after a partial loop-unrolling
float dotProduct( float x[], float y[], int n )
{
   int n4= n/4*4; // or n4=n&(~3);
   float p=0;
   int i;

   for (i=0; i<n4; i+=4)
   {
      p+=x[i]*y[i];
      p+=x[i+1]*y[i+1];
      p+=x[i+2]*y[i+2];
      p+=x[i+3]*y[i+3];
   }

   // last n%4 elements
   for (; i<n; i++)
      p+=x[i]*y[i];

   return p;
}
```

Główną zaletą ten rodzaj optymalizacji jest zmniejsza liczbę warunkowego rozgałęzianie pętli, o ile 75%. Ponadto przez odpowiednie zwiększenie liczby operacji w treści pętli, kompilator może już więcej możliwości w celu dalszej optymalizacji. Na przykład niektóre FPUs może istnieć możliwość wykonania Dodaj wielokrotnie w p += x [i] * y [i] podczas pobierania jednocześnie wartości x [i + 1] i y [i + 1] do użycia w następnym kroku. Ten rodzaj optymalizacji jest idealnie bezpieczne dla obliczenia liczb zmiennoprzecinkowych, ponieważ zachowuje on kolejność operacji.

Często jest korzystne kompilatora zmienić kolejność wszystkie operacje w celu uzyskania szybszego kodu. Rozważmy następujący kod:

```cpp
double a, b, c, d;
double x, y, z;
...
x = a*a*a + b*b*b + c*c*c;
...
y = a*a + b*b + c*c;
...
z = a + b + c;
```

Reguły semantycznego C++ wskazują program powinna dawać wyników tak, jakby najpierw obliczana x, a następnie y i finally. Załóżmy, że kompilator ma tylko cztery dostępne rejestrów zmiennoprzecinkowych. Kompilator jest wymuszenie obliczeniowe x, y i w kolejności, można wygenerować kod w następujących semantyki:

```cpp
double a, b, c, d;
double x, y, z;
register r0, r1, r2, r3;
...
// Compute x
r0 = a;         // r1 = a*a*a
r1 = r0*r0;
r1 = r1*r0;
r0 = b;         // r2 = b*b*b
r2 = r0*r0;
r2 = r2*r0;
r0 = c;         // r3 = c*c*c
r3 = r0*r0;
r3 = r3*r0;
r0 = r1 + r2;
r0 = r0 + r3;
x = r0;         // x = r1+r2+r3
// . . .
// Compute y
r0 = a;         // r1 = a*a
r1 = r0*r0;
r0 = b;         // r2 = b*b
r2 = r0*r0;
r0 = c;         // r3 = c*c
r3 = r0*r0;
r0 = r1 + r2;
r0 = r0 + r3;
y = r0;         // y = r1+r2+r3
// . . .
// Compute z
r1 = a;
r2 = b;
r3 = c;
r0 = r1 + r2;
r0 = r0 + r3;
z = r0;         // z = r1+r2+r3
```

Istnieje kilka operacji wyraźnie nadmiarowe jest ten typ kodowania. Jeśli kompilator ściśle semantycznego reguł C++, ta kolejność jest konieczne, ponieważ program mogą uzyskiwać dostęp do środowiska FPU między każdym przypisania. Jednak domyślne ustawienia fp: dokładne Zezwalaj kompilator, aby zoptymalizować tak, jakby program nie uzyskiwać dostęp do środowiska, dzięki któremu można zmienić kolejność tych wyrażeń. Następnie jest bezpłatna do usunięcia zwolnienia przez obliczenie trzy wartości w odwrotnej kolejności, w następujący sposób:

```cpp
double a, b, c, d;
double x, y, z;
register r0, r1, r2, r3;
...
// Compute z
r1 = a;
r2 = b;
r3 = c;
r0 = r1+r2;
r0 = r0+r3;
z = r0;
...
// Compute y
r1 = r1*r1;
r2 = r2*r2;
r3 = r3*r3;
r0 = r1+r2;
r0 = r0+r3;
y = r0;
...
// Compute x
r0 = a;
r1 = r1*r0;
r0 = b;
r2 = r2*r0;
r0 = c;
r3 = r3*r0;
r0 = r1+r2;
r0 = r0+r3;
x = r0;
```

Kodowanie jest wyraźnie wyższego poziomu, mając zredukowanie liczby fp instrukcje o niemal 40%. Wyniki dla x, y i są takie same jak poprzednio, ale obliczonym przy mniejsze koszty.

W obszarze fp: precise, kompilator może również *przeplotu* wspólnych wyrażeń podrzędnych aż do uzyskania szybszego kodu. Na przykład kod do obliczenia korzenie równości kwadratowe mogą być zapisane w następujący sposób:

```cpp
double a, b, c, root0, root1;
...
root0 = (-b + sqrt(b*b-4*a*c))/(2*a);
root1 = (-b - sqrt(b*b-4*a*c))/(2*a);
```

Mimo że wyrażenia te różnią się tylko za pomocą jednej operacji, programista może zostały zapisane go ten sposób, aby zagwarantować, że każda wartość głównego będzie obliczana w najwyższym dokładność praktyczne. W obszarze fp: precise, kompilator będzie mógł przeplotu obliczenia root0 i root1, aby usunąć wspólnych wyrażeń podrzędnych bez utraty dokładności. Na przykład następujące zostały usunięte kilka kroków nadmiarowe podczas produkowania dokładnie tego samego odpowiedzi.

```cpp
double a, b, c, root0, root1;
...
register tmp0 = -b;
register tmp1 = sqrt(b*b-4*a*c);
register tmp2 = 2*a;
root0 = (tmp0+tmp1)/tmp2;
root1 = (tmp0-tmp1)/tmp2;
```

Inne optymalizacje mogą próbować przenieść oceny niektórych niezależnych wyrażeń. Należy wziąć pod uwagę następujące algorytmu, który zawiera gałąź warunkowa w treści pętli.

```cpp
vector<double> a(n);
double d, s;
// . . .
for (int i=0; i<n; i++)
{
   if (abs(d)>1.0)
      s = s+a[i]/d;
   else
      s = s+a[i]*d;
}
```

Kompilator może wykryć, że wartość wyrażenia (abs(d) > 1) jest niezmienne w treści pętli. Dzięki temu kompilator "Wózek nośny" if — instrukcja poza ciałem pętli, przekształcania powyższy kod w następujących czynności:

```cpp
vector<double> a(n);
double d, s;
// . . .
if (abs(d)>1.0)
   for (int i=0; i<n; i++)
      s = s+a[i]/d;
else
   for (int i=0; i<n; i++)
      s = s+a[i]*d;
```

Po przekształceniu nie ma gałąź warunkowa w jednym z treści pętli, co znacznie poprawia ogólną wydajność pętli. Ten rodzaj optymalizacji jest idealnie bezpieczne ponieważ obliczania wyrażenia (abs(d) > 1.0) jest niezależna od innych wyrażeń.

Obecności dostęp do środowiska FPU lub wyjątki zmiennoprzecinkowe są contraindicated tego rodzaju optymalizacji, ponieważ one semantycznego przepływ zmian. Takie optymalizacje tylko są dostępne w obszarze fp: trybie ścisłym ponieważ dostęp do środowiska FPU i semantyki zmiennoprzecinkowych wyjątków są domyślnie wyłączone. Funkcje, które uzyskują dostęp do środowiska FPU jawnie można wyłączyć za pomocą takich optymalizacje `fenv_access` pragma kompilatora. Podobnie, należy użyć funkcji przy użyciu wyjątki zmiennoprzecinkowe `float_control(except ... )` pragma kompilatora (lub użyj **/FP: except** przełącznik wiersza polecenia).

Podsumowując, fp: tryb dokładne umożliwia kompilatora, aby zmienić kolejność obliczania wyrażeń zmiennoprzecinkowych, pod warunkiem, że wyniki końcowe nie zostały zmienione oraz że wyniki nie są zależne od środowiska FPU lub na wyjątki zmiennoprzecinkowe.

### <a name="fpu-environment-access-under-fpprecise"></a>Dostęp do środowiska FPU w obszarze fp: precise

Gdy fp: włączony jest tryb dokładne, kompilator przyjęto założenie, że program nie dostępu lub wpływu na środowisko FPU. Jak wspomniano wcześniej, to założenie włącza kompilator, aby zmienić kolejność lub przenieść operacji zmiennoprzecinkowych aby poprawić wydajność w obszarze fp: precise.

Niektóre programy mogą zmienić zmiennoprzecinkowe zaokrąglania kierunek przy użyciu `_controlfp` funkcji. Na przykład niektóre programy obliczeniowe górnej i niższych granic błąd dla operacji arytmetycznych przez wykonanie tej samej obliczenia dwa razy, najpierw podczas zaokrąglania do nieskończoności ujemnej, następnie podczas zaokrąglania do nieskończoności dodatniej. Ponieważ FPU oferują wygodny sposób do sterowania zaokrąglaniem, programisty może zdecydować się na zmianę trybu zaokrąglania przez zmianę środowiska FPU. Poniższy kod oblicza dokładny błąd granica zmiennoprzecinkowe mnożenia przez zmianę środowiska FPU.

```cpp
double a, b, cLower, cUpper;
// . . .
_controlfp( _RC_DOWN, _MCW_RC );    // round to -&infin;
cLower = a*b;
_controlfp( _RC_UP, _MCW_RC );    // round to +&infin;
cUpper = a*b;
_controlfp( _RC_NEAR, _MCW_RC );    // restore rounding mode
```

W obszarze fp: precise, kompilator zawsze przyjęto założenie, domyślnym środowisku FPU tak Optymalizator jest bezpłatna zignorowanie wywołań `_controlfp` i zmniejszyć powyżej przypisania do cUpper = cLower = * b; wyraźnie mogłoby to spowodować zwrócenie niepoprawnych wyników. Aby zapobiec takiej optymalizacji, należy włączyć FPU dostęp do środowiska za pomocą `fenv_access` pragma kompilatora.

Inne programy mogą próbować wykrywać niektórych zmiennoprzecinkowe błędów przez sprawdzenie słowa stanu FPU. Na przykład następujący kod sprawdza warunki dzielenie przez zero i niedokładnymi

```cpp
double a, b, c, r;
float x;
// . . .
_clearfp();
r = (a*b + sqrt(b*b-4*a*c))/(2*a);
if (_statusfp() & _SW_ZERODIVIDE)
   handle divide by zero as a special case
_clearfp();
x = r;
if (_statusfp() & _SW_INEXACT)
   handle inexact error as a special case
etc...
```

W obszarze fp: precise, funkcje optymalizacji, które zmienić kolejność obliczania wyrażenia może zmienić punktów, w których występują pewne błędy. Programy podczas uzyskiwania dostępu do programu word stanu, należy włączyć dostęp do środowiska FPU przy użyciu `fenv_access` pragma kompilatora.

Aby uzyskać więcej informacji, zobacz sekcję [fenv_access pragma](#the-fenv-access-pragma).

### <a name="floating-point-exception-semantics-under-fpprecise"></a>Semantyka zmiennoprzecinkowych wyjątków w obszarze fp: precise

Domyślnie semantyki zmiennoprzecinkowych wyjątków są wyłączone w obszarze fp: precise. Większość programistów C++ wolą obsługę wyjątkowych warunków zmiennoprzecinkowe bez korzystania z systemu i wyjątków języka C++. Ponadto jak podano wcześniej, wyłączenie semantyki zmiennoprzecinkowych wyjątków umożliwia kompilatora większą elastyczność podczas optymalizacji operacji zmiennoprzecinkowych. Użyj jednej **/FP: z wyjątkiem** przełącznika lub `float_control` pragma, aby włączyć semantyki zmiennoprzecinkowych wyjątków za pomocą fp: dokładne modelu.

Aby uzyskać więcej informacji, zobacz sekcję [włączenie semantyki zmiennoprzecinkowych wyjątków](#enabling-floating-point-exception-semantics).

## <a name="the-fpfast-mode-for-floating-point-semantics"></a>Tryb fp:fast semantykę zmiennoprzecinkową

Jeśli włączony jest tryb fp:fast, kompilator zwalnia reguły tego fp: dokładne używa podczas optymalizacji operacji zmiennoprzecinkowych. Ten tryb jest umożliwia kompilatorowi jeszcze bardziej zoptymalizować zmiennoprzecinkowe kodu dla danej szybkości kosztem zmiennoprzecinkowe dokładność i poprawności. Programy, które nie należy polegać na bardzo dokładne obliczenia zmiennoprzecinkowe mogą wystąpić poprawy szybkości znaczących przez włączenie trybu fp:fast.

Tryb zmiennoprzecinkowe fp:fast jest włączone, za pomocą [Fast](fp-specify-floating-point-behavior.md) przełącznika kompilatora wiersza polecenia w następujący sposób:

> source.cpp Fast cl

W tym przykładzie nakazuje kompilatorowi używanie semantyki fp:fast podczas generowania kodu dla pliku source.cpp. Fp:fast model również może być wywoływana na poszczególnych funkcji funkcji przy użyciu `float_control` pragma kompilatora.

Aby uzyskać więcej informacji, zobacz sekcję [float_control pragma](#the-float-control-pragma).

W trybie fp:fast kompilator może wykonywać funkcje optymalizacji, które alter dokładność obliczeń zmiennoprzecinkowych. Kompilator nie może poprawnie zaokrąglona w przypisania, typecasts lub funkcji wywołania i pośredniego zaokrąglania zostanie nie zawsze można wykonać. Zmiennoprzecinkowe optymalizacje określonych, takich jak skrótów, są zawsze włączone. Semantyka zmiennoprzecinkowych wyjątków i FPU środowisko czułość są wyłączone i jest niedostępne.

|Semantyka FP:Fast|Wyjaśnienie
|-|-|
|Zaokrąglanie semantyki|Jawne zaokrąglania w przypisania, typecasts i wywołania funkcji można zignorować.<br/>Pośredni wyrażenia może zostać zaokrąglona w mniej niż zarejestrować dokładność, zgodnie z wymaganiami wydajności.|
|Algebraicznych przekształcenia|Kompilator może przekształcić wyrażenia zgodnie z liczbą rzeczywistą algebraiczną asocjacyjnej, podziału; przekształcenia te nie ma gwarancji być niedokładne lub prawidłowe.|
|Skrótów|Zawsze włączone; Nie można wyłączyć przez wartość dyrektywy pragma `fp_contract`|
|Kolejność obliczania liczb zmiennoprzecinkowych|Kompilator może zmienić kolejność obliczania wyrażeń zmiennoprzecinkowych, nawet wtedy, gdy takie zmiany mogą zmienić końcowego wyniku.|
|Dostęp do środowiska FPU|Wyłączone. Niedostępne|
|Semantyka wyjątków dotyczących liczb zmiennoprzecinkowych|Wyłączone. Niedostępne|

### <a name="rounding-semantics-for-floating-point-expressions-under-fpfast"></a>Semantyka wyrażeń liczb zmiennoprzecinkowych w obszarze fp:fast zaokrąglania

W odróżnieniu od fp: model dokładne, fp:fast model wykonuje obliczenia pośredniego najbardziej wygodne dokładności. Zaokrąglanie w przypisania, typecasts i wywołania funkcji może nie zawsze być przeprowadzane. Na przykład pierwszej funkcji poniżej przedstawiono trzy zmienne pojedynczej precyzji (`C`, `Y` i `T`). Kompilator może wybrać przebiegała tych zmiennych, w celu podwyższania poziomu typu `C`, `Y` i `T` do podwójnej precyzji.

Początkowe funkcje:

```cpp
float KahanSum( const float A[], int n )
{
   float sum=0, C=0, Y, T;
   for (int i=0; i<n; i++)
   {
      Y = A[i] - C;
      T = sum + Y;
      C = T - sum - Y;
      sum = T;
   }
   return sum;
}
```

Zmienne w zarejestrowany:

```cpp
float KahanSum( const float A[], int n )
{
   float sum=0;
   double C=0, Y, T; // now held in-register
   for (int i=0; i<n; i++)
   {
      Y = A[i] - C;
      T = sum + Y;
      C = T - sum - Y;
      sum = (float) T;
   }
   return sum;
}
```

W tym przykładzie fp:fast ma subverted celem pierwotnej funkcji. Ostatni wynik w zmiennej zoptymalizowanych pod kątem `sum`, może być dość perturbed z prawidłowego wyniku.

W obszarze fp:fast kompilator zwykle będzie podejmować próby obsługi co najmniej dokładność określona przez kod źródłowy. Jednak w niektórych przypadkach kompilator może wybrać do wykonania pośredniego wyrażenia w *obniżyć dokładności* niż określona w kodzie źródłowym. Na przykład pierwszy blok kodu poniżej wywołuje wersji podwójnej precyzji funkcji pierwiastek kwadratowy. W obszarze fp:fast w pewnych okolicznościach, takie jak kiedy wynik i argumenty funkcji są jawnie rzutować pojedynczej precyzji, kompilator może nastąpić Zastąp wywołanie podwójnej precyzji `sqrt` wywołaniem o pojedynczej precyzji `sqrtf`funkcji. Ponieważ rzutowania Sprawdź, czy wartość, przechodząc do `sqrt` i wyjście wartości są zaokrąglane do pojedynczej precyzji, spowoduje to zmianę tylko miejsca zaokrąglania. Jeśli wartość do sqrt była wartość podwójnej precyzji i kompilator wykonać tego przekształcenia więcej niż połowy bitów dokładność może być nieprawidłowa.

Oryginalny — funkcja

```cpp
double sqrt(double);
// . . .
double a, b, c;
float f1, f2;
// . . .
float length = (float)sqrt((float)(a*a + b*b + c*c));
float sum = (float) ((double)f1 + (double)f2);
```

Zoptymalizowane — funkcja

```cpp
float sqrtf(float)...
// . . .
double a, b, c;
float f1, f2;
// . . .
double tmp0 = a*a + b*b + c*c;
float tmp1 = tmp0;    // round of parameter value
float length = sqrtf(tmp1); // rounded sqrt result
float sum = f1 + f2;
```

Mimo że mniej dokładne, tego rodzaju optymalizacji mogą być szczególnie przydatne, gdy procesorów, które zapewniają pojedynczej precyzji, wersje wewnętrznej funkcji takich jak `sqrt`. Po prostu dokładnie po kompilator użyje tych optymalizacje jest zależna zarówno kontekst, jak i platformy.

Ponadto jest nie gwarantuje spójności Precision obliczeniach pośrednich, które mogą być wykonywane na dowolnym poziomie dokładności dostępne do kompilatora. Mimo że kompilator będzie próbował zachować co najmniej poziom dokładności określone przez kod, fp:fast umożliwia Optymalizator przypisanie elementu podrzędnego obliczenia pośredniego aby wygenerować kod maszynowy szybsze lub mniejszy. Na przykład kompilator może jeszcze bardziej zoptymalizować kod z powyższych zostać zaokrąglona niektóre pośredniego mnożenia do pojedynczej precyzji.

```cpp
float sqrtf(float)...
// . . .
double a, b, c;
float f1, f2;
// . . .
float tmp0 = a*a;     // round intermediate a*a to single-precision
float tmp1 = b*b;     // round intermediate b*b to single-precision
double tmp2 = c*c;    // do NOT round intermediate c*c to single-precision
float tmp3 = tmp0 + tmp1 + tmp2;
float length = sqrtf(tmp3);
float sum = f1 + f2;
```

Tego rodzaju zaokrąglania dodatkowe mogą wynikać z za pomocą dolnej dokładności liczb zmiennoprzecinkowych jednostki, takich jak SSE2, do wykonania niektórych pośrednich obliczeń. Dokładność zaokrąglania fp:fast w związku z tym jest zależne od platformy; Kod, który kompiluje się do jednego procesora zawsze mogą nie działać dla innego procesora. Zostanie pozostawiony do użytkownika w celu ustalenia, jeśli szybkość korzyści przeważają problemów dokładności.

W przypadku szczególnie powodować problemy dla określonych funkcji optymalizacji fp:fast zmiennoprzecinkowe tryb można lokalnie przełączyć fp: precise przy użyciu `float_control` pragma kompilatora.


### <a name="algebraic-transformations-under-fpfast"></a>Algebraicznych przekształcenia w obszarze fp:fast

Tryb fp:fast umożliwia kompilatora do wykonania niektórych, niebezpieczne algebraicznych przekształcenia na liczby zmiennoprzecinkowe punktu wyrażenia. Na przykład w obszarze fp:fast można zastosować następujące optymalizacje niebezpieczne.

||||
|-|-|-|
|Oryginalny kod|Krok #1|Krok #2
|`double a, b, c;`<br/>`double x, y, z;`<br/><br/>`y = (a + b);`<br/>`z = y – a – b;`<br/><br/>`c = x – z;`<br/><br/>`c = x * z;`<br/><br/>`c = x - z;`<br/><br/>`c = x + z;`<br/><br/>`c = z-x;`|`double a, b, c;`<br/>`double x, y, z;`<br/><br/>`y = (a + b);`<br/>`z = 0;`<br/><br/>`c = x – 0;`<br/><br/>`c = x * 0;`<br/><br/>`c = x - 0;`<br/><br/>`c = x + 0;`<br/><br/>`c = 0 - x;`|`double a, b, c;`<br/>`double x, y, z;`<br/><br/>`y = (a + b);`<br/>`z = 0;`<br/><br/>`c = x;`<br/><br/>`c = 0;`<br/><br/>`c = x;`<br/><br/>`c = x;`<br/><br/>`c = -x;`|

W kroku 1, kompilator przestrzega, który `z = y – a – b` jest zawsze równa zero. Chociaż jest technicznie nieprawidłowy obserwacji, jest dozwolone na mocy fp:fast. Kompilator następnie propaguje stała wartość zero do każdego późniejsze użycie zmiennej z. W kroku 2, kompilator dodatkowo optymalizuje obserwując który `x - 0 == x`, `x * 0 == 0`itp. Ponownie nawet jeśli te uwagi nie są ściśle prawidłowe, zezwala na fp:fast. Kod zoptymalizowany teraz jest znacznie szybsze, ale mogą również być znacznie mniej dokładne lub nawet niepoprawne.

Żadnego z następujących reguł algebraicznych (unsafe) mogą zostać wykorzystane przez optymalizator, jeśli włączony jest tryb fp:fast:

|||
|-|-|
|Formularz|Opis|
|`(a + b) + c = a + (b + c)`|Reguła asocjacyjnej do dodania|
|`(a * b) * c = a * (b * c)`|Reguła asocjacyjnej mnożenia|
|`a * (b + c) = a * b + b * c`|Dystrybucji mnożenia przez dodanie|
|`(a + b)(a - b) = a * a - b * b`|Algebraicznych Factoring|
|`a / b = a * (1 / b)`|Dzielenie przez odwrotność multiplicative|
|`a * 1.0 = a, a / 1.0 = a`|Tożsamość mnożenia|
|`a ± 0.0 = a, 0.0 - a = -a`|Tożsamość dodatku|
|`a / a = 1.0, a - a = 0.0`|Anulowanie|

W przypadku szczególnie powodować problemy dla danej funkcji optymalizacji fp:fast zmiennoprzecinkowe tryb można lokalnie przełączyć fp: precise przy użyciu `float_control` pragma kompilatora.

### <a name="order-of-floating-point-expression-evaluation-under-fpfast"></a>Kolejność obliczania wyrażenia liczb zmiennoprzecinkowych w obszarze fp:fast

W odróżnieniu od fp: precise, fp:fast umożliwia kompilatora zmienić kolejność operacji zmiennoprzecinkowych aż do uzyskania szybszego kodu. W związku z tym niektóre optymalizacji pod fp:fast nie może zachować zamierzonej kolejności wyrażeń. Na przykład należy wziąć pod uwagę następujące funkcji, który oblicza iloczyn dwóch wektorów wymiarów n.

```cpp
float dotProduct( float x[], float y[],
                  int n )
{
   float p=0;
   for (int i=0; i<n; i++)
      p += x[i]*y[i];
   return p;
}
```

W obszarze fp:fast, optymalizator może wykonywać skalarne zmniejszenie `dotProduct` funkcji skutecznie Przekształcanie funkcji w następujący sposób:

```cpp
float dotProduct( float x[], float y[],int n )
{
    int n4= n/4*4; // or n4=n&(~3);
    float p=0, p2=0, p3=0, p4=0;
    int i;

    for (i=0; i<n4; i+=4)
    {
        p+=x[i]*y[i];
        p2+=x[i+1]*y[i+1];
        p3+=x[i+2]*y[i+2];
        p4+=x[i+3]*y[i+3];
    }
    p+=p2+p3+p4;

    // last n%4 elements
    for (; i<n; i++)
    p+=x[i]*y[i];

    return p;
}
```

W wersji zoptymalizowane funkcji czterech dostępnych oddzielny produkt jednocześnie zarejestrowane i następnie dodane do siebie. Tego rodzaju optymalizacji można przyspieszyć przy obliczaniu `dotProduct` na podstawie tak, jak współczynnik cztery w zależności od procesora docelowych, ale wynik końcowy mogą być niedokładne sposób utrudniający bezużyteczny. Jeśli takie optymalizacje są szczególnie powodować problemy dla jednej funkcji lub jednostce tłumaczenia, tryb zmiennoprzecinkowe można lokalnie przełączyć fp: precise przy użyciu `float_control` pragma kompilatora.

## <a name="the-fpstrict-mode-for-floating-point-semantics"></a>Fp: strict tryb semantykę zmiennoprzecinkową

Gdy fp: tryb z ograniczeniami jest włączone, kompilator opiera się na te same zasady tego fp: dokładne używa podczas optymalizacji operacji zmiennoprzecinkowych. Ten tryb również włącza semantyki zmiennoprzecinkowych wyjątków i liter w środowisku FPU i wyłącza niektórych optymalizacji, takich jak skrótów. Jest to najbardziej rygorystyczne tryb.

Fp: tryb z ograniczeniami zmiennoprzecinkowej jest włączone, za pomocą [/FP: strict](fp-specify-floating-point-behavior.md) przełącznika kompilatora wiersza polecenia w następujący sposób:

> Cl/FP: strict source.cpp

W tym przykładzie nakazuje kompilatorowi używanie fp: strict semantyki podczas generowania kodu dla pliku source.cpp. Fp: strict modelu również może być wywoływana na poszczególnych funkcji funkcji przy użyciu `float_control` pragma kompilatora.

Aby uzyskać więcej informacji, zobacz sekcję [float_control pragma](#the-float-control-pragma).

W obszarze fp: tryb z ograniczeniami, kompilator nigdy nie wykonuje wszystkie funkcje optymalizacji, które perturb dokładność obliczeń zmiennoprzecinkowych. Kompilator zawsze zaokrągla poprawnie w przypisania, typecasts i wywołania funkcji i pośredniego zaokrąglania spójnie odbędzie się w tej samej precyzji jak rejestruje FPU. Semantyka zmiennoprzecinkowych wyjątków i FPU środowisko czułość są domyślnie włączone. Pewne optymalizacje, takich jak skrótów, są wyłączone, ponieważ kompilator nie może zagwarantować poprawność w każdym przypadku.

|FP: strict semantyki|Wyjaśnienie|
|-|-|
|Zaokrąglanie semantyki|Jawne zaokrąglania w przypisania, typecasts i wywołania funkcji<br/>Zostaną obliczone wyrażenia pośredniego na dokładność rejestru.<br/>Taki sam jak fp: precise|
|Algebraicznych przekształcenia|Ścisłego przestrzegania z systemem innym niż łączny, podziału algebraiczną liczb zmiennoprzecinkowych, chyba że transformację jest zawsze gwarancji działają tak samo.<br/>Taki sam jak fp: precise|
|Skrótów|Zawsze wyłączone|
|Kolejność obliczania liczb zmiennoprzecinkowych|Kompilator nie spowoduje zmiany kolejności obliczania wyrażeń liczb zmiennoprzecinkowych|
|Dostęp do środowiska FPU|Zawsze włączone.|
|Semantyka wyjątków dotyczących liczb zmiennoprzecinkowych|Domyślnie włączony.|

### <a name="floating-point-exception-semantics-under-fpstrict"></a>Semantyka zmiennoprzecinkowych wyjątków w obszarze fp: strict

Domyślnie semantyki zmiennoprzecinkowych wyjątków są włączone w obszarze fp: strict modelu. Aby wyłączyć te semantyki, użyj **/FP: oprócz-** przełącznika lub wprowadzenie `float_control(except, off)` pragma.

Aby uzyskać więcej informacji, zobacz sekcje [włączenie semantyki zmiennoprzecinkowych wyjątków](#enabling-floating-point-exception-semantics) i [float_control Pragma](#the-float-control-pragma).

## <a name="the-fenvaccess-pragma"></a>Fenv_access pragma

Sposób użycia:

```cpp
#pragma fenv_access( [ on  | off ] )
```

[Fenv_access](../../preprocessor/fenv-access.md) pragma umożliwia kompilatorowi wprowadzić niektóre funkcje optymalizacji, które może mógł wykorzystać FPU flagę testy i zmiany trybu FPU. Gdy stan `fenv_access` jest wyłączona, można założyć, kompilator obowiązują tryby FPU domyślne i flagi FPU nie są sprawdzane pod. Domyślnie dostęp do środowiska jest wyłączone dla fp: trybie ścisłym, chociaż może być jawnie włączone, za pomocą tej pragmy. W obszarze fp: strict, `fenv_access` jest zawsze włączona i nie można wyłączyć. W obszarze fp:fast `fenv_access` jest zawsze wyłączona i nie można włączyć.

Zgodnie z opisem w fp: dokładne sekcji niektórych programiści mogą zmienić zmiennoprzecinkowe przy użyciu kierunek zaokrąglania `_controlfp` funkcji. Na przykład można obliczyć granic obliczania górnego i dolnego błędu dla operacji arytmetycznych, niektóre programy wykonaj dwa razy, tym samym obliczenia najpierw podczas zaokrąglania do nieskończoności ujemnej, a następnie podczas zaokrąglania do nieskończoności dodatniej. Ponieważ FPU oferują wygodny sposób do sterowania zaokrąglaniem, programisty może zdecydować się na zmianę trybu zaokrąglania przez zmianę środowiska FPU. Poniższy kod oblicza dokładny błąd granica zmiennoprzecinkowe mnożenia przez zmianę środowiska FPU.

```cpp
double a, b, cLower, cUpper;
// . . .
_controlfp( _RC_DOWN, _MCW_RC );    // round to -infinity
cLower = a*b;
_controlfp( _RC_UP, _MCW_RC );       // round to +infinity
cUpper = a*b;
_controlfp( _RC_NEAR, _MCW_RC );    // restore rounding mode
```

Po wyłączeniu `fenv_access` pragma umożliwia kompilatorowi założono domyślnego środowiska FPU; w związku z tym Optymalizator zwolnieniu Ignoruj wywołań `_controlfp` i przypisania powyżej, aby ograniczyć `cUpper = cLower = a*b`. Gdy włączone, jednak `fenv_access` uniemożliwia takie optymalizacji.

Programy również sprawdzić, czy słowa stanu FPU do wykrywania określonych błędów zmiennoprzecinkowych. Na przykład następujący kod sprawdza warunki dzielenie przez zero i niedokładnymi

```cpp
double a, b, c, r;
float x;
// . . .
_clearfp();
r = (a*b + sqrt(b*b-4*a*c))/(2*a);
if (_statusfp() & _SW_ZERODIVIDE)
   handle divide by zero as a special case
_clearfp();
x = (a*b + sqrt(b*b-4*a*c))/(2*a);
if (_statusfp() & _SW_INEXACT)
   handle inexact error as a special case
etc...
```

Gdy `fenv_access` jest wyłączone, kompilator może zmienić kolejność wykonywania wyrażenia liczb zmiennoprzecinkowych, w związku z tym prawdopodobnie subverting sprawdza stan FPU. Włączanie `fenv_access` uniemożliwia takie optymalizacji.

## <a name="the-fpcontract-pragma"></a>Fp_contract pragma

Sposób użycia:

```cpp
#pragma fp_contract( [ on | off ] )
```

Zgodnie z opisem w fp: sekcja dokładne, zmniejszenia jest podstawowych funkcji architektury dla wielu nowoczesnych jednostek zmiennoprzecinkowych. Skrótów zapewniają możliwość wykonywania mnożenia, następuje dodanie jako jedna operacja z pośredniego błąd zaokrąglania. Te instrukcje o pojedynczej są szybciej niż wykonywania oddzielnych mnożenia i dodać instrukcje i są bardziej dokładne, ponieważ nie istnieje, bez pośredniego zaokrąglania produktu. Operacja umowie można oblicza wartość `(a*b+c)` tak, jakby operacjami zostały obliczona nieskończona dokładnością, a następnie jest zaokrąglana do najbliższej liczby zmiennoprzecinkowej. Tego rodzaju optymalizacji można znacznie przyspieszyć funkcje zawierające kilka przeplatana mnożenie i Dodaj operacji. Rozważmy na przykład następujący algorytm Oblicza iloczyn dwóch wektorów n wymiarowej kropki.

```cpp
float dotProduct( float x[], float y[], int n )
{
   float p=0.0;
   for (int i=0; i<n; i++)
      p += x[i]*y[i];
   return p;
}
```

Te obliczenia można wykonać szereg instrukcje formularza należy pomnożyć Dodaj `p = p + x[i]*y[i]`.

[Fp_contract](../../preprocessor/fp-contract.md) pragma Określa, czy są zawarte zmiennoprzecinkowe wyrażenia. Domyślnie fp: trybie ścisłym umożliwia skrótów ponieważ poprawiają dokładność i szybkości. Tryb fp:fast zawsze włączoną skrótów. Jednakże, ponieważ skrótów można mógł wykorzystać jawne wykrywania błędów, `fp_contract` pragma jest zawsze wyłączona w obszarze fp: tryb z ograniczeniami. Przykłady wyrażeń, które mogą być nabytej kiedy `fp_contract` pragma jest włączona:

```cpp
float a, b, c, d, e, t;
...
d = a*b + c;         // may be contracted
d += a*b;            // may be contracted
d = a*b + e*d;       // may be contracted into a mult followed by a mult-add etc...

d = (float)a*b + c;  // won't be contracted because of explicit rounding

t = a*b;             // (this assignment rounds a*b to float)
d = t + c;           // won't be contracted because of rounding of a*b
```

## <a name="the-floatcontrol-pragma"></a>Float_control pragma

**/FP: dokładne**, **Fast**, **/FP: strict** i **/FP: except** semantykę zmiennoprzecinkową w pliku przez plik sterowania przełączników podstawy. [Float_control](../../preprocessor/float-control.md) pragma zapewnia takie kontrolę na podstawie funkcja przez funkcję.

Sposób użycia:

```cpp
#pragma float_control(push)
#pragma float_control(pop)
#pragma float_control( precise, on | off [, push] )
#pragma float_control( except, on | off [, push] )
```

Pragma `float_control(push)` i `float_control(pop)` odpowiednio wypychania i pop bieżący stan trybu zmiennoprzecinkowych i opcji wyjątku na stosie. Należy pamiętać, że stan `fenv_access` i `fp_contract` nie dotyczy pragma `pragma float_control(push/pop)`.

Wywoływanie pragma `float_control(precise, on)` spowoduje włączenie i `float_control(precise, off)` spowoduje wyłączenie w trybie ścisłym semantyki. Podobnie, pragma `float_control(except, on)` spowoduje włączenie i `float_control(except, off)` spowoduje wyłączenie semantyki wyjątku. Semantyki wyjątek można włączyć tylko w przypadku, gdy dokładne semantyki są również włączone. Gdy opcjonalny `push` argument jest obecny, stanów `float_control` opcje są usuwane przed zmiana semantyki.

### <a name="setting-the-floating-point-semantic-mode-on-a-function-by-function-basis"></a>Ustawianie zmiennoprzecinkowe trybu semantycznych na podstawie funkcja funkcji

Przełączniki wiersza polecenia są faktycznie skrótowa do ustawiania czterech różnych zmiennoprzecinkowych pragm. Aby wybrać jawnie określonym trybie zmiennoprzecinkowe semantycznych na podstawie funkcja przez funkcję, wybierz każdego z czterech opcji zmiennoprzecinkowych pragm zgodnie z opisem w poniższej tabeli:

||||||
|-|-|-|-|-|
||float_control(Precise)|float_control(EXCEPT)|fp_contract|fenv_access|
|/ FP: strict|on|on|Wyłączanie|on|
|/ FP: strict/FP: except-|on|Wyłączanie|Wyłączanie|on|
|/ FP: precise|on|Wyłączanie|on|Wyłączanie|
|/ FP: precise/FP: except|on|on|on|Wyłączanie|
|Fast|Wyłączanie|Wyłączanie|on|Wyłączanie|

Na przykład następujące jawnie umożliwia fp:fast semantyki.

```cpp
#pragma float_control( except, off )   // disable exception semantics
#pragma float_control( precise, off )  // disable precise semantics
#pragma fp_contract(on)                // enable contractions
#pragma fenv_access(off)               // disable fpu environment sensitivity
```

> [!Note]
> Semantyka wyjątków muszą zostać wyłączone przed wyłączeniem semantyki "precise".

## <a name="enabling-floating-point-exception-semantics"></a>Włączanie semantyki wyjątków dotyczących liczb zmiennoprzecinkowych

Niektórych wyjątkowe zmiennoprzecinkowe warunki, takie jak dzielenie przez zero, może spowodować FPU sygnalizują wyjątek sprzętu. Wyjątki zmiennoprzecinkowe są domyślnie wyłączone. Wyjątki zmiennoprzecinkowe są włączone, modyfikując słowa formantu FPU z `_controlfp` funkcji. Na przykład poniższy kod umożliwia dzielenie przez zero zmiennoprzecinkowych wyjątków:

```cpp
_clearfp(); // always call _clearfp before
            // enabling/unmasking a FPU exception
_controlfp( _EM_ZERODIVIDE, _MCW_EM );
```

Po włączeniu wyjątek dzielenie przez zero żadnej operacji dzielenia z denominator równej zero spowoduje zostać zgłoszony wyjątek FPU.

Aby przywrócić domyślny tryb FPU słowa formantu, należy wywołać `_controlfp(_CW_DEFAULT, ~0)`.

Włączanie semantyki zmiennoprzecinkowych wyjątków z **/FP: except** flaga nie jest to samo co włączenie wyjątki zmiennoprzecinkowe. Po włączeniu semantyki zmiennoprzecinkowych wyjątków kompilator muszą uwzględniać możliwość, że żadnych operacji zmiennoprzecinkowej może zgłosić wyjątek. Ponieważ FPU jest jednostką oddzielne procesora, instrukcje wykonywania na FPU mogą być wykonywane równocześnie z instrukcji dotyczących innych jednostek.

Po włączeniu zmiennoprzecinkowych wyjątków FPU zatrzymuje wykonywanie instrukcji ataku i sygnalizuje warunek wyjątkowych, ustawiając słowa stanu FPU. Gdy Procesor osiągnie następnej instrukcji zmiennoprzecinkowych, najpierw sprawdza wszystkie oczekujące wyjątki FPU. Jeśli istnieje oczekujące wyjątek, procesor traps przez wywołanie metody obsługi wyjątków obsługiwanych przez System operacyjny. Oznacza to, że podczas operacji zmiennoprzecinkowej napotka warunek wyjątkowych, odpowiedni wyjątek nie zostanie wykryty do czasu następnej operacji zmiennoprzecinkowej jest wykonywana. Na przykład następujący kod traps wyjątek dzielenie przez zero:

```cpp
double a, b, c;
// . . .
// ...unmasking of FPU exceptions omitted...
__try
{
   b/c; // assume c==0.0
   printf("This line shouldn't be reached when c==0.0\n");
   c = 2.0*b;
}
__except( EXCEPTION_EXECUTE_HANDLER )
{
   printf("SEH Exception Detected\n");
}
// . . .
```

Występuje, jeśli warunek dzielenie przez zero w wyrażeniu = b/c FPU nie pułapki/Zgłoś wyjątek do czasu następnej operacji zmiennoprzecinkowych w wyrażeniu 2.0 * b. Powoduje to następujące dane wyjściowe:

```Output
This line shouldn't be reached when c==0.0
SEH Exception Detected
```

Printf odpowiadający pierwszy wiersz dane wyjściowe powinny nie został osiągnięty; został osiągnięty, ponieważ zmiennoprzecinkowych wyjątków spowodowanych wyrażenie b/c nie został zgłoszony aż do osiągnięcia 2.0 wykonywania * b. Aby zgłosić wyjątek zaraz po wykonaniu b/c, kompilator wprowadzić instrukcji "Czekaj":

```cpp
// . . .
   __try
   {
      b/c; // assume this expression will cause a "divide-by-zero" exception
      __asm fwait;
      printf("This line shouldn't be reached when c==0.0\n");
      c = 2.0*b;
   }
// . . .
```

Ta instrukcja "Czekaj" wymusza procesora do synchronizacji ze stanem FPU i obsługiwać wszystkie wyjątki oczekujące. Kompilator będzie generować tylko te "Czekaj" instrukcje po włączeniu semantykę zmiennoprzecinkową. Gdy te semantyki są wyłączone, są domyślnie, programy mogą wystąpić błędy synchronicity, podobny do przedstawionego powyżej, używając wyjątki zmiennoprzecinkowe.

Po włączeniu semantykę zmiennoprzecinkową, kompilator nie wprowadzi tylko instrukcje "Czekaj", również uniemożliwi kompilator nielegalnego optymalizacji liczb zmiennoprzecinkowych kodu obecności możliwych wyjątków. W tym wszelkie transformacje, których alter punktów, w których są zgłaszane wyjątki. Ze względu na te czynniki włączenie semantykę zmiennoprzecinkową znacznie może zmniejszyć wydajność wygenerowanego kodu maszyny, w związku z tym zmniejszenie wydajności aplikacji.

Semantyka zmiennoprzecinkowych wyjątków są domyślnie włączone w obszarze fp: tryb z ograniczeniami. Aby włączyć te semantyki w fp: trybie ścisłym dodać **/FP: oprócz** przełączyć się do kompilatora wiersza polecenia. Semantyka zmiennoprzecinkowych wyjątków również może być włączony i wyłączone na poszczególnych funkcji funkcji przy użyciu `float_control` pragma.

### <a name="floating-point-exceptions-as-c-exceptions"></a>Wyjątki zmiennoprzecinkowe jako wyjątki języka C++

Wszystkie wyjątki sprzętowe, wyjątki zmiennoprzecinkowe nie powodują bardzo wyjątek języka C++, ale zamiast tego wywołać wyjątków strukturalnych. Aby mapować wyjątki strukturalne liczb zmiennoprzecinkowych wyjątków języka C++, użytkownicy mogą stać się niestandardowych translator wyjątków SEH. Najpierw należy wprowadzić wyjątek języka C++, odpowiadający każdej zmiennoprzecinkowych wyjątków:

```cpp
class float_exception : public std::exception {};

class fe_denormal_operand : public float_exception {};
class fe_divide_by_zero : public float_exception {};
class fe_inexact_result : public float_exception {};
class fe_invalid_operation : public float_exception {};
class fe_overflow : public float_exception {};
class fe_stack_check : public float_exception {};
class fe_underflow : public float_exception {};
```

Następnie wprowadzić funkcji tłumaczenia wykryje zmiennoprzecinkowych wyjątków SEH i throw odpowiednich wyjątków C++. Aby użyć tej funkcji, należy ustawić translator obsługi wyjątków strukturalnych bieżącego wątku procesu z [_set_se_translator —](../../c-runtime-library/reference/set-se-translator.md) funkcji z biblioteki środowiska uruchomieniowego.

```cpp
void se_fe_trans_func( unsigned int u, EXCEPTION_POINTERS* pExp )
{
    switch (u)
    {
    case STATUS_FLOAT_DENORMAL_OPERAND:   throw fe_denormal_operand();
    case STATUS_FLOAT_DIVIDE_BY_ZERO:     throw fe_divide_by_zero();
   etc...
    };
}
// . . .
_set_se_translator(se_fe_trans_func);
```

Po zainicjowaniu to mapowanie wyjątki zmiennoprzecinkowe będą zachowywać się tak, jakby są wyjątków języka C++. Na przykład:

```cpp
try
{
   // floating-point code that might throw divide-by-zero
   // or other floating-point exception
}
catch(fe_divide_by_zero)
{
    cout << "fe_divide_by_zero exception detected" << endl;
}
catch(float_exception)
{
    cout << "float_exception exception detected" << endl;
}
```

## <a name="references"></a>Odwołania

[Co naukowca co komputer powinien wiedzieć o zmiennoprzecinkowe arytmetyczne](http://pages.cs.wisc.edu/~david/courses/cs552/S12/handouts/goldberg-floating-point.pdf) przez Dominika Kowalski.

## <a name="see-also"></a>Zobacz także

[Optymalizacja kodu](optimizing-your-code.md)<br/>
