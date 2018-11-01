---
title: Microsoft Visual C++ Optymalizacja liczb zmiennoprzecinkowych
ms.date: 03/09/2018
ms.topic: conceptual
ms.openlocfilehash: 6e297cebb4982b293e86885815436c4120d903cd
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50504302"
---
# <a name="microsoft-visual-c-floating-point-optimization"></a>Microsoft Visual C++ optymalizacji zmiennoprzecinkowych

Uzyskaj dojście optymalizacji kodu zmiennoprzecinkowego, za pomocą kompilatora Microsoft C++ metodę zarządzania semantykę liczb zmiennopozycyjnych. Utwórz szybko programy przy jednoczesnym zapewnieniu, że tylko bezpiecznych optymalizacje są wykonywane na kod zmiennoprzecinkowy.

## <a name="optimization-of-floating-point-code-in-c"></a>Optymalizacja kodu zmiennoprzecinkowego w języku C++

Optymalizacja kompilatora języka C++ nie tylko dokonuje translacji kodu źródłowego do kodu maszynowego, organizuje instrukcje maszynę w taki sposób, aby zwiększyć wydajność i/lub Zmniejsz rozmiar. Niestety wiele typowych optymalizacji nie są zawsze bezpieczne, po zastosowaniu do obliczeń zmiennoprzecinkowych. Dobrym przykładem są widoczne przy użyciu następującego algorytmu sumą pobranych z Davidem Kowalski, "Co co komputer Analityk powinien wiedzieć o zmiennopozycyjna arytmetyczne", *obliczeń ankiet*, marca 1991 pg. 203:

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

Ta funkcja dodaje n **float** wartości w wektorze tablicy `A`. W treści pętli algorytm oblicza wartość "Poprawka", co jest następnie stosowane do następnego kroku podsumowania. Ta metoda znacznie zmniejsza zbiorczą błędy zaokrągleń w porównaniu do prostych sumowania, przy zachowaniu O(n) czasu złożoności.

Kompilator języka C++ naiwni zakładać, że arytmetyki zmiennoprzecinkowej te same reguły algebraicznych jako liczba rzeczywista operacje arytmetyczne. Takie kompilator może następnie błędnie stwierdzą, że

> C = T - sum - Y == > (suma + Y) — Suma - Y == > 0.

Oznacza to, że wartość postrzegany c jest zawsze stałą wartość zero. Jeśli ta wartość stała jest następnie propagowany do kolejnych wyrażeń, ciało pętli jest skrócony do prostych sumą. Aby była precyzyjna,

> Y = [i] - C == > Y = [i]<br/>T = Suma + Y == > T = suma + [i]<br/>Suma = T == > Suma = suma + [i]

W efekcie kompilatorowi naiwni, logiczne przekształcania `KahanSum` funkcji:

```cpp
float KahanSum( const float A[], int n )
{
   float sum=0; // C, Y & T are now unused
   for (int i=0; i<n; i++)
      sum = sum + A[i];
   return sum;
}
```

Mimo że przekształcone algorytm jest szybsze, *w ogóle nie stanowi dokładne odzwierciedlenia zamiar programisty*. Korekcja błędów dokładnie przygotowane została usunięta całkowicie, a teraz pozostawiliśmy z algorytmem proste, bezpośrednie sumą z jego skojarzony błąd.

Oczywiście zaawansowanych kompilator języka C++ wiedział, że algebraicznych reguły o rzeczywistym arytmetyczne ogólnie dotyczy arytmetyki zmiennoprzecinkowej. Jednak nawet zaawansowane kompilator języka C++ mogą nadal niepoprawnie interpretować zamiar programisty.

Rozważmy typowe optymalizacji, które podejmuje próbę przechowywać dowolną liczbę wartości w rejestrach, jak to możliwe (o nazwie "rejestrowanie" wartości). W `KahanSum` przykład tego rodzaju optymalizacji może próbować przebiegała zmienne `C`, `Y` i `T` ponieważ są one używane tylko w treści pętli. Dokładność Zarejestruj się w przypadku 52bits (podwójny) zamiast 23bits (pojedyncze), tego rodzaju optymalizacji skutecznie typu promuje `C`, `Y` i `T` na typ **double**. Jeśli zmienna suma nie jest również przechowywane w rejestrze procesora, pozostanie zakodowany w pojedynczej precyzji. To przekształca semantykę `KahanSum` dla następujących

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

Mimo że `Y`, `T` i `C` teraz są obliczane na większą precyzję nowe kodowanie może powodować mniej dokładne wyniki, w zależności od wartości w `A[]`. Dlatego nawet pozornie nieszkodliwe optymalizacje może wiązać z negatywnymi skutkami.

Tego rodzaju problemów z optymalizacją nie są ograniczone do "skomplikowanych" kodu zmiennoprzecinkowego. Nawet prostych algorytmy zmiennoprzecinkowych może zakończyć się niepowodzeniem, gdy nieprawidłowo zoptymalizowane pod kątem. Należy wziąć pod uwagę algorytm prosty, sumą bezpośrednie:

```cpp
float Sum( const float A[], int n )
{
   float sum=0;
   for (int i=0; i<n; i++)
      sum = sum + A[i];
   return sum;
}
```

Ponieważ niektóre jednostki zmiennoprzecinkowej może wykonać wiele operacji jednocześnie, dzięki którym można zaangażować optymalizacji redukcja skalaru wybrać kompilatora. Tego rodzaju optymalizacji skutecznie przekształcający prostą funkcję Sum z powyższych następujące czynności:

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

Funkcja obsługuje teraz udostępnia cztery oddzielne, które mogą być przetwarzane jednocześnie w każdym kroku. Mimo że funkcja zoptymalizowane teraz znacznie szybciej, zoptymalizowane wyniki mogą być bardzo różne wyniki niezoptymalizowany. Wprowadzając tę zmianę, kompilator zakłada, że asocjacyjnych dodanie zmiennoprzecinkowych; oznacza to że te dwa wyrażenia są równoważne: `(a + b) + c == a + (b + c)`. Jednak łączność nie zawsze ma wartość true dla liczb zmiennoprzecinkowych. Zamiast przetwarzania sumą jako:

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

W przypadku niektórych wartości z `A[]`, inną kolejność operacji dodawania może powodować nieoczekiwane rezultaty. Do dalszego skomplikować, niektórych programistów mają możliwość przewidywanie takich optymalizacje i odpowiednio kompensacji je. W takim przypadku program można utworzyć tablicy `A` w innej kolejności, tak aby suma zoptymalizowane daje oczekiwanych wyników. Ponadto w wielu sytuacjach dokładność zoptymalizowane wynik może być "wystarczająco bliskie". Jest to szczególnie istotne w przypadku, gdy Optymalizacja zalety atrakcyjnych szybkości. Gry wideo, na przykład wymagać, ponieważ znacznie przyspieszyć, jak to możliwe, ale często nie wymagają wysokiej dokładne obliczeń zmiennoprzecinkowych. Twórcy kompilatora muszą więc zapewniać mechanizm dla programistów kontrolować często rozbieżnymi celów szybkość i dokładność.

Niektóre kompilatory rozpoznać zależności między szybkość i dokładność, zapewniając przełącznika osobne dla każdego typu optymalizacji. Umożliwia to deweloperom Wyłącz optymalizacje, które powodują zmiany zmiennoprzecinkowych dokładność dla określonej aplikacji. Chociaż to rozwiązanie może zaoferować wysokiego stopnia kontroli nad kompilator, wprowadza kilka dodatkowych problemów:

- Często jest niejasny przełącza się do włączania lub wyłączania.
- Wyłączenie dowolnego pojedynczego optymalizacji może niekorzystnie wpłynąć na wydajność kodu bez zmiennoprzecinkowego.
- Każdy przełącznik dodatkowe wiąże się wielu nowych połączeń przełącznika; liczbę kombinacji szybko staje się niewydolna.

Dlatego podczas zapewnienie oddzielnymi przełącznikami dla każdego optymalizacji może wydawać się ich orkiestracją, przy użyciu takich kompilatorów może być skomplikowane i zawodnych.

Oferuje wiele kompilatorów języka C++ *spójności* model zmiennoprzecinkowy (za pośrednictwem **/Op** lub **/fltconsistency** przełącznika) co pozwala deweloperom tworzyć programy zgodne za pomocą ścisłą semantykę liczb zmiennopozycyjnych. Wykonujących, w tym modelu zabezpiecza kompilator przed przy użyciu większość optymalizacji na obliczeń zmiennoprzecinkowych, zapewniając te optymalizacje kodu bez punktu zmiennoprzecinkowego. Model spójności ma jednak dark-side. Aby zwrócić przewidywalne wyniki w różnych architektur FPU, prawie wszystkich implementacjach **/Op** round wyrażeń pośrednich użytkownikowi określona precyzja; na przykład rozważmy następujące wyrażenie:

```cpp
float a, b, c, d, e;
// . . .
a = b * c + d * e;
```

W celu uzyskania spójnego i powtarzalnego wyników w obszarze **/Op**, to wyrażenie oceniane tak, jakby zostały zaimplementowane w następujący sposób:

```cpp
float x = b  *c;
float y = d * e;
a = x + y;
```

Wynik końcowy teraz odczuwa błędy zaokrągleń pojedynczej precyzji *w każdym kroku obliczając wartość wyrażenia*. Mimo że ten interpretacji ściśle nie przerywa wszystkie reguły semantyki C++, prawie nigdy nie jest najlepszym sposobem obliczać wyrażeń zmiennoprzecinkowych. Jest zazwyczaj bardziej pożądane obliczeń pośrednich wyników w możliwie dokładności praktycznych. Na przykład byłoby lepiej do obliczenia wyrażenia `a = b * c + d * e` w większą precyzję, na przykład

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

Podczas obliczania wyników pośrednich w większą precyzję, wynik końcowy jest znacznie bardziej dokładne. Ironically przyjmując model spójności, prawdopodobieństwo wystąpienia błędu zwiększa się dokładnie, gdy użytkownik próbuje zmniejszyć błąd, wyłączając optymalizacje niebezpieczne. Tym samym modelu spójności naszych użytkowników bardzo poważnie może zmniejszyć wydajność przy jednoczesnym zapewnieniu żadnej gwarancji, zwiększenia dokładności. Programistom poważne wartości liczbowych to nie wydawać się to z kompromisem bardzo dobre i jest głównym powodem, czy model nie zazwyczaj dobrze Odebrano.

Począwszy od wersji 8.0 (Visual C++ 2005®), Microsoft C++ kompilator zapewnia znacznie lepszą alternatywą. Umożliwia programistom wybierz jedną z trzech trybów zmiennoprzecinkowych ogólne: fp: precise, FP: Fast i fp: strict.

- W obszarze fp: precise, tylko bezpiecznych optymalizacje wykonywane są kod zmiennoprzecinkowy, a także, w odróżnieniu od **/Op**, obliczeń pośrednich niezmienne spisywała się na najwyższym dokładności praktyczne.
- Tryb FP: Fast zwalnia zmiennoprzecinkowych reguły, co zapewnia bardziej agresywnego optymalizacji kosztem dokładności.
- FP: tryb z ograniczeniami zapewnia ogólne poprawność fp: precise podczas włączania semantykę wyjątku fp i zapobieganie niedozwolony przekształcenia obecności zmiany środowiska FPU (np. zmiany precyzji rejestru, zaokrąglaniem kierunku itp.).

Semantyka wyjątek zmiennoprzecinkowy, którego można kontrolować niezależnie, przełącznik wiersza polecenia lub dyrektywy kompilatora; Domyślnie semantykę wyjątku zmiennoprzecinkowego są wyłączone w obszarze fp: dokładne i włączone w obszarze fp: strict. Kompilator zapewnia również kontrolę nad czułości środowiska FPU i niektórych określonych optymalizacji zmiennopozycyjnych, takich jak skrótów. Ten model proste daje deweloperom dużą kontrolę nad kompilacji kodu zmiennoprzecinkowego, bez obciążeń zbyt wiele przełączniki kompilatora lub Perspektywa niepożądane skutki uboczne.

## <a name="the-fpprecise-mode-for-floating-point-semantics"></a>Fp: precise tryb semantykę zmiennoprzecinkową

Domyślny tryb semantykę liczb zmiennopozycyjnych to fp: precise. Po wybraniu tego trybu kompilator ściśle zgodna z zestawem zasad bezpieczeństwa podczas optymalizacji operacji zmiennopozycyjnych. Te reguły zezwala kompilatorowi generowanie kodu maszynowego wydajne przy zachowaniu dokładność obliczeń zmiennoprzecinkowych. Ułatwiające produkcji szybkie programy, fp: precise modelu wyłącza semantykę wyjątku zmiennoprzecinkowego (mimo że można ją jawnie włączyć). Wybrany fp przez firmę Microsoft: dokładne jak domyślny tryb zmiennoprzecinkowych, ponieważ powoduje to szybkie i dokładne programów.

Na jawne żądanie fp: trybie ścisłym, za pomocą kompilatora wiersza polecenia, użyj [/FP: precise](fp-specify-floating-point-behavior.md) przełącznika:

> Cl/FP: precise source.cpp

To powoduje, że kompilator korzystać fp: precise semantyki podczas generowania kodu dla pliku source.cpp. Fp: precyzyjnego modelu można również wywołać w poszczególnych funkcji przez funkcję przy użyciu [dyrektywy kompilatora float_control](#the-float-control-pragma).

W obszarze fp: trybie ścisłym, kompilator nigdy nie wykonuje żadnych optymalizacje, które perturb dokładność obliczeń zmiennoprzecinkowych. Kompilator zawsze zostanie niepoprawnie zaokrąglać w przypisania, rzutowaniach typu i wywołaniach funkcji i pośredniego zaokrąglania spójnie odbędzie się w tej samej precyzji jak rejestruje FPU. Optymalizacje bezpieczne, takich jak skrótów, są domyślnie włączone. Semantykę wyjątku i czułość środowiska FPU są domyślnie wyłączone.

|FP: precise semantyki|Wyjaśnienie|
|-|-|
|Zaokrąglanie semantyki|Jawne Zaokrąglenie w przypisania, rzutowaniach typu, a funkcja wywołuje. Wyrażeń pośrednich zostanie oceniona dokładności rejestru.|
|Przekształcenia algebraiczne|Ścisłego przestrzegania-asocjacyjnych, bez podziału algebry zmiennoprzecinkowych, chyba że przekształcenie gwarantuje zawsze działają tak samo.|
|Skrótów|Dozwolone domyślnie. Aby uzyskać więcej informacji, zobacz sekcję [fp_contract pragma](#the-fp-contract-pragma).|
|Kolejność obliczania zmiennoprzecinkowych|Kompilator może zmienić kolejność obliczania wyrażeń liczb zmiennopozycyjnych, pod warunkiem, że wyniki końcowe nie zostały zmienione.|
|Dostęp do środowiska FPU|Domyślnie wyłączone. Aby uzyskać więcej informacji, zobacz sekcję [fenv_access pragma](#the-fenv-access-pragma). Przyjęto, że domyślna dokładność i trybu zaokrąglania.|
|Semantyka wyjątków dotyczących liczb zmiennoprzecinkowych|Domyślnie wyłączone. Aby uzyskać więcej informacji, zobacz [/FP: except](fp-specify-floating-point-behavior.md).|

### <a name="rounding-semantics-for-floating-point-expressions-under-fpprecise"></a>Zaokrąglanie semantykę zmiennoprzecinkową wyrażeń w obszarze fp: precise

Fp: precyzyjnego modelu zawsze wykonuje pośrednich obliczeń na najwyższym dokładności praktyczne, jawnie zaokrąglania tylko w określonych punktach Obliczanie wyrażenia. Z dokładnością do określonej przez użytkownika zawsze jest zaokrąglana w czterech miejsc: () w przypadku przydziału, (b) Jeśli rzutowanie typu jest wykonywane, (c) po wartość zmiennoprzecinkowa jest przekazywany jako argument do funkcji oraz (d) kiedy wartość zmiennoprzecinkowa jest zwracana z Funkcja. Ponieważ pośrednich obliczeń są zawsze wykonywane na dokładność rejestru, dokładność wyników pośrednich jest zależna platformy (chociaż dokładności zawsze będzie co najmniej tak dokładny jak użytkownik określony dokładności).

Należy wziąć pod uwagę wyrażenia przypisania w poniższym kodzie. Wyrażenie po prawej stronie przypisania operatora "=" zostanie obliczona o dokładności rejestru i jawnie zaokrąglone do typu po lewej stronie przypisania.

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

Aby jawnie zaokrąglić wyniki pośrednie, należy wprowadzić typecast. Na przykład, jeśli poprzedni kod jest modyfikowany przez dodanie jawne rzutowanie typu, pośrednie wyrażenia (c * d) zostanie zaokrąglona do rodzaju typecast.

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

Jeden domniemanie tej metody zaokrąglania jest, że niektóre pozornie równoważne przekształcenia faktycznie nie mają identyczne semantyki. Na przykład następujące przekształcania dzieli wyrażenie jednej do dwóch wyrażeń przypisania.

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

Tych kodowaniach ma semantykę równoważne, ponieważ każdy drugi kodowania wprowadziły operatora przypisania dodatkowe, a więc dodatkowe zaokrąglania punktu.

Gdy funkcja zwraca wartość zmiennoprzecinkową, wartość zostanie zaokrąglona do typu funkcji. Gdy wartość zmiennoprzecinkowa jest przekazywany jako parametr do funkcji, wartość zostanie zaokrąglona do typu parametru. Na przykład:

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

### <a name="architecture-specific-rounding-under-fpprecise"></a>Zaokrąglanie architektury, w obszarze fp: precise

|Procesor|Zaokrąglanie dokładności dla wyrażeń pośrednich|
|-|-|
|x86|Wyrażeń pośrednich są obliczane na 53-bitową precyzję domyślne z zakresem rozszerzonej dostarczone przez wykładnik 16-bitowych. Gdy te wartości 53:16 są "rozlane" do pamięci (co może się zdarzyć podczas wywołania funkcji), rozszerzonych wykładnika zakres będzie zawężony do 11 bitów. Oznacza to rozlanej wartości są rzutowane do formatu standardowego podwójnej precyzji z wykładnik 11-bitowych.<br/>Użytkownik może przełączyć się do rozszerzonego precyzji 64-bitowych zaokrąglania pośredniego, zmieniając przy użyciu słowo sterujące zmiennoprzecinkowe `_controlfp` i włączając dostęp do środowiska FPU (zobacz [fenv_access pragma](#the-fenv-access-pragma)). Jednak gdy register wartości rozszerzone dokładności są rozrzucone pamięci, wyniki pośrednie zostanie nadal zaokrąglony podwójnej precyzji.<br/>Tej konkretnej semantycznego może ulec zmianie.|
|amd64|Semantyki FP na amd64 różnią się nieco na innych platformach. Ze względu na wydajność operacji pośrednie są obliczane najszerszego dokładność jeden z operandów, a nie na dokładność najszerszego dostępne.  Wymuszenie obliczenia, które ma zostać obliczony, za pomocą dokładności szerszy niż operandów, użytkownicy muszą wprowadzić operacji rzutowania na co najmniej jeden argument w wyrażeniu podrzędnych.<br/>Tej konkretnej semantycznego może ulec zmianie.|

### <a name="algebraic-transformations-under-fpprecise"></a>Przekształcenia algebraiczne w obszarze fp: precise

Podczas fp: precise tryb jest włączone, kompilator nigdy nie będzie wykonywać przekształcenia algebraiczne *chyba że ostateczny wynik jest identyczne zgodność*. Wiele dobrze znanych algebraicznych reguły arytmetyczne liczba rzeczywista nie zawsze mają dla arytmetyki zmiennoprzecinkowej. Na przykład, poniższe wyrażenia są równoważne Reals, ale niekoniecznie wartości zmiennoprzecinkowe.

|Formularz|Opis|
|-|-|
|`(a+b)+c = a+(b+c)`|Reguła asocjacyjnych do dodania|
|`(a*b)*c = a*(b*c)`|Reguła asocjacyjnych mnożenia|
|`a*(b+c) = a*b + b*c`|Rozkład mnożenia przez dodanie|
|`(a+b)(a-b) = a*a-b*b`|Wyprowadzenie algebraicznych|
|`a/b = a*(1/b)`|Dzielenie przez odwrotność multiplicative|
|`a*1.0 = a`|Tożsamość mnożenia|

Jak pokazano w przykładzie wprowadzenie za pomocą funkcji `KahanSum`, kompilator może mieć ochotę wykonać różne przekształcenia algebraiczne w celu wygenerowania programy znacznie szybsze. Mimo że zależy od takich przekształcenia algebraiczne optymalizacje prawie zawsze są niepoprawne, istnieją sytuacje, w których są całkowicie bezpieczne. Na przykład czasami jest pożądane, aby zastąpić dzielenie przez *stałej* mnożenia przez wartość mnożenia odwrotność stała wartość:

```cpp
const double four = 4.0;
double a, b;
...

a = b/four;
```

Może być przekształcone na

```cpp
const double four = 4.0;
const double tmp0 = 1/4.0;
double a, b;
...
a = b*tmp0;
```

Jest to bezpieczne transformacji, ponieważ Optymalizator można określić w czasie kompilacji x / 4.0 == x*(1/4.0) wszystkich zmiennoprzecinkowe wartości x, łącznie z nieskończoności i NaN. Zastępując operacji dzielenia mnożenia, kompilator może zapisać kilka cykli — zwłaszcza w przypadku FPUs, bezpośrednio nie implementują dzielenia, które wymagają kompilatora do generowania kombinacji zbliżenia odwracanie i mnożenie Dodawanie instrukcje. Kompilator może wykonywać takiej optymalizacji, w obszarze fp: precise tylko wtedy, gdy mnożenia zastąpienie tworzy dokładnie takie same powoduje, jako podziału. Kompilator może również wykonywać proste transformacje w ramach fp: precise, pod warunkiem że wyniki są identyczne. Należą do nich następujące elementy:

|Formularz|Opis
|-|-|
|`(a+b) == (b+a)`|Przemienne reguły do dodania|
|`(a*b) == (b*a)`|Przemienne reguły dla mnożenia|
|`1.0*x*y == x*1.0*y == x*y*1.0 == x*y`|Mnożenie przez 1.0|
|`x/1.0*y == x*y/1.0 == x*y`|Dzielenie przez 1.0|
|`2.0*x == x+x`|Mnożenie przez w wersji 2.0|

### <a name="contractions-under-fpprecise"></a>Skrótów w obszarze fp: precise

Kluczową cechą architektury wiele nowoczesnych jednostek zmiennoprzecinkowych jest możliwość wykonywania mnożenia, następuje dodatku jako pojedyncza operacja błędem nie pośredni zaokrąglania. Na przykład firmy Intel Itanium architektura zawiera instrukcje dotyczące łączenia każdego z tych operacji trójargumentowy (*b + c), (* b c) i (c-a * b), w pojedynczej instrukcji zmiennoprzecinkowych (fma, fms i fnma odpowiednio). Te instrukcje o pojedynczej są szybsze niż wykonywania oddzielnych Pomnóż i Dodaj instrukcje i są bardziej precyzyjne, ponieważ nie ma pośrednich zaokrąglenie nie produktu. Tego rodzaju optymalizacji, można znacznie przyspieszyć funkcje zawierające kilka z przeplotem wielokrotnie i dodać operacje. Na przykład należy wziąć pod uwagę następujące algorytmu, który oblicza skalarnego dwa wektory n wymiarowy.

```cpp
float dotProduct( float x[], float y[], int n )
{
   float p=0.0;
   for (int i=0; i<n; i++)
      p += x[i]*y[i];
   return p;
}
```

To obliczenie, które mogą być wykonywane szereg instrukcji formularza p mnożenie dodawanie = p + x [i] * y [i].

Optymalizacja zmniejszenia mogą być kontrolowane niezależnie przy użyciu `fp_contract` dyrektywy kompilatora. Domyślnie fp: precise modelu pozwala na skrótów, ponieważ zwiększają szybkość i dokładność. W obszarze fp: precise, kompilator nigdy nie skontaktuję się z zaokrąglaniem jawne wyrażenie.
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

### <a name="order-of-floating-point-expression-evaluation-under-fpprecise"></a>Kolejność obliczania wyrażenie typu zmiennoprzecinkowego, w obszarze fp: precise

Optymalizacje, które zachowują kolejność obliczania wyrażeń zmiennoprzecinkowe są zawsze bezpieczne i w związku z tym są dozwolone w ramach fp: precise trybu. Rozważ następującą funkcję, która oblicza iloczyn dwóch wektorów n wymiarowy w pojedynczej precyzji. Pierwszy blok kodu poniższym funkcja pierwotna jako mogą być kodowane przez programistę następuje taką samą funkcję po częściowej optymalizacji odwijania pętli.

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

Główną Korzyścią płynącą z tego rodzaju optymalizacji jest zmniejsza liczbę warunkowego rozgałęzianie pętli, o ile 75%. Ponadto, zwiększając liczbę operacji w treści pętli, kompilator może już więcej możliwości w celu dalszej optymalizacji. Na przykład niektóre FPUs może można wykonać mnożenie dodawanie w p += x [i] * y [i] podczas pobierania równocześnie wartości x [i + 1] i y [i + 1] do użycia w następnym kroku. Tego rodzaju optymalizacji jest idealnie bezpieczne dla obliczeń zmiennoprzecinkowych, ponieważ jego zachowuje kolejność operacji.

Często korzystne jest dla kompilatora zmienić kolejność całej operacji, aby można było utworzyć kod szybciej. Rozważmy poniższy kod:

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

Reguły semantyki C++ wskazują, że program powinno to dawać wyniki tak, jakby najpierw obliczane x, a następnie y i na końcu. Załóżmy, że kompilator zawiera tylko cztery dostępne rejestrów zmiennoprzecinkowych. Jeśli kompilator jest zmuszony do obliczenia x, y i z kolei, warto generowanie kodu za pomocą się następującą semantyką:

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

Istnieje kilka operacji nadmiarowych wyraźnie jest to kodowanie. Jeśli kompilator ściśle regułom C++ semantyczne, ta kolejność jest konieczne, ponieważ program mogą uzyskiwać dostęp do środowiska FPU wewnętrzne każdego przypisania. Jednak ustawienia domyślne dla fp: precise umożliwia kompilatorowi optymalizację tak, jakby program nie dostęp do środowiska, dzięki któremu kolejności tych wyrażeń. Następnie jest usunąć zwolnienia przez obliczenie wartości w odwrotnej kolejności, w następujący sposób:

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

To kodowanie jest wyraźnie przełożonego, posiadające zmniejszona liczbę instrukcji fp prawie 40%. Wyniki dla x, y i z są takie same, tak jak poprzednio, ale obliczone mniejsze obciążenie.

W obszarze fp: precise, kompilator może również *przeplotu* typowych wyrażeń podrzędnych w taki sposób, aby utworzyć kod szybciej. Na przykład kod, aby obliczyć pierwiastki w równaniu kwadratowym mogą być zapisane w następujący sposób:

```cpp
double a, b, c, root0, root1;
...
root0 = (-b + sqrt(b*b-4*a*c))/(2*a);
root1 = (-b - sqrt(b*b-4*a*c))/(2*a);
```

Mimo że te wyrażenia różnią się tylko jednej operacji, programistę może być napisane tak go ten sposób, aby zagwarantować, że każda wartość głównego zostanie obliczona w najwyższym dokładności praktyczne. W obszarze fp: precise, kompilator jest bezpłatna dla przeplotu obliczania root0 i root1, aby usunąć wspólnych podrzędną wyrażeniach bez utraty dokładności. Na przykład następujące usunięto kilka kroków nadmiarowe przy jednoczesnym dokładnie tej samej odpowiedzi.

```cpp
double a, b, c, root0, root1;
...
register tmp0 = -b;
register tmp1 = sqrt(b*b-4*a*c);
register tmp2 = 2*a;
root0 = (tmp0+tmp1)/tmp2;
root1 = (tmp0-tmp1)/tmp2;
```

Inne optymalizacje mogą próbować przenieść obliczanie niektórych niezależnych wyrażeń. Należy wziąć pod uwagę następującego algorytmu, który zawiera gałąź warunkowa w ciele pętli.

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

Kompilator może wykryć, że wartość wyrażenia (abs(d) > 1) jest niezmienny w treści pętli. Dzięki temu kompilator "przenieść" if instrukcji poza ciałem pętli, przekształcania powyższy kod w następujących czynności:

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

Po przekształceniu nie ma już gałąź warunkowa w jednym z treści pętli, co znacznie poprawia ogólną wydajność pętli. Ten rodzaj optymalizacji jest idealnie bezpieczne ponieważ obliczania wyrażenia (abs(d) > 1.0) jest niezależna od innych wyrażeń.

Obecności dostęp do środowiska FPU lub wyjątki zmiennoprzecinkowe są contraindicated tego rodzaju optymalizacji, ponieważ umożliwiają one zmianę semantycznego przepływu. Optymalizacje takie są dostępne tylko w obszarze fp: precise tryb ponieważ dostęp do środowiska FPU i semantyka wyjątków zmiennopozycyjnych są domyślnie wyłączone. Funkcje, które dostęp do środowiska FPU jawnie wyłączyć za pomocą takich optymalizacje `fenv_access` dyrektywy kompilatora. Podobnie, należy użyć funkcji przy użyciu wyjątki zmiennoprzecinkowe `float_control(except ... )` dyrektywy kompilatora (lub użyj **/FP: except** przełącznik wiersza polecenia).

Podsumowując, fp: precise tryb umożliwia kompilator, aby zmienić kolejność obliczania wyrażeń liczb zmiennopozycyjnych, pod warunkiem, że wyniki końcowe nie zostały zmienione i czy wyniki nie są zależne od środowiska FPU lub na wyjątki zmiennoprzecinkowe.

### <a name="fpu-environment-access-under-fpprecise"></a>Dostęp do środowiska FPU w obszarze fp: precise

Gdy fp: precise tryb jest włączone, kompilator zakłada, program nie dostępu lub zmiany środowiska FPU. Jak wspomniano wcześniej, to założenie umożliwia kompilatorowi zmiana kolejności lub Przenieś operacji zmiennoprzecinkowych w celu poprawy wydajności w ramach fp: precise.

Niektóre programy mogą zmienić zmiennoprzecinkowych zaokrąglaniem kierunku rozmieszczania zawartości śródwierszowej przy użyciu `_controlfp` funkcji. Na przykład niektóre programy obliczeń w prawym górnym i dolnym błąd górnych granic operacje arytmetyczne, wykonując ten sam obliczeń dwa razy, najpierw podczas zaokrąglaniem kierunku minus nieskończoność, następnie podczas zaokrąglania do nieskończoności dodatniej. Ponieważ FPU zapewnia wygodny sposób kontrolowania zaokrąglania, programista może zdecydować się na zmianę trybu zaokrąglania przez zmianę środowiska FPU. Poniższy kod oblicza dokładny błąd powiązany zmiennoprzecinkowych mnożenia przez zmianę środowiska FPU.

```cpp
double a, b, cLower, cUpper;
// . . .
_controlfp( _RC_DOWN, _MCW_RC );    // round to -&infin;
cLower = a*b;
_controlfp( _RC_UP, _MCW_RC );    // round to +&infin;
cUpper = a*b;
_controlfp( _RC_NEAR, _MCW_RC );    // restore rounding mode
```

W obszarze fp: precise, kompilator zawsze zakłada środowiska FPU domyślnego, więc Optymalizator jest bezpłatna dla ignorować wywołania do `_controlfp` i zmniejszyć powyżej przypisania do cUpper = cLower = * b; wyraźnie mogłoby to spowodować zwrócenie niepoprawnych wyników. Aby uniknąć takich optymalizacje, należy włączyć dostęp do środowiska FPU za pomocą `fenv_access` dyrektywy kompilatora.

Inne programy mogą próbować wykrywania niektórych błędów zmiennoprzecinkowych, sprawdzając FPU wyrazy stanu. Na przykład poniższy kod sprawdza, czy warunki dzielenie przez zero i niedokładny

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

W obszarze fp: precise, optymalizacje, zmienić kolejność oceny wyrażenia, które mogą ulec zmianie punkty, w których występują pewne błędy. Uzyskiwanie dostępu do słowa stanu programów, należy włączyć dostęp do środowiska FPU przy użyciu `fenv_access` dyrektywy kompilatora.

Aby uzyskać więcej informacji, zobacz sekcję [fenv_access pragma](#the-fenv-access-pragma).

### <a name="floating-point-exception-semantics-under-fpprecise"></a>Semantyka wyjątków dotyczących liczb zmiennoprzecinkowych pod fp: precise

Domyślnie semantykę wyjątku zmiennoprzecinkowego są wyłączone w obszarze fp: precise. Większość programistów C++ łatwiej obsługiwać wyjątkowych warunkach zmiennoprzecinkowych bez korzystania z systemu i wyjątki języka C++. Ponadto jak wspomniano wcześniej, wyłączenie semantykę wyjątku zmiennoprzecinkowego umożliwia kompilatora większą elastyczność podczas optymalizacji operacji zmiennopozycyjnych. Użyj jednej **/FP: z wyjątkiem** przełącznika lub `float_control` pragma umożliwienia semantyki wyjątków zmiennoprzecinkowych, korzystając z fp: precise modelu.

Aby uzyskać więcej informacji, zobacz sekcję [Włączanie semantykę wyjątku zmiennoprzecinkowego](#enabling-floating-point-exception-semantics).

## <a name="the-fpfast-mode-for-floating-point-semantics"></a>Tryb FP: Fast semantykę zmiennoprzecinkową

Po włączeniu trybu FP: Fast, kompilator zwalnia reguły tego fp: precise używa podczas optymalizacji operacji zmiennopozycyjnych. Ten tryb jest umożliwia kompilatorowi do dalszej optymalizacji kodu zmiennoprzecinkowego dla danej szybkości, kosztem dokładności zmiennoprzecinkowe i poprawności. Programy, które nie zależą od bardzo dokładnych obliczeń zmiennoprzecinkowych może wystąpić do poprawy szybkości znaczące przez włączenie trybu FP: Fast.

Tryb zmiennoprzecinkowych FP: Fast jest włączane przy użyciu [Fast](fp-specify-floating-point-behavior.md) przełącznika kompilatora wiersza polecenia w następujący sposób:

> source.cpp Fast cl

W tym przykładzie nakazuje kompilatorowi korzystają bezpośrednio z semantyki FP: Fast podczas generowania kodu dla pliku source.cpp. Można również wywołać model FP: Fast na temat korzystania z poszczególnych funkcji przez funkcję `float_control` dyrektywy kompilatora.

Aby uzyskać więcej informacji, zobacz sekcję [float_control pragma](#the-float-control-pragma).

W trybie FP: Fast kompilator może dokonać optymalizacji, zmienić dokładność obliczeń zmiennoprzecinkowych. Kompilator może niepoprawnie zaokrąglać w przypisania, rzutowaniach typu lub wywołaniach funkcji i pośredniego zaokrąglania nie zawsze odbędzie się. Określone optymalizacji zmiennopozycyjnych, takich jak skrótów, są zawsze włączone. Semantyka wyjątków dotyczących liczb zmiennoprzecinkowych i ważność środowiska FPU są wyłączone i jest niedostępne.

|Semantyka FP: Fast|Wyjaśnienie
|-|-|
|Zaokrąglanie semantyki|Jawne Zaokrąglenie w przypisania, rzutowaniach typu i wywołania funkcji można zignorować.<br/>Wyrażeń pośrednich mogą być zaokrąglane w ciągu mniej niż zarejestrować dokładności zgodnie z wymaganiami dotyczącymi wydajności.|
|Przekształcenia algebraiczne|Kompilator może przekształcić wyrażeń, zgodnie z liczbą rzeczywistą algebry asocjacyjnych, podziału; te przekształcenia nie musi być niedokładne lub prawidłowe.|
|Skrótów|Zawsze włączone; Nie można wyłączyć przez dyrektywy pragma `fp_contract`|
|Kolejność obliczania zmiennoprzecinkowych|Kompilator może zmienić kolejność obliczania wyrażeń liczb zmiennopozycyjnych, nawet wtedy, gdy takie zmiany mogą zmienić wyników końcowych.|
|Dostęp do środowiska FPU|Wyłączone. Niedostępne|
|Semantyka wyjątków dotyczących liczb zmiennoprzecinkowych|Wyłączone. Niedostępne|

### <a name="rounding-semantics-for-floating-point-expressions-under-fpfast"></a>Zaokrąglanie semantykę zmiennoprzecinkową wyrażeń w obszarze FP: Fast

W odróżnieniu od fp: precyzyjnego modelu, model FP: Fast wykonuje obliczeń pośrednich najbardziej wygodne dokładności. Zaokrąglenie w przypisania, rzutowaniach typu i wywołania funkcji nie może być zawsze wykonywane. Na przykład pierwsza funkcja poniżej wprowadza trzy zmienne pojedynczej precyzji (`C`, `Y` i `T`). Kompilator może wybrać przebiegała tych zmiennych, obowiązuje podwyższania poziomu typu `C`, `Y` i `T` do podwójnej precyzji.

Funkcja pierwotna:

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

Zmienne przechowywane w rejestrze procesora:

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

W tym przykładzie FP: Fast ma subverted celem funkcja pierwotna. Ostatni wynik przechowywany w zmiennej zoptymalizowane pod kątem `sum`, może być dość perturbed z odpowiedni wynik.

W obszarze FP: Fast kompilator zazwyczaj będzie podejmować próby obsługi co najmniej dokładność określona na podstawie kodu źródłowego. Jednak w niektórych przypadkach kompilator może wybrać do wykonania wyrażeń pośrednich w *zmniejszyć dokładność* niż określona w kodzie źródłowym. Na przykład pierwszy blok kodu poniższym wywołuje funkcję pierwiastek kwadratowy w wersji podwójnej precyzji. W obszarze FP: Fast w pewnych okolicznościach, np. Jeśli wynik i argumenty funkcji są jawnie zrzutować pojedynczej precyzji kompilator może wybrać Zastąp wywołanie podwójnej precyzji `sqrt` przy użyciu wywołania do pojedynczej precyzji `sqrtf`funkcji. Ponieważ rzutowania upewnij się, że wartość, przechodząc do `sqrt` i wartość wyjście są zaokrąglane do pojedynczej precyzji, spowoduje to zmianę tylko miejsca zaokrąglania. Jeśli wartość do sqrt była wartość podwójnej precyzji i kompilator wykonać takie przekształcenie dowolną liczbę połowę bitów precyzji może być nieprawidłowa.

Funkcja pierwotna

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

Mimo że mniej dokładne, tego rodzaju optymalizacji mogą być szczególnie korzystne w przypadku przeznaczone dla procesorów, które zapewniają pojedynczej precyzji na wewnętrzne wersje funkcji, takich jak `sqrt`. Po prostu dokładnie Kiedy kompilator będzie używał takich optymalizacje jest uzależniona platformy i kontekstu.

Ponadto nie ma żadnych gwarancji spójności dokładność obliczeń pośrednich, które można wykonać na dowolnym poziomie dokładności, dostępne dla kompilatora. Mimo że kompilator będzie próbował zachować co najmniej poziom dokładności określony przez kod, FP: Fast umożliwia Optymalizator downcast pośrednich obliczeń w celu wygenerowania kodu maszynowego szybszy lub mniejsze. Na przykład kompilator może jeszcze bardziej zoptymalizować kodu z powyższych zaokrąglić część pośredniego mnożenia do pojedynczej precyzji.

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

Tego rodzaju zaokrąglenie dodatkowe mogą wynikać z przy użyciu niższe dokładności jednostki zmiennoprzecinkowej, takich jak SSE2, do wykonywania niektórych obliczeń pośrednich. Dokładność zaokrąglania FP: Fast jest zatem platformy zależnych; Kod, który kompiluje dobrze sprawdza się w jednym procesorze mogą działać dobrze w przypadku innego procesora. Pozostawia się użytkownika w celu ustalenia, jeśli korzyści szybkość przewyższają wszelkie problemy dokładności.

Jeśli optymalizacji FP: Fast jest szczególnie problematyczny dla określonych funkcji, tryb zmiennoprzecinkowych może być lokalnie ich fp: precise przy użyciu `float_control` dyrektywy kompilatora.

### <a name="algebraic-transformations-under-fpfast"></a>Przekształcenia algebraiczne w obszarze FP: Fast

Tryb FP: Fast umożliwia kompilatorowi wykonanie pewnych, niebezpieczne przekształcenia algebraiczne do zmiennoprzecinkowych punktu wyrażeń. Na przykład można zastosować następujące optymalizacje niebezpiecznych w obszarze FP: Fast.

||||
|-|-|-|
|Oryginalny kod|Krok #1|Krok #2
|`double a, b, c;`<br/>`double x, y, z;`<br/><br/>`y = (a + b);`<br/>`z = y – a – b;`<br/><br/>`c = x – z;`<br/><br/>`c = x * z;`<br/><br/>`c = x - z;`<br/><br/>`c = x + z;`<br/><br/>`c = z-x;`|`double a, b, c;`<br/>`double x, y, z;`<br/><br/>`y = (a + b);`<br/>`z = 0;`<br/><br/>`c = x – 0;`<br/><br/>`c = x * 0;`<br/><br/>`c = x - 0;`<br/><br/>`c = x + 0;`<br/><br/>`c = 0 - x;`|`double a, b, c;`<br/>`double x, y, z;`<br/><br/>`y = (a + b);`<br/>`z = 0;`<br/><br/>`c = x;`<br/><br/>`c = 0;`<br/><br/>`c = x;`<br/><br/>`c = x;`<br/><br/>`c = -x;`|

W kroku 1, kompilator obserwuje, że `z = y – a – b` jest zawsze równa zero. Chociaż jest technicznie nieprawidłowy obserwacji, jest dozwolone na mocy FP: Fast. Kompilator następnie propaguje stałej wartości zero do każdego późniejsze użycie zmiennej z. W kroku 2, kompilator dodatkowo optymalizuje przez obserwację, `x - 0 == x`, `x * 0 == 0`itp. Ponownie nawet jeśli te uwagi nie jest prawidłowym ściśle, zezwala na FP: Fast. Zoptymalizowany kod jest teraz znacznie szybciej, ale może również znacznie mniej dokładne lub nawet niepoprawne.

Dowolne z następujących reguł algebraicznych (niebezpieczne) mogą zostać wykorzystane przez optymalizator, po włączeniu trybu FP: Fast:

|||
|-|-|
|Formularz|Opis|
|`(a + b) + c = a + (b + c)`|Reguła asocjacyjnych do dodania|
|`(a * b) * c = a * (b * c)`|Reguła asocjacyjnych mnożenia|
|`a * (b + c) = a * b + b * c`|Rozkład mnożenia przez dodanie|
|`(a + b)(a - b) = a * a - b * b`|Wyprowadzenie algebraicznych|
|`a / b = a * (1 / b)`|Dzielenie przez odwrotność multiplicative|
|`a * 1.0 = a, a / 1.0 = a`|Tożsamość mnożenia|
|`a ± 0.0 = a, 0.0 - a = -a`|Tożsamość dodatku|
|`a / a = 1.0, a - a = 0.0`|Anulowanie|

Jeśli optymalizacji FP: Fast jest szczególnie problematyczny dla określonej funkcji, tryb zmiennoprzecinkowych może być lokalnie ich fp: precise przy użyciu `float_control` dyrektywy kompilatora.

### <a name="order-of-floating-point-expression-evaluation-under-fpfast"></a>Kolejność obliczania wyrażenie typu zmiennoprzecinkowego, w obszarze FP: Fast

W odróżnieniu od fp: precise, FP: Fast umożliwia kompilatorowi zmieniać kolejność operacji zmiennoprzecinkowych tak, aby utworzyć kod szybciej. W związku z tym niektóre optymalizacje w obszarze FP: Fast nie może zachować zalecanej kolejności wyrażeń. Na przykład rozważmy następującą funkcję, która oblicza iloczyn dwóch wektorów n wymiarowy.

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

W obszarze FP: Fast, optymalizator może wykonywać redukcja skalaru z `dotProduct` działać skutecznie Przekształcanie funkcji w następujący sposób:

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

Cztery oddzielne dostępnych produktów zoptymalizowane wersję funkcji są wykonywane równocześnie i następnie dodane do siebie. Tego rodzaju optymalizacji można przyspieszyć obliczania `dotProduct` przez tyle, ile współczynnik czterech zależności od tego, czy procesor docelowy, ale wynik końcowy może być tak niedokładne utrudniający bezużyteczny. Jeśli takie optymalizacje są szczególnie problematyczny dla jednej funkcji lub jednostce translacji, tryb zmiennoprzecinkowych może być lokalnie ich fp: precise przy użyciu `float_control` dyrektywy kompilatora.

## <a name="the-fpstrict-mode-for-floating-point-semantics"></a>Fp: strict tryb semantykę zmiennoprzecinkową

Podczas fp: tryb z ograniczeniami jest włączone, kompilator działa zgodnie z tych samych reguł tego fp: precise używa podczas optymalizacji operacji zmiennopozycyjnych. W tym trybie również włącza semantykę wyjątku zmiennoprzecinkowego i czułości do środowiska FPU i wyłącza niektóre optymalizacje, takie jak skrótów. Jest to najbardziej rygorystyczne tryb działania.

Fp: tryb z ograniczeniami zmiennoprzecinkowej jest włączane przy użyciu [/FP: strict](fp-specify-floating-point-behavior.md) przełącznika kompilatora wiersza polecenia w następujący sposób:

> Cl/FP: strict source.cpp

W tym przykładzie nakazuje kompilatorowi używanie fp: ścisłą semantykę podczas generowania kodu dla pliku source.cpp. Fp: strict modelu można również wywołać w poszczególnych funkcji przez funkcję przy użyciu `float_control` dyrektywy kompilatora.

Aby uzyskać więcej informacji, zobacz sekcję [float_control pragma](#the-float-control-pragma).

W obszarze fp: tryb z ograniczeniami, kompilator nigdy nie wykonuje żadnych optymalizacje, które perturb dokładność obliczeń zmiennoprzecinkowych. Kompilator zawsze zostanie niepoprawnie zaokrąglać w przypisania, rzutowaniach typu i wywołaniach funkcji i pośredniego zaokrąglania spójnie odbędzie się w tej samej precyzji jak rejestruje FPU. Semantyka wyjątków dotyczących liczb zmiennoprzecinkowych i ważność środowiska FPU są domyślnie włączone. Niektóre optymalizacje, takie jak skrótów, są wyłączone, ponieważ kompilator nie może zagwarantować poprawność w każdym przypadku.

|FP: strict semantyki|Wyjaśnienie|
|-|-|
|Zaokrąglanie semantyki|Jawne Zaokrąglenie w przypisania, rzutowaniach typu, a następnie wywołuje funkcję<br/>Wyrażeń pośrednich zostanie oceniona dokładności rejestru.<br/>Taki sam jak fp: precise|
|Przekształcenia algebraiczne|Ścisłego przestrzegania-asocjacyjnych, bez podziału algebry zmiennoprzecinkowych, chyba że przekształcenie gwarantuje zawsze działają tak samo.<br/>Taki sam jak fp: precise|
|Skrótów|Zawsze wyłączone|
|Kolejność obliczania zmiennoprzecinkowych|Kompilator nie będą mogli zmienić kolejności obliczania wyrażeń liczb zmiennopozycyjnych|
|Dostęp do środowiska FPU|Zawsze włączone.|
|Semantyka wyjątków dotyczących liczb zmiennoprzecinkowych|Domyślnie włączony.|

### <a name="floating-point-exception-semantics-under-fpstrict"></a>Semantyka wyjątków dotyczących liczb zmiennoprzecinkowych pod fp: strict

Domyślnie semantykę wyjątku zmiennoprzecinkowego są włączone w obszarze fp: strict modelu. Aby wyłączyć te semantykę, należy użyć **/FP: except —** przełącznika lub wprowadzenia `float_control(except, off)` pragma.

Aby uzyskać więcej informacji, zobacz sekcje [Włączanie semantykę wyjątku zmiennopozycyjnego](#enabling-floating-point-exception-semantics) i [float_control Pragma](#the-float-control-pragma).

## <a name="the-fenvaccess-pragma"></a>Fenv_access pragma

Sposób użycia:

```cpp
#pragma fenv_access( [ on  | off ] )
```

[Fenv_access](../../preprocessor/fenv-access.md) pragma umożliwia kompilatorowi wprowadzić pewne optymalizacje, które może być złamać FPU flagi testy i FPU zmiany trybu. Gdy stan `fenv_access` jest wyłączona, kompilator może przyjąć tryby FPU domyślne są stosowane, a flagi FPU, nie są sprawdzane. Domyślnie dostęp do środowiska jest wyłączone dla fp: precise tryb chociaż może być jawnie włączone, za pomocą tej pragmie. W obszarze fp: strict, `fenv_access` jest zawsze włączona i nie można wyłączyć. W obszarze FP: Fast `fenv_access` jest zawsze wyłączona i nie można włączyć.

Zgodnie z opisem w fp: precise sekcji niektórych programistów mogą zmienić zmiennoprzecinkowych za pomocą zaokrąglaniem kierunku rozmieszczania zawartości śródwierszowej `_controlfp` funkcji. Na przykład do obliczenia granice obliczania górnego i dolnego błędu na operacje arytmetyczne, niektóre programy wykonać dwa razy, tych samych obliczeń najpierw podczas zaokrąglaniem kierunku minus nieskończoność, a następnie podczas zaokrąglania do nieskończoności dodatniej. Ponieważ FPU zapewnia wygodny sposób kontrolowania zaokrąglania, programista może zdecydować się na zmianę trybu zaokrąglania przez zmianę środowiska FPU. Poniższy kod oblicza dokładny błąd powiązany zmiennoprzecinkowych mnożenia przez zmianę środowiska FPU.

```cpp
double a, b, cLower, cUpper;
// . . .
_controlfp( _RC_DOWN, _MCW_RC );    // round to -infinity
cLower = a*b;
_controlfp( _RC_UP, _MCW_RC );       // round to +infinity
cUpper = a*b;
_controlfp( _RC_NEAR, _MCW_RC );    // restore rounding mode
```

Po wyłączeniu `fenv_access` pragma umożliwia kompilator, aby założył środowiska FPU domyślnego; w związku z tym Optymalizator jest bezpłatna dla ignorować wywołania do `_controlfp` i zmniejszyć powyżej przypisania do `cUpper = cLower = a*b`. Po włączeniu jednak `fenv_access` zapobiega takich optymalizacji.

Programy mogą również sprawdzić wyrazy stanu FPU do wykrywania niektórych błędów zmiennoprzecinkowych. Na przykład poniższy kod sprawdza, czy warunki dzielenie przez zero i niedokładny

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

Gdy `fenv_access` jest wyłączona, kompilator może zmienić kolejność wykonywania wyrażeń liczb zmiennopozycyjnych, więc prawdopodobnie subverting FPU sprawdzania stanu. Włączanie `fenv_access` zapobiega takich optymalizacji.

## <a name="the-fpcontract-pragma"></a>Fp_contract pragma

Sposób użycia:

```cpp
#pragma fp_contract( [ on | off ] )
```

Zgodnie z opisem w fp: sekcja dokładne, zmniejszenia jest podstawową cechą architektury dla wielu nowoczesnych jednostkom zmiennoprzecinkowym. Skrótów zapewniają możliwość wykonywania mnożenia, następuje dodatku jako pojedyncza operacja błędem nie pośredni zaokrąglania. Te instrukcje o pojedynczej są szybsze niż wykonywania oddzielnych Pomnóż i Dodaj instrukcje i są bardziej precyzyjne, ponieważ nie ma pośrednich zaokrąglenie nie produktu. Operacja umowie można oblicza wartość `(a*b+c)` tak, jakby były obliczane z dokładnością do nieskończoności zarówno operacji, a następnie jest zaokrąglana do najbliższej liczba zmiennoprzecinkowa. Tego rodzaju optymalizacji, można znacznie przyspieszyć funkcje zawierające kilka z przeplotem wielokrotnie i dodać operacje. Na przykład należy wziąć pod uwagę następujące algorytmu, który oblicza skalarnego dwa wektory n wymiarowy.

```cpp
float dotProduct( float x[], float y[], int n )
{
   float p=0.0;
   for (int i=0; i<n; i++)
      p += x[i]*y[i];
   return p;
}
```

To obliczenie, które mogą być wykonywane szereg instrukcji formularza mnożenie Dodawanie `p = p + x[i]*y[i]`.

[Fp_contract](../../preprocessor/fp-contract.md) pragmę, czy są zawarte zmiennoprzecinkowych wyrażeń. Domyślnie fp: pozwala na skrótów w trybie ścisłym, ponieważ zwiększają szybkość i dokładność. Skrótów są zawsze włączone dla trybu FP: Fast. Jednakże, ponieważ skrótów można złamać jawne wykrywania warunków błędów `fp_contract` pragma jest zawsze wyłączona w ramach fp: tryb z ograniczeniami. Przykłady wyrażeń, które mogą być nabytej kiedy `fp_contract` pragmy jest włączona:

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

**/FP: precise**, **Fast**, **/FP: strict** i **/FP: z wyjątkiem** przełączniki kontrolowania semantykę liczb zmiennopozycyjnych w pliku przez pliku Podstawa. [Float_control](../../preprocessor/float-control.md) pragma zapewnia takie kontrolę na podstawie funkcji przez funkcję.

Sposób użycia:

```cpp
#pragma float_control(push)
#pragma float_control(pop)
#pragma float_control( precise, on | off [, push] )
#pragma float_control( except, on | off [, push] )
```

Dyrektywy pragma `float_control(push)` i `float_control(pop)` odpowiednio wypychania i pop bieżącego stanu zmiennoprzecinkowego tryb i opcji wyjątku na stosie. Należy pamiętać, że stan `fenv_access` i `fp_contract` nie dotyczy pragma `pragma float_control(push/pop)`.

Wywoływanie pragmy `float_control(precise, on)` spowoduje włączenie i `float_control(precise, off)` spowoduje wyłączenie semantyki w trybie ścisłym. Podobnie, pragma `float_control(except, on)` spowoduje włączenie i `float_control(except, off)` spowoduje wyłączenie semantykę wyjątku. Semantykę wyjątku można włączyć tylko w przypadku, gdy dokładne semantyki również są włączone. Gdy opcjonalnego `push` argument jest obecny, Stany `float_control` opcje są wypychane poprzedzający zmianę semantyki.

### <a name="setting-the-floating-point-semantic-mode-on-a-function-by-function-basis"></a>Ustawianie zmiennoprzecinkowych trybu semantycznych na podstawie funkcji, funkcja

Przełączniki wiersza polecenia są w rzeczywistości skrót do ustawiania czterech różnych zmiennoprzecinkowych pragm. Aby wybrać jawnie określonym trybie zmiennoprzecinkowych semantycznych na podstawie funkcji przez funkcję, wybierz każdego z czterech opcji zmiennoprzecinkowych pragm zgodnie z opisem w poniższej tabeli:

||||||
|-|-|-|-|-|
||float_control(Precise)|float_control(EXCEPT)|fp_contract|fenv_access|
|/ FP: strict|on|on|Wyłączone|on|
|/ FP: strict/FP: except-|on|Wyłączone|Wyłączone|on|
|/ FP: precise|on|Wyłączone|on|Wyłączone|
|/ FP: precise/FP: except|on|on|on|Wyłączone|
|Fast|Wyłączone|Wyłączone|on|Wyłączone|

Na przykład następujące jawnie włącza semantykę FP: Fast.

```cpp
#pragma float_control( except, off )   // disable exception semantics
#pragma float_control( precise, off )  // disable precise semantics
#pragma fp_contract(on)                // enable contractions
#pragma fenv_access(off)               // disable fpu environment sensitivity
```

> [!Note]
> Semantykę wyjątku muszą zostać wyłączone przed wyłączeniem semantykę "precise".

## <a name="enabling-floating-point-exception-semantics"></a>Włączanie semantyki wyjątków dotyczących liczb zmiennoprzecinkowych

Niektóre wyjątkowych warunków zmiennoprzecinkowych, takich jak dzielenie przez zero, może spowodować FPU w celu sygnalizowania, że wyjątek sprzętowy. Wyjątki zmiennoprzecinkowe są domyślnie wyłączone. Wyjątki zmiennoprzecinkowe są włączone, modyfikując słowa sterującego FPU z `_controlfp` funkcji. Na przykład poniższy kod umożliwia dzielenie przez zero zmiennoprzecinkowych wyjątków:

```cpp
_clearfp(); // always call _clearfp before
            // enabling/unmasking a FPU exception
_controlfp( _EM_ZERODIVIDE, _MCW_EM );
```

Po włączeniu wyjątek dzielenie przez zero żadnych operacji dzielenia, za pomocą mianownik równej zero spowoduje, że wyjątek FPU ma być zasygnalizowany.

Aby przywrócić domyślny tryb słowa sterującego FPU, należy wywołać `_controlfp(_CW_DEFAULT, ~0)`.

Włączanie semantyki wyjątków dotyczących liczb zmiennoprzecinkowych za pomocą **/FP: except** flaga nie jest taka sama jak włączenie wyjątki zmiennoprzecinkowe. Po włączeniu semantykę wyjątku zmiennoprzecinkowego, kompilator muszą uwzględniać możliwość, że wszelkie operacji zmiennoprzecinkowej może zgłosić wyjątek. Ponieważ FPU jest jednostką oddzielne procesora, instrukcje wykonywania w FPU mogą być wykonywane równocześnie z instrukcjami w innych jednostkach.

Po włączeniu wyjątku zmiennopozycyjnego FPU zatrzymuje wykonywanie problematycznych instrukcji, a następnie sygnał wyjątkowy warunek, ustawiając FPU wyrazy stanu. Gdy procesor CPU osiągnie następnej instrukcji zmiennoprzecinkowej, najpierw sprawdza wszystkie oczekujące wyjątki FPU. W przypadku wyjątku oczekujące procesor pułapki, wywołując program obsługi wyjątku dostarczone przez System operacyjny. Oznacza to, że podczas operacji zmiennoprzecinkowej napotka wyjątkowy warunek, odpowiedni wyjątek nie zostanie wykryty do momentu następnej operacji zmiennoprzecinkowych jest wykonywane. Na przykład poniższy kod pułapek wyjątków dzielenie przez zero:

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

Występuje, jeśli warunek dzielenie przez zero w wyrażeniu = b/c FPU nie pułapki/Zgłoś wyjątek, aż do następnej operacji zmiennoprzecinkowych w wyrażeniu 2.0 * b. To powoduje zwrócenie następujących danych wyjściowych:

```Output
This line shouldn't be reached when c==0.0
SEH Exception Detected
```

Printf — odpowiadający pierwszy wiersz danych wyjściowych powinna nie zostanie osiągnięty; został osiągnięty, ponieważ zmiennoprzecinkowych wyjątków spowodowanych wyrażenie b/c nie został zgłoszony, aż do osiągnięcia 2.0 wykonywania * b. Aby zgłosić wyjątek zaraz po wykonaniu b i c., kompilator należy wprowadzić instrukcji "wait":

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

Ta instrukcja "Czekaj" wymusza procesora synchronizować ze stanem FPU i obsługiwać wszystkie wyjątki oczekujące. Kompilator wygeneruje tylko te "Czekaj" instrukcje po włączeniu semantykę liczb zmiennopozycyjnych. Gdy te semantyki są wyłączone, są domyślnie programy mogą wystąpić błędy synchronicity, podobny do powyższego, korzystając z wyjątków zmiennoprzecinkowych.

Po włączeniu semantykę liczb zmiennopozycyjnych, kompilator nie wprowadza tylko instrukcje "oczekiwanie", jego będzie również uniemożliwić kompilatorowi nielegalny optymalizacji kodu zmiennoprzecinkowego obecności możliwych wyjątków. Dotyczy to również wszelkich przekształceń, które zmienia punkty, w których są zgłaszane wyjątki. Ze względu na te czynniki Włączanie semantykę liczb zmiennopozycyjnych może znacznie zmniejszyć wydajność wygenerowanego kodu maszyny, w związku z tym zmniejszenie wydajności aplikacji.

Semantykę wyjątku zmiennoprzecinkowego są włączone domyślnie w ramach fp: tryb z ograniczeniami. Umożliwienia te semantyki w fp: trybie ścisłym, Dodaj **/FP: except** przejdź do wiersza polecenia kompilatora. Można również semantykę wyjątku zmiennoprzecinkowego włączone i wyłączone podstawę funkcji przez funkcję przy użyciu `float_control` pragmy.

### <a name="floating-point-exceptions-as-c-exceptions"></a>Wyjątki zmiennoprzecinkowe jako wyjątki języka C++

Za pomocą wszystkich wyjątków sprzętowych wyjątki zmiennoprzecinkowe wewnętrznie nie powodują wyjątków C++, ale zamiast tego wyzwalacza wyjątków strukturalnych. Aby mapować zmiennoprzecinkowych wyjątki strukturalne wyjątki C++, użytkownicy wprowadzić niestandardowe translatora złożonego wyjątku SEH. Po pierwsze wprowadzenie wyjątków C++, odpowiadający każdej zmiennoprzecinkowych wyjątków:

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

Następnie wprowadzono funkcję tłumaczenia, która wykryje zmiennoprzecinkowych wyjątków SEH i odpowiedni wyjątek języka C++. Aby użyć tej funkcji, Ustaw bieżący wątek procesu przy użyciu w usłudze translator obsługi wyjątków strukturalnych [_set_se_translator](../../c-runtime-library/reference/set-se-translator.md) funkcji z biblioteki środowiska uruchomieniowego.

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

Po zainicjowaniu to mapowanie wyjątki zmiennoprzecinkowe będą zachowywać się tak, jakby są wyjątki C++. Na przykład:

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

[Co każdy analityk komputera wiedzieć o arytmetyki zmiennoprzecinkowej](http://pages.cs.wisc.edu/~david/courses/cs552/S12/handouts/goldberg-floating-point.pdf) przez David Kowalski.

## <a name="see-also"></a>Zobacz także

[Optymalizacja kodu](optimizing-your-code.md)<br/>
