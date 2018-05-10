---
title: '&lt;losowe&gt; | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 08/24/2017
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- <random>
dev_langs:
- C++
helpviewer_keywords:
- random header
ms.assetid: 60afc25c-b162-4811-97c1-1b65398d4c57
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bdfae58c03d18638ad44f844909d585b41d710cd
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
---
# <a name="ltrandomgt"></a>&lt;Losowe&gt;

Definiuje urządzeń Generowanie liczby losowej umożliwia utworzenie jednolicie rozproszonej liczb losowych.

## <a name="syntax"></a>Składnia

```cpp
#include <random>
```

## <a name="summary"></a>Podsumowanie

A *generatora liczb losowych* jest obiekt, który tworzy sekwencję pseudolosowego wartości. Generator kodu, który tworzy wartości, które mogą być równomiernie rozłożone w określonym zakresie jest *Uniform generatora liczb losowych* (URNG). Klasy szablonów przeznaczony do działania jako URNG jest określany jako *aparat* tej klasy, czy niektóre typowe cechy, które zostały omówione w dalszej części tego artykułu. Może być URNG — i zwykle jest — połączeniu z *dystrybucji* przez przekazanie URNG jako argument do dystrybucji `operator()` do tworzenia wartości, które są dystrybuowane w taki sposób, który jest definiowana za pomocą dystrybucji.

Te linki przeskoczyć do głównych sekcji tego artykułu:

- [Przykłady](#code)

- [Lista kategorii](#listing)

- [Aparaty i dystrybucji](#engdist)

- [Uwagi](#comments)

### <a name="quick-tips"></a>Szybkie porady

Poniżej przedstawiono kilka wskazówek, które należy wziąć pod uwagę w przypadku korzystania z \<losowe >:

- W większości przypadków URNGs utworzyć raw bitów, które muszą być w kształcie przy dystrybucji. (Wyjątkiem ważne jest [std::shuffle()](../standard-library/algorithm-functions.md#shuffle) ponieważ bezpośrednio używa URNG.)

- Pojedynczego wystąpienia URNG lub dystrybucji nie może bezpiecznie można wywołać jednocześnie, ponieważ uruchomiona URNG lub dystrybucji jest operacji modyfikowania. Aby uzyskać więcej informacji, zobacz [bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md).

- [Wstępnie zdefiniowane elementy TypeDef](#typedefs) kilku aparaty są dostarczane, co jest preferowany sposób tworzenia URNG, jeśli jest używany aparat.

- Parowanie najbardziej przydatne w przypadku większości aplikacji jest `mt19937` aparat z `uniform_int_distribution`, jak pokazano w [przykładowy kod](#code) dalszej części tego artykułu.

Istnieje wiele opcji do wyboru w \<losowe > nagłówka i z nich jest preferowane nieaktualne funkcji C Runtime `rand()`. Aby uzyskać informacje o problem z `rand()` i w jaki sposób \<losowe > dotyczy tych nieprawidłowości, zobacz [ten film](http://go.microsoft.com/fwlink/p/?linkid=397615).

## <a name="code"></a> Przykłady

Poniższy przykład kodu pokazuje sposób generowania niektórych liczb losowych w takim przypadku pięć ich przy użyciu generator utworzone za pomocą inicjatora deterministyczna.

```cpp
#include <random>
#include <iostream>

using namespace std;

int main()
{
    random_device rd;   // non-deterministic generator
    mt19937 gen(rd());  // to seed mersenne twister.
                        // replace the call to rd() with a
                        // constant value to get repeatable
                        // results.

    for (int i = 0; i < 5; ++i) {
        cout << gen() << " "; // print the raw output of the generator.
    }
    cout << endl;
}
```

```Output
2430338871 3531691818 2723770500 3252414483 3632920437
```

Są to liczb losowych wysokiej jakości i różnych zawsze działa ten program, nie są one zawsze przydatne zakresu. Aby kontrolować zakres, użyj uniform dystrybucji, jak pokazano w poniższym kodzie:

```cpp
#include <random>
#include <iostream>

using namespace std;

int main()
{
    random_device rd;   // non-deterministic generator
    mt19937 gen(rd());  // to seed mersenne twister.
    uniform_int_distribution<> dist(1,6); // distribute results between 1 and 6 inclusive.

    for (int i = 0; i < 5; ++i) {
        cout << dist(gen) << " "; // pass the generator to the distribution.
    }
    cout << endl;
}
```

```Output
5 1 6 1 2
```

Następny przykładowy kod przedstawia bardziej realistyczne zestawu przypadków użycia z jednolicie rozproszonej losowe generatory numer zmiana kolejności zawartość wektora i tablicy.

```cpp
// cl.exe /EHsc /nologo /W4 /MTd
#include <algorithm>
#include <array>
#include <iostream>
#include <random>
#include <string>
#include <vector>
#include <functional> // ref()

using namespace std;

template <typename C> void print(const C& c) {
    for (const auto& e : c) {
        cout << e << " ";
    }

    cout << endl;
}

template <class URNG>
void test(URNG& urng) {

    // Uniform distribution used with a vector
    // Distribution is [-5, 5] inclusive
    uniform_int_distribution<int> dist(-5, 5);
    vector<int> v;

    for (int i = 0; i < 20; ++i) {
        v.push_back(dist(urng));
    }

    cout << "Randomized vector: ";
    print(v);

    // Shuffle an array
    // (Notice that shuffle() takes a URNG, not a distribution)
    array<string, 26> arr = { { "H", "He", "Li", "Be", "B", "C", "N", "O", "F",
        "Ne", "Na", "Mg", "Al", "Si", "P", "S", "Cl", "Ar", "K", "Ca", "Sc",
        "Ti", "V", "Cr", "Mn", "Fe" } };

    shuffle(arr.begin(), arr.end(), urng);

    cout << "Randomized array: ";
    print(arr);
    cout << "--" << endl;
}

int main()
{
    // First run: non-seedable, non-deterministic URNG random_device
    // Slower but crypto-secure and non-repeatable.
    random_device rd;
    cout << "Using random_device URNG:" << endl;
    test(rd);

    // Second run: simple integer seed, repeatable results
    cout << "Using constant-seed mersenne twister URNG:" << endl;
    mt19937 engine1(12345);
    test(engine1);

    // Third run: random_device as a seed, different each run
    // (Desirable for most purposes)
    cout << "Using non-deterministic-seed mersenne twister URNG:" << endl;
    mt19937 engine2(rd());
    test(engine2);

    // Fourth run: "warm-up" sequence as a seed, different each run
    // (Advanced uses, allows more than 32 bits of randomness)
    cout << "Using non-deterministic-seed \"warm-up\" sequence mersenne twister URNG:" << endl;
    array<unsigned int, mt19937::state_size> seed_data;
    generate_n(seed_data.begin(), seed_data.size(), ref(rd));
    seed_seq seq(begin(seed_data), end(seed_data));
    mt19937 engine3(seq);
    test(engine3);
}
```

```Output
Using random_device URNG:
Randomized vector: 5 -4 2 3 0 5 -2 0 4 2 -1 2 -4 -3 1 4 4 1 2 -2
Randomized array: O Li V K C Ti N Mg Ne Sc Cl B Cr Mn Ca Al F P Na Be Si Ar Fe S He H
--
Using constant-seed mersenne twister URNG:
Randomized vector: 3 -1 -5 0 0 5 3 -4 -3 -4 1 -3 0 -3 -2 -4 5 1 -1 -1
Randomized array: Al O Ne Si Na Be C N Cr Mn H V F Sc Mg Fe K Ca S Ti B P Ar Cl Li He
--
Using non-deterministic-seed mersenne twister URNG:
Randomized vector: 5 -4 0 2 1 -2 4 4 -4 0 0 4 -5 4 -5 -1 -3 0 0 3
Randomized array: Si Fe Al Ar Na P B Sc H F Mg Li C Ti He N Mn Be O Ca Cr V K Ne Cl S
--
Using non-deterministic-seed "warm-up" sequence mersenne twister URNG:
Randomized vector: -1 3 -2 4 1 3 0 -5 5 -5 0 0 5 0 -3 3 -4 2 5 0
Randomized array: Si C Sc H Na O S Cr K Li Al Ti Cl B Mn He Fe Ne Be Ar V P Ca N Mg F
--
```

Ten kod ilustruje dwóch różnych randomizations — Ustaw losowy wektorem liczb całkowitych i losowo tablicę danych indeksowanego — przy użyciu funkcji szablonu testu. Pierwsze wywołanie funkcji test używa bezpiecznych kryptograficznego, deterministyczna, nie seedable, powtarzalne URNG `random_device`. Drugi testu używa `mersenne_twister_engine` jako URNG, z deterministyczne inicjatora stałej 32-bitowa, co oznacza są powtarzalne wyniki. Trzeci testu ziarna `mersenne_twister_engine` z wynikiem deterministyczna 32-bitowych z `random_device`. Uruchomienie testu czwarty rozszerza na tym za pomocą [inicjatora sekwencji](../standard-library/seed-seq-class.md) wypełnione `random_device` wyników, które skutecznie zawiera więcej niż 32-bitowych losowości deterministyczna (ale nadal nie crypto-secure). Aby uzyskać więcej informacji Przeczytaj na.

## <a name="listing"></a> Lista kategorii

###  <a name="urngs"></a> Uniform generatory liczb losowych

URNGs często są opisane w tych właściwości:

1. **Długość okresu**: liczby iteracji trwa powtórzenie sekwencji liczb wygenerowany. Im dłuższy tym lepiej.

2. **Wydajność**: jak szybko można wygenerować liczb i ilość pamięci potrzebny. Mniejsze tym lepiej.

3. **Jakość**: jak blisko true liczb losowych wygenerowanego sekwencji jest. Jest to często nazywane "*losowości*".

W poniższych sekcjach wymieniono uniform losowych liczb generatory (URNGs) w \<losowe > nagłówka.

####  <a name="rd"></a> Generator deterministyczna

|||
|-|-|
|[random_device, klasa](../standard-library/random-device-class.md)|Generuje deterministyczna, bezpieczne kryptograficznie losowe sekwencji za pomocą zewnętrznego urządzenia. Zazwyczaj używany do generowania aparatu. Niska wydajność bardzo wysokiej jakości. Aby uzyskać więcej informacji, zobacz [uwagi](#comments).|

####  <a name="typedefs"></a> Definicje typów aparat wstępnie zdefiniowanych parametrów

Tworzenie wystąpień aparaty i adapterów aparatu. Aby uzyskać więcej informacji, zobacz [aparaty i dystrybucji](#engdist).

- `default_random_engine` Domyślny aparat.
 `typedef mt19937 default_random_engine;`

- `knuth_b` Aparat Knuth.
 `typedef shuffle_order_engine<minstd_rand0, 256> knuth_b;`

- `minstd_rand0` 1988 minimalnego standardowe aparat (Nowak, Goodman i Tomaszewski, 1969).
 `typedef linear_congruential_engine<unsigned int, 16807, 0, 2147483647> minstd_rand0;`

- `minstd_rand` Zaktualizowany aparat standardowe minimalnego `minstd_rand0` (wstrzymywanie Tomaszewski i Stockmeyer, 1993).
 `typedef linear_congruential_engine<unsigned int, 48271, 0, 2147483647> minstd_rand;`

- `mt19937` 32-bitowe ramach projektu Mersenne — trąba powietrzna aparat (Matsumoto i Nishimura, 1998).
 `typedef mersenne_twister_engine<unsigned int, 32, 624, 397,      31, 0x9908b0df,      11, 0xffffffff,      7, 0x9d2c5680,      15, 0xefc60000,      18, 1812433253> mt19937;`

- `mt19937_64` 64-bitowych ramach projektu Mersenne — trąba powietrzna aparat (Matsumoto i Nishimura, 2000).
 `typedef mersenne_twister_engine<unsigned long long, 64, 312, 156,      31, 0xb5026f5aa96619e9ULL,      29, 0x5555555555555555ULL,      17, 0x71d67fffeda60000ULL,      37, 0xfff7eee000000000ULL,      43, 6364136223846793005ULL> mt19937_64;`

- `ranlux24` Aparat RANLUX 24-bitowego (Lüscher pole i Krzysztof uprawnionego 1994 r.).
 `typedef discard_block_engine<ranlux24_base, 223, 23> ranlux24;`

- `ranlux24_base` Użyty jako podstawa dla `ranlux24`.
 `typedef subtract_with_carry_engine<unsigned int, 24, 10, 24> ranlux24_base;`

- `ranlux48` Aparat RANLUX 48-bitowe (Lüscher pole i Krzysztof uprawnionego 1994 r.).
 `typedef discard_block_engine<ranlux48_base, 389, 11> ranlux48;`

- `ranlux48_base` Użyty jako podstawa dla `ranlux48`.
 `typedef subtract_with_carry_engine<unsigned long long, 48, 5, 12> ranlux48_base;`

####  <a name="eng"></a> Aparat szablonów

Aparat szablony są używane jako autonomiczny URNGs lub aparaty podstawowej przekazane do [aparat adapterów](#engadapt). Zazwyczaj są tworzone z [wstępnie zdefiniowane typedef aparat](#typedefs) i przekazywane do [dystrybucji](#distributions). Aby uzyskać więcej informacji, zobacz [aparaty i dystrybucji](#engdist) sekcji.

|||
|-|-|
|[linear_congruential_engine, klasa](../standard-library/linear-congruential-engine-class.md)|Generuje losowe sekwencji przy użyciu algorytmu congruential liniowej. Najbardziej simplistic i najniższym jakości.|
|[mersenne_twister_engine, klasa](../standard-library/mersenne-twister-engine-class.md)|Generuje losowe sekwencji za pomocą algorytmu — trąba powietrzna w ramach projektu Mersenne. Najbardziej złożonych i jest najwyższej jakości, z wyjątkiem random_device — klasa. Bardzo duża wydajność.|
|[subtract_with_carry_engine, klasa](../standard-library/subtract-with-carry-engine-class.md)|Generuje losowe sekwencji za pomocą algorytmu subtract z przenoszące. Udoskonalenia w `linear_congruential_engine`, ale znacznie mniejszą jakości i wydajność niż `mersenne_twister_engine`.|

####  <a name="engadapt"></a> Aparat szablonów karty

Aparat adapterów są szablony, które dostosowania innych aparatów (podstawowy). Zazwyczaj są tworzone z [wstępnie zdefiniowane typedef aparat](#typedefs) i przekazywane do [dystrybucji](#distributions). Aby uzyskać więcej informacji, zobacz [aparaty i dystrybucji](#engdist) sekcji.

|||
|-|-|
|[discard_block_engine, klasa](../standard-library/discard-block-engine-class.md)|Generuje losowe sekwencji odrzucając wartości zwracanych przez silnik podstawowej.|
|[independent_bits_engine, klasa](../standard-library/independent-bits-engine-class.md)|Generuje losowe sekwencję z określoną liczbę bitów przez przepakowaniu bitów spośród wartości zwróconych przez silnik podstawowej.|
|[shuffle_order_engine, klasa](../standard-library/shuffle-order-engine-class.md)|Generuje losowe sekwencji zmiana kolejności wartości zwracane z jego podstawowej aparatu.|

[[Aparat szablonów](#eng)]

###  <a name="distributions"></a> Dystrybucje liczb losowych

W poniższych sekcjach wymieniono dystrybucje w \<losowe > nagłówka. Dystrybucje są mechanizm przetwarzania końcowego, zwykle za pomocą URNG dane wyjściowe jako dane wejściowe i dystrybucji danych wyjściowych przez funkcję zdefiniowanych statystyczne gęstości prawdopodobieństwa. Aby uzyskać więcej informacji, zobacz [aparaty i dystrybucji](#engdist) sekcji.

#### <a name="uniform-distributions"></a>Jednolite dystrybucji

|||
|-|-|
|[uniform_int_distribution, klasa](../standard-library/uniform-int-distribution-class.md)|Tworzy dystrybucji wartości jednolitego całkowitą w zakresie w interwale zamknięte \[a, b] (włącznie włącznie).|
|[uniform_real_distribution, klasa](../standard-library/uniform-real-distribution-class.md)|Tworzy uniform rzeczywistym dystrybucji wartość (zmiennoprzecinkowa) w zakresie w zakresie połowy Otwórz [a b) (wraz z wartościami granicznymi wyłączne).|
|[generate_canonical](../standard-library/random-functions.md#generate_canonical)|Tworzy nawet dystrybucji wartości rzeczywistych (liczba zmiennoprzecinkowa) danego dokładności między [0, 1) (wraz z wartościami granicznymi wyłączne).|

[[Losowych liczb dystrybucje](#distributions)]

#### <a name="bernoulli-distributions"></a>Dystrybucje Bernoulliego

|||
|-|-|
|[bernoulli_distribution, klasa](../standard-library/bernoulli-distribution-class.md)|Tworzy Rozkład Bernoulliego `bool` wartości.|
|[binomial_distribution, klasa](../standard-library/binomial-distribution-class.md)|Tworzy dwumianowy z wartości całkowitych.|
|[geometric_distribution, klasa](../standard-library/geometric-distribution-class.md)|Tworzy geometrycznych rozkład wartości będące liczbami całkowitymi.|
|[negative_binomial_distribution, klasa](../standard-library/negative-binomial-distribution-class.md)|Tworzy ujemny dwumianowy z wartości całkowitych.|

[[Losowych liczb dystrybucje](#distributions)]

#### <a name="normal-distributions"></a>Rozkład normalny

|||
|-|-|
|[cauchy_distribution, klasa](../standard-library/cauchy-distribution-class.md)|Tworzy dystrybucji Cauchy wartości rzeczywistych (liczba zmiennoprzecinkowa).|
|[chi_squared_distribution, klasa](../standard-library/chi-squared-distribution-class.md)|Tworzy rozkład chi kwadrat wartości rzeczywistych (liczba zmiennoprzecinkowa).|
|[fisher_f_distribution, klasa](../standard-library/fisher-f-distribution-class.md)|Tworzy F dystrybucji (znanej także jako jego Snedecor F dystrybucji lub dystrybucji Snedecor Fishera) wartości rzeczywistych (liczba zmiennoprzecinkowa).|
|[lognormal_distribution, klasa](../standard-library/lognormal-distribution-class.md)|Tworzy rozkładu normalnego dziennika wartości rzeczywistych (liczba zmiennoprzecinkowa).|
|[normal_distribution, klasa](../standard-library/normal-distribution-class.md)|Tworzy normalnej dystrybucji (Gaussa) wartości rzeczywistych (liczba zmiennoprzecinkowa).|
|[student_t_distribution, klasa](../standard-library/student-t-distribution-class.md)|Tworzy studenta *t*— rozkład wartości rzeczywistych (liczba zmiennoprzecinkowa).|

[[Losowych liczb dystrybucje](#distributions)]

#### <a name="poisson-distributions"></a>Rozkład Poissona

|||
|-|-|
|[exponential_distribution, klasa](../standard-library/exponential-distribution-class.md)|Tworzy rozkład wykładniczy wartości rzeczywistych (liczba zmiennoprzecinkowa).|
|[extreme_value_distribution, klasa](../standard-library/extreme-value-distribution-class.md)|Tworzy dystrybucji najwyższą wartość rzeczywista (liczba zmiennoprzecinkowa) wartości.|
|[gamma_distribution, klasa](../standard-library/gamma-distribution-class.md)|Tworzy dystrybucji gamma wartości rzeczywistych (liczba zmiennoprzecinkowa).|
|[poisson_distribution, klasa](../standard-library/poisson-distribution-class.md)|Tworzy rozkład Poissona wartości będące liczbami całkowitymi.|
|[weibull_distribution, klasa](../standard-library/weibull-distribution-class.md)|Tworzy dystrybucji Weibulla wartości rzeczywistych (liczba zmiennoprzecinkowa).|

[[Losowych liczb dystrybucje](#distributions)]

#### <a name="sampling-distributions"></a>Dystrybucje pobierania próbek

|||
|-|-|
|[discrete_distribution, klasa](../standard-library/discrete-distribution-class.md)|Tworzy dystrybucji odrębny liczby całkowitej.|
|[piecewise_constant_distribution, klasa](../standard-library/piecewise-constant-distribution-class.md)|Tworzy piecewise dystrybucji stałej wartości rzeczywistych (liczba zmiennoprzecinkowa).|
|[piecewise_linear_distribution, klasa](../standard-library/piecewise-linear-distribution-class.md)|Tworzy piecewise liniowej dystrybucji wartości rzeczywistych (liczba zmiennoprzecinkowa).|

[[Losowych liczb dystrybucje](#distributions)]

### <a name="utility-functions"></a>Funkcje pomocnicze

Ta sekcja zawiera funkcje ogólne narzędzie zawarte w \<losowe > nagłówka.

|||
|-|-|
|[seed_seq, klasa](../standard-library/seed-seq-class.md)|Generuje sekwencji-ukierunkowane zaszyfrowane inicjatora. Pozwala uniknąć replikacji losowe variate strumieni. Przydatne w przypadku wielu URNGs są utworzone z aparatów.|

### <a name="operators"></a>Operatory

Ta sekcja zawiera operatory w \<losowe > nagłówka.

|||
|-|-|
|`operator==`|Sprawdza, czy URNG po lewej stronie operatora jest równa aparatu po prawej stronie.|
|`operator!=`|Sprawdza, czy URNG po lewej stronie operatora nie jest równa aparatu po prawej stronie.|
|`operator<<`|Zapisuje informacje o stanie do strumienia.|
|`operator>>`|Wyodrębnia informacje o stanie ze strumienia.|

## <a name="engdist"></a> Aparaty i dystrybucji

Zobacz następujące sekcje zawierają informacje o każdej z tych kategorii klasy szablonu zdefiniowany w \<losowe >. Obu tych kategorii klasy szablonu pobranie typu jako argumentu i użyj nazwy parametru szablonu współużytkowanego opisujących właściwości typu, które są dozwolone jako typu rzeczywistego argumentu w następujący sposób:

- `IntType` Wskazuje `short`, `int`, `long`, `long long`, `unsigned short`, `unsigned int`, `unsigned long`, lub `unsigned long long`.

- `UIntType` Wskazuje `unsigned short`, `unsigned int`, `unsigned long`, lub `unsigned long long`.

- `RealType` Wskazuje `float`, `double`, lub `long double`.

### <a name="engines"></a>Aparaty

[Aparat szablonów](#eng) i [szablony karty aparatu](#engadapt) szablonów, w której parametry dostosowywać generator utworzony.

*Aparat* klasy lub klasy szablonu, którego wystąpienia (generatory) działać jako źródło liczb losowych jednolicie jest rozdzielona między wartością minimalną i maksymalną. *Karty aparatu* zapewnia sekwencję wartości, które mają różne losowości właściwości przez pobieranie wartości produkowane przez niektóre inne losowe aparat numeru i stosowanie algorytmu pewnego rodzaju tych wartości.

Każdy aparat i aparat karty ma następujące elementy:

- `typedef` `numeric-type` `result_type` jest to typ zwracany przez generator `operator()`. `numeric-type` Jest przekazywana jako parametr szablonu podczas tworzenia wystąpienia.

- `result_type operator()` Zwraca wartości, które są równomiernie między `min()` i `max()`.

- `result_type min()` Zwraca minimalną wartość zwracaną przez generator `operator()`. Aparat adapterów Użyj podstawowego aparatu `min()` wynik.

- `result_type max()` Zwraca maksymalną wartość zwracaną przez generator `operator()`. Gdy `result_type` jest typ całkowity (wartości całkowitych) `max()` maksymalna wartość, która faktycznie można zwrócić (włącznie); podczas `result_type` jest typ zmiennoprzecinkowy (przechowywanymi w rzeczywistym) `max()` jest większa niż wszystkie wartości najmniejszej wartości który może być zwracany (z systemem innym niż — włącznie). Aparat adapterów Użyj podstawowego aparatu `max()` wynik.

- `void seed(result_type s)` nasiona generator o wartości początkowej `s`. Aparaty, podpis jest `void seed(result_type s = default_seed)` dla Obsługa parametrów domyślnych (aparat adapterów zdefiniuj oddzielnej `void seed()`, zobacz podsekcji).

- `template <class Seq> void seed(Seq& q)` nasiona generatora przy użyciu [seed_seq —](../standard-library/seed-seq-class.md)`Seq`.

- Jawne konstruktora z argumentem `result_type x` tworzącą generator rozpoczęta tak, jakby przez wywołanie `seed(x)`.

- Jawne konstruktora z argumentem `seed_seq& seq` tworzącą generator rozpoczęta tak, jakby przez wywołanie `seed(seq)`.

- `void discard(unsigned long long count)` wywołuje `operator()` `count` czasu i odrzuca każdej wartości.

**Aparat adapterów** dodatkowo obsługuje tych elementów członkowskich (`Engine` jest pierwszy parametr szablonu adaptera aparat wyznaczenie typ podstawowy aparat):

- Domyślny konstruktor zainicjować generatora tak, jakby z podstawowej aparat domyślnego konstruktora.

- Jawne konstruktora z argumentem `const Engine& eng`. To obsługuje konstrukcji kopiowania za pomocą aparatu podstawowej.

- Jawne konstruktora z argumentem `Engine&& eng`. To obsługuje konstrukcji przenoszenia przy użyciu aparatu podstawowej.

- `void seed()` który inicjuje generator o wartości początkowej domyślny aparat podstawowej.

- `const Engine& base()` Funkcja właściwość, która zwraca podstawowej aparatem, który został użyty do utworzenia generatora.

Każdy silnik utrzymuje *stanu* , który określa kolejność wartości, które będą generowane przez kolejne wywołania `operator()`. Stany dwóch generatory utworzonych na podstawie aparaty tego samego typu można porównać przy użyciu `operator==` i `operator!=`. Jeśli porównać dwa stany jako równe, wygeneruje taką samą sekwencję wartości. Stan obiektu, który można zapisać do strumienia jako sekwencję 32-bitowej wartości bez znaku przy użyciu `operator<<` generatora. Stan nie zostanie zmieniona przez zapisanie go. Zapisany stan może zostać odczytany do generatora utworzone z tego samego typu aparatu przy użyciu `operator>>`.

### <a name="distributions"></a>Dystrybucje

A [losowe dystrybucje numer](#distributions) jest klasa lub klasy szablonu, którego wystąpienia przekształcenie strumienia jednolicie rozproszonej liczb losowych uzyskane z aparatu do strumienia losowych liczb, które mają dystrybucji określonego. Każdy dystrybucji ma następujące elementy:

- `typedef` `numeric-type` `result_type` jest to typ zwracany przez dystrybucji `operator()`. `numeric-type` Jest przekazywana jako parametr szablonu podczas tworzenia wystąpienia.

- `template <class URNG> result_type operator()(URNG& gen)` Zwraca wartości, które są dystrybuowane zgodnie z definicją dystrybucji przy użyciu `gen` jako źródło jednolicie rozproszonej losowych wartości i zapisana *parametry dystrybucji*.

- `template <class URNG> result_type operator()(URNG& gen, param_type p)` Zwraca rozkład zgodnie z definicją dystrybucji wartości przy użyciu `gen` jako źródło jednolicie rozproszonej losowych wartości i struktura parametrów `p`.

- `typedef` `unspecified-type` `param_type` Pakiet parametrów opcjonalnie przekazywany do `operator()` i jest używany zamiast przechowywane parametry do generowania jego wartości zwracanej.

- A `const param&` Konstruktor inicjuje przechowywane parametry z jej argument.

- `param_type param() const` pobiera parametry przechowywane.

- `void param(const param_type&)` Ustawia parametry przechowywane z jej argument.

- `result_type min()` Zwraca minimalną wartość zwracaną przez dystrybucji `operator()`.

- `result_type max()` Zwraca maksymalną wartość zwracaną przez dystrybucji `operator()`. Gdy `result_type` jest typ całkowity (wartości całkowitych) `max()` maksymalna wartość, która faktycznie można zwrócić (włącznie); podczas `result_type` jest typ zmiennoprzecinkowy (przechowywanymi w rzeczywistym) `max()` jest większa niż wszystkie wartości najmniejszej wartości który może być zwracany (z systemem innym niż — włącznie).

- `void reset()` odrzuca wszystkie buforowane wartości, tak aby wynik następne wywołanie `operator()` nie zależy od wartości uzyskane z aparatu przed wywołaniem.

Struktura parametru jest obiekt, który przechowuje wszystkie parametry potrzebne do dystrybucji. Ten przewodnik zawiera:

- `typedef` `distribution-type` `distribution_type`, który jest typem jego dystrybucji.

- Zawiera co najmniej jeden konstruktorów przyjmujących tego samego parametru jako podjęcia konstruktorów dystrybucji.

- Te same funkcje dostępu do parametru jako dystrybucji.

- Operatory porównania równości i nierówności.

Aby uzyskać więcej informacji zobacz tematy podrzędne odwołanie poniżej tego, połączone wcześniej w tym artykule.

## <a name="comments"></a> Uwagi

Istnieją dwa URNGs bardzo przydatne w programie Visual Studio —`mt19937` i `random_device`, jak pokazano w poniższej tabeli porównania:

|URNG|Szybkie|Zabezpieczanie kryptograficznego|Seedable|Deterministyczna|
|----------|-----------|---------------------|---------------|--------------------|
|`mt19937`|Tak|Nie|Tak|Tak<sup>*</sup>|
|`random_device`|Nie|Tak|Nie|Nie|

<sup>* Jeśli wyposażone w znanych inicjatora.</sup>

Mimo że standardowi ISO C++ nie wymaga `random_device` do kryptograficznie zabezpieczenia, w programie Visual Studio jest zaimplementowany jako kryptograficznie bezpieczny. (Termin "kryptograficznie bezpiecznego" oznacza gwarancji, ale odwołuje się do minimalny poziom entropii — i w związku z tym poziomu przewidywalności — algorytm danego losowe. Aby uzyskać więcej informacji, zobacz artykuł Wikipedia [kryptograficznie bezpiecznego generatora liczb pseudolosowych](http://go.microsoft.com/fwlink/p/?linkid=398017).) Ponieważ standardowi ISO C++ nie wymaga to, może wprowadzić innych platform `random_device` jako proste pseudolosowego generatora liczb (kryptograficznie niezabezpieczony) i tylko może być odpowiednie jako źródło inicjatora dla innego generatora. Sprawdź dokumentację dla tych platform, korzystając z `random_device` w kodzie i platform.

Zgodnie z definicją `random_device` wyniki nie są odtworzenia i efektem ubocznym jest, że może znacznie mniejszą od innych URNGs uruchomione. Większość aplikacji, które nie są wymagane do kryptograficznie można zabezpieczyć użyj `mt19937` lub podobnych aparat, chociaż może zajść potrzeba inicjatora go wywołaniem `random_device`, jak pokazano w [przykładowy kod](#code).

## <a name="see-also"></a>Zobacz także

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)<br/>
