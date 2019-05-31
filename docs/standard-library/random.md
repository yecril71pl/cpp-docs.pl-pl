---
title: '&lt;random&gt;'
ms.date: 08/24/2017
f1_keywords:
- <random>
helpviewer_keywords:
- random header
ms.assetid: 60afc25c-b162-4811-97c1-1b65398d4c57
ms.openlocfilehash: 3fd6272ebcb58d48cc943541f32d1195c3fab498
ms.sourcegitcommit: 28eae422049ac3381c6b1206664455dbb56cbfb6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/31/2019
ms.locfileid: "66450792"
---
# <a name="ltrandomgt"></a>&lt;random&gt;

Definiuje urządzenia Generowanie liczby losowej, umożliwiając tworzenie równomiernie rozłożonych liczb losowych.

## <a name="syntax"></a>Składnia

```cpp
#include <random>
```

## <a name="summary"></a>Podsumowanie

A *generator liczb losowych* jest obiektem, który wytwarza sekwencję wartości pseudolosowych. Generator, który tworzy wartości równomiernie rozłożone w określonym zakresie jest *jednolitego Generator liczb losowych* (URNG). Klasa szablonu, zaprojektowany do działania jako URNG nazywa się *aparatu* Jeśli klasa ma pewne typowe cechy, które zostały omówione w dalszej części tego artykułu. Może być URNG — i jest zazwyczaj — w połączeniu z *dystrybucji* przez przekazanie URNG jako argumentu do dystrybucji `operator()` do produkcji wartości, które są rozmieszczone w taki sposób, który jest zdefiniowany przez dystrybucję.

Te łącza przejść do głównych sekcji w tym artykule:

- [Przykłady](#code)

- [Lista kategorii](#listing)

- [Aparaty i dystrybucji](#engdist)

- [Uwagi](#comments)

### <a name="quick-tips"></a>Szybkie wskazówki

Poniżej przedstawiono kilka wskazówek, o których należy pamiętać, korzystając z \<losowy >:

- W większości przypadków URNGs produktu pierwotne bitów, które muszą być ukształtowane przez dystrybucji. (Wyjątkiem istotne jest [std::shuffle()](../standard-library/algorithm-functions.md#shuffle) ponieważ używa ona URNG bezpośrednio.)

- Pojedynczego wystąpienia URNG lub dystrybucji nie bezpiecznie można wywołać jednocześnie, ponieważ działa URNG lub dystrybucji jest operacją modyfikowania. Aby uzyskać więcej informacji, zobacz [bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md).

- [Wstępnie zdefiniowane elementy TypeDef](#typedefs) kilku znajdują się aparatów; jest to preferowany sposób tworzenia URNG, jeśli używany jest silnik.

- Parowanie najbardziej przydatne w przypadku większości aplikacji jest `mt19937` aparatu z `uniform_int_distribution`, jak pokazano na [przykładowy kod](#code) w dalszej części tego artykułu.

Istnieje wiele opcji do wyboru w \<losowy > Nagłówek i dowolny z nich jest przestarzałe funkcji środowiska uruchomieniowego C `rand()`. Aby uzyskać informacje o problem z `rand()` i w jaki sposób \<losowy > adresy te wad zobacz [ten film wideo](https://go.microsoft.com/fwlink/p/?linkid=397615).

## <a name="code"></a> Przykłady

W poniższym przykładzie kodu pokazano, jak można wygenerować niektórych liczb losowych w tym przypadku pięciu je przy użyciu generatora utworzonych za pomocą inicjatora deterministyczna.

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

Gdy są liczb losowych wysokiej jakości i różnych za każdym razem, gdy ten program jest uruchomiony, nie są zawsze w zakresie przydatne. Aby kontrolować zakres, użyj jednolity rozkład, jak pokazano w poniższym kodzie:

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

Następny przykład kodu przedstawia bardziej realistycznego zestaw przypadków użycia z równomiernie rozłożonych liczb losowych rekonfiguracja zawartość wektora i tablicy.

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

Ten kod przedstawia dwa różne randomizations — losowe Określanie wektorem liczb całkowitych i losowo tablicę indeksowane dane — za pomocą funkcji szablonu testów. Pierwsze wywołanie funkcji testowej używa URNG bezpieczne kryptograficznego deterministyczna, nie seedable, powtarzalne `random_device`. Drugi test uruchomiony używa `mersenne_twister_engine` jako URNG, za pomocą deterministyczne inicjatora stałej 32-bitowych, co oznacza, wyniki są powtarzalne. Trzeci testu wartości początkowe `mersenne_twister_engine` z wynikiem niedeterministyczne 32-bitowy z `random_device`. Przebieg testu czwarty rozszerza to przy użyciu [umieszczenia sekwencji](../standard-library/seed-seq-class.md) wypełnione `random_device` wyniki, które skutecznie daje więcej niż losowości niedeterministyczne 32-bitowych (ale nadal nie crypto-secure). Aby uzyskać więcej informacji Czytaj dalej.

## <a name="listing"></a> Lista kategorii

###  <a name="urngs"></a> Jednolite generatory liczb losowych

URNGs są często opisywana w kategoriach tych właściwości:

1. **Długość okresu**: Jak dużo iteracji trwa powtórzenie sekwencji numerów wygenerowany. Im dłuższy lepiej.

2. **Wydajność**: Jak szybko można wygenerować liczb i ilość pamięci, które zajmują. Mniejszy lepiej.

3. **Jakość**: Jak blisko true liczb losowych wygenerowanego sekwencji. Jest to często nazywane "*losowości*".

W poniższych sekcjach wymieniono jednolitego generatorów liczb losowych (URNGs) podany w \<losowy > nagłówka.

####  <a name="rd"></a> Generator deterministyczna

|||
|-|-|
|[random_device, klasa](../standard-library/random-device-class.md)|Generuje losową sekwencję niedeterministyczne i kryptograficznie bezpieczne za pomocą zewnętrznego urządzenia. Zazwyczaj używany do generowania silnika. Niska wydajność, bardzo wysokiej jakości. Aby uzyskać więcej informacji, zobacz [uwagi](#comments).|

####  <a name="typedefs"></a> Aparat definicje typów, przy użyciu wstępnie zdefiniowanych parametrów

Utworzenie wystąpienia aparatów i adapterów aparatu. Aby uzyskać więcej informacji, zobacz [aparatów i dystrybucji](#engdist).

- `default_random_engine` Domyślny aparat.

    ```cpp
    typedef mt19937 default_random_engine;
    ```

- `knuth_b` Aparat Knuth.

    ```cpp
    typedef shuffle_order_engine<minstd_rand0, 256> knuth_b;
    ```

- `minstd_rand0` 1988 minimalny standardowa aparat (Lewis Goodman i Miller 1969).

    ```cpp
    typedef linear_congruential_engine<unsigned int, 16807, 0, 2147483647> minstd_rand0;
    ```

- `minstd_rand` Zaktualizowany aparat standard minimalny `minstd_rand0` (Park Miller i Stockmeyer, 1993).

    ```cpp
    typedef linear_congruential_engine<unsigned int, 48271, 0, 2147483647> minstd_rand;
    ```

- `mt19937` 32-bitowe aparatu Mersenne twister (Matsumoto i Nishimura-1998).

    ```cpp
    typedef mersenne_twister_engine<
        unsigned int, 32, 624, 397,
        31, 0x9908b0df,
        11, 0xffffffff,
        7, 0x9d2c5680,
        15, 0xefc60000,
        18, 1812433253> mt19937;
    ```

- `mt19937_64` 64-bitowe aparatu Mersenne twister (Matsumoto i Nishimura, 2000).

    ```cpp
    typedef mersenne_twister_engine<
        unsigned long long, 64, 312, 156,
        31, 0xb5026f5aa96619e9ULL,
        29, 0x5555555555555555ULL,
        17, 0x71d67fffeda60000ULL,
        37, 0xfff7eee000000000ULL,
        43, 6364136223846793005ULL> mt19937_64;
    ```

- `ranlux24` Aparat RANLUX 24-bitowego (Martin Lüscher i Fred James, 1994 r.).

    ```cpp
    typedef discard_block_engine<ranlux24_base, 223, 23> ranlux24;
    ```

- `ranlux24_base` Używane jako podstawa `ranlux24`.

    ```cpp
    typedef subtract_with_carry_engine<unsigned int, 24, 10, 24> ranlux24_base;
    ```

- `ranlux48` Aparat RANLUX 48-bitowego (Martin Lüscher i Fred James, 1994 r.).

    ```cpp
    typedef discard_block_engine<ranlux48_base, 389, 11> ranlux48;
    ```

- `ranlux48_base` Używane jako podstawa `ranlux48`.

    ```cpp
    typedef subtract_with_carry_engine<unsigned long long, 48, 5, 12> ranlux48_base;
    ```

####  <a name="eng"></a> Aparat szablonów

Szablony aparat są używane jako autonomiczny URNGs lub aparatów bazowy przekazany do [aparatu adapterów](#engadapt). Zazwyczaj są one tworzone przy użyciu [wstępnie zdefiniowane typedef aparatu](#typedefs) i przekazywane do [dystrybucji](#distributions). Aby uzyskać więcej informacji, zobacz [aparatów i dystrybucji](#engdist) sekcji.

|||
|-|-|
|[linear_congruential_engine, klasa](../standard-library/linear-congruential-engine-class.md)|Generuje losową sekwencję przy użyciu liniowego algorytmu liczb pseudolosowych. Najbardziej uproszczony i najniższego jakości.|
|[mersenne_twister_engine, klasa](../standard-library/mersenne-twister-engine-class.md)|Generuje losową sekwencję przy użyciu algorytmu Mersenne twister. Najbardziej złożone i jest najwyższej jakości, z wyjątkiem random_device — klasa. Bardzo wydajne.|
|[subtract_with_carry_engine, klasa](../standard-library/subtract-with-carry-engine-class.md)|Generuje losową sekwencję przy użyciu algorytmu odejmowania z przeniesienia. Ulepszenie dla `linear_congruential_engine`, ale znacznie niższe jakości i wydajności niż `mersenne_twister_engine`.|

####  <a name="engadapt"></a> Aparat adaptera szablonów

Adapterów aparat są szablonami, które dostosowania innymi aparatami (podstawowa). Zazwyczaj są one tworzone przy użyciu [wstępnie zdefiniowane typedef aparatu](#typedefs) i przekazywane do [dystrybucji](#distributions). Aby uzyskać więcej informacji, zobacz [aparatów i dystrybucji](#engdist) sekcji.

|||
|-|-|
|[discard_block_engine, klasa](../standard-library/discard-block-engine-class.md)|Generuje losową sekwencję przez odrzucenie wartości zwracanych przez silnik podstawowy.|
|[independent_bits_engine, klasa](../standard-library/independent-bits-engine-class.md)|Generuje losową sekwencję z określoną liczbą bitów przez przepakowaniu bitów z wartości zwracanych przez silnik podstawowy.|
|[shuffle_order_engine, klasa](../standard-library/shuffle-order-engine-class.md)|Generuje losową sekwencję przez zmianę kolejności wartości zwracanych z silnika podstawowego.|

[[Aparatu szablonów](#eng)]

###  <a name="distributions"></a> Dystrybucje liczb losowych

W poniższych sekcjach wymieniono dystrybucje podawany \<losowy > nagłówka. Dystrybucje to mechanizm przetwarzania końcowego, zazwyczaj przy użyciu danych wyjściowych URNG jako dane wejściowe i dystrybucji danych wyjściowych przez funkcję zdefiniowanych statystyczne gęstości prawdopodobieństwa. Aby uzyskać więcej informacji, zobacz [aparatów i dystrybucji](#engdist) sekcji.

#### <a name="uniform-distributions"></a>Jednolite dystrybucji

|||
|-|-|
|[uniform_int_distribution, klasa](../standard-library/uniform-int-distribution-class.md)|Generuje jednolity wartość rozkład całkowitoliczbowy w zakresie w zamkniętym przedziale \[a, b] (włączne włączne).|
|[uniform_real_distribution, klasa](../standard-library/uniform-real-distribution-class.md)|Generuje jednolity rzeczywistym dystrybucji (bitoąa) w zakresie w interwale połowicznie rozwarty [a, b) (włącznie wyłącznie).|
|[generate_canonical](../standard-library/random-functions.md#generate_canonical)|Generuje równomierny rozkład wartości danego dokładności w rzeczywistym (liczba zmiennoprzecinkowa) [0, 1) (włącznie wyłącznie).|

[[Dystrybucje liczb losowych](#distributions)]

#### <a name="bernoulli-distributions"></a>Dystrybucje Bernoulli'ego

|||
|-|-|
|[bernoulli_distribution, klasa](../standard-library/bernoulli-distribution-class.md)|Generuje rozkład Bernoulli'ego **bool** wartości.|
|[binomial_distribution, klasa](../standard-library/binomial-distribution-class.md)|Generuje rozkład dwumianowy liczb całkowitych.|
|[geometric_distribution, klasa](../standard-library/geometric-distribution-class.md)|Generuje rozkład geometryczny liczb całkowitych.|
|[negative_binomial_distribution, klasa](../standard-library/negative-binomial-distribution-class.md)|Generuje rozkład dwumianowy ujemny liczb całkowitych.|

[[Dystrybucje liczb losowych](#distributions)]

#### <a name="normal-distributions"></a>Dystrybucje normalny

|||
|-|-|
|[cauchy_distribution, klasa](../standard-library/cauchy-distribution-class.md)|Generuje rozkład Cauchy'ego wartości rzeczywistych (liczba zmiennoprzecinkowa).|
|[chi_squared_distribution, klasa](../standard-library/chi-squared-distribution-class.md)|Tworzy rozkładem wartości rzeczywistych (liczba zmiennoprzecinkowa).|
|[fisher_f_distribution, klasa](../standard-library/fisher-f-distribution-class.md)|Tworzy — rozkład F (znany także jako rozkład F Snedecor firmy lub dystrybucji Snedecor Fishera) wartości rzeczywistych (liczba zmiennoprzecinkowa).|
|[lognormal_distribution, klasa](../standard-library/lognormal-distribution-class.md)|Generuje rozkład logarytmiczno normalny, wartości rzeczywistych (liczba zmiennoprzecinkowa).|
|[normal_distribution, klasa](../standard-library/normal-distribution-class.md)|Generuje rozkład normalny (Gaussa) w wartości rzeczywistej (liczba zmiennoprzecinkowa).|
|[student_t_distribution, klasa](../standard-library/student-t-distribution-class.md)|Tworzy studenta *t*-rozkładu wartości rzeczywistych (liczba zmiennoprzecinkowa).|

[[Dystrybucje liczb losowych](#distributions)]

#### <a name="poisson-distributions"></a>Dystrybucje Poissona

|||
|-|-|
|[exponential_distribution, klasa](../standard-library/exponential-distribution-class.md)|Generuje rozkład wykładniczy wartości rzeczywistych (liczba zmiennoprzecinkowa).|
|[extreme_value_distribution, klasa](../standard-library/extreme-value-distribution-class.md)|Generuje rozkład wartości skrajnych wartości rzeczywistych (liczba zmiennoprzecinkowa).|
|[gamma_distribution, klasa](../standard-library/gamma-distribution-class.md)|Generuje rozkład gamma wartości rzeczywistych (liczba zmiennoprzecinkowa).|
|[poisson_distribution, klasa](../standard-library/poisson-distribution-class.md)|Generuje rozkład Poisson liczb całkowitych.|
|[weibull_distribution, klasa](../standard-library/weibull-distribution-class.md)|Generuje rozkład Weibulla wartości rzeczywistych (liczba zmiennoprzecinkowa).|

[[Dystrybucje liczb losowych](#distributions)]

#### <a name="sampling-distributions"></a>Dystrybucje próbkowania

|||
|-|-|
|[discrete_distribution, klasa](../standard-library/discrete-distribution-class.md)|Generuje dyskretny rozkład całkowitoliczbowy.|
|[piecewise_constant_distribution, klasa](../standard-library/piecewise-constant-distribution-class.md)|Generuje rozkład elementowy stałej rozkładu wartości rzeczywistych (liczba zmiennoprzecinkowa).|
|[piecewise_linear_distribution, klasa](../standard-library/piecewise-linear-distribution-class.md)|Generuje rozkład elementowy liniowy rozkładu wartości rzeczywistych (liczba zmiennoprzecinkowa).|

[[Dystrybucje liczb losowych](#distributions)]

### <a name="utility-functions"></a>Funkcje pomocnicze

W tej sekcji przedstawiono funkcje narzędziowe ogólne, podany w \<losowy > nagłówka.

|||
|-|-|
|[seed_seq, klasa](../standard-library/seed-seq-class.md)|Generuje sekwencję — obciążona seed zaszyfrowany. Używany w celu uniknięcia replikacji losowe variate strumieni. Parametr jest przydatne, gdy wiele URNGs są tworzone z silników.|

### <a name="operators"></a>Operatory

Ta sekcja zawiera listę operatorów w \<losowy > nagłówka.

|||
|-|-|
|`operator==`|Sprawdza, czy URNG po lewej stronie operatora jest równy aparatowi po prawej stronie.|
|`operator!=`|Sprawdza, czy URNG po lewej stronie operatora nie jest równy aparatowi po prawej stronie.|
|`operator<<`|Zapisuje informacje o stanie do strumienia.|
|`operator>>`|Wyodrębnia informacje o stanie ze strumienia.|

## <a name="engdist"></a> Aparaty i dystrybucji

Można znaleźć w poniższych sekcjach, aby uzyskać informacje o każdej z tych kategorii klasy szablonu, zdefiniowanych w \<losowy >. Obie te kategorie klasy szablonu typu jako argumentu i użyj nazwy parametru współużytkowanego szablonu do opisywania właściwości typu dozwolonych jako typu rzeczywisty typ argumentu, w następujący sposób:

- `IntType` Wskazuje **krótki**, **int**, **długie**, **long long**, **typ unsigned short**,  **unsigned int**, **unsigned long**, lub **unsigned long long**.

- `UIntType` Wskazuje **typ unsigned short**, **unsigned int**, **unsigned long**, lub **unsigned long long**.

- `RealType` Wskazuje **float**, **double**, lub **typu long double**.

### <a name="engines"></a>Aparaty

[Aparat szablonów](#eng) i [szablony łącznik aparatu](#engadapt) szablonów, których parametry dostosowują generator utworzone.

*Aparatu* jest klasą lub klasą szablonu, której wystąpienia (generatory) działają jako źródło liczb losowych równomiernie podzielone między wartością minimalną i maksymalną. *Łącznik aparatu* dostarcza sekwencję wartości, które mają różne losowości właściwości przez wykonanie wartości generowane przez niektóre inne losowego silnika liczb i stosowanie algorytmu pewnego rodzaju tych wartości.

Każdy silnik i łącznik aparatu ma następujące składowe:

- `typedef` `numeric-type` `result_type` to typ, który jest zwracany przez generator programu `operator()`. `numeric-type` Jest przekazywany jako parametr przy tworzeniu wystąpienia szablonu.

- `result_type operator()` Zwraca wartości równomiernie rozłożone między `min()` i `max()`.

- `result_type min()` Zwraca minimalną wartość, która jest zwracana przez generator programu `operator()`. Aparat adapterów za pomocą podstawowego aparatu `min()` wynik.

- `result_type max()` Zwraca maksymalną wartość, która jest zwracana przez generator programu `operator()`. Gdy `result_type` to integralny typ, (wartości całkowitych), `max()` jest maksymalna wartość, która może rzeczywiście być zwrócony (włącznie); podczas `result_type` (przechowywanymi w rzeczywistym) typu zmiennoprzecinkowego, jest `max()` jest najmniejsza wartość większa niż wszystkie wartości które mogą być zwracane (wyłącznie). Aparat adapterów za pomocą podstawowego aparatu `max()` wynik.

- `void seed(result_type s)` inicjowania inicjuje generator wartością inicjującą `s`. Dla silników, podpis jest `void seed(result_type s = default_seed)` dla Obsługa parametrów domyślnych (aparat adapterów zdefiniować oddzielny `void seed()`, zobacz podsekcji).

- `template <class Seq> void seed(Seq& q)` przy użyciu inicjowania inicjuje generator [seed_seq —](../standard-library/seed-seq-class.md)`Seq`.

- Jawny Konstruktor z argumentem `result_type x` tworząca generator zasilany jak przez wywołanie `seed(x)`.

- Jawny Konstruktor z argumentem `seed_seq& seq` tworząca generator zasilany jak przez wywołanie `seed(seq)`.

- `void discard(unsigned long long count)` skutecznie wywołuje `operator()` `count` razy i odrzuca każdą wartość.

**Aparat adapterów** obsługuje również te elementy członkowskie (`Engine` jest pierwszym parametrem szablonu adaptera silnik podstawowy aparat typu wyznaczaniu):

- Domyślny konstruktor zainicjować generatora tak, jakby z podstawowego aparatu domyślnego konstruktora.

- Jawny Konstruktor z argumentem `const Engine& eng`. To do obsługi konstrukcji kopiowania przy użyciu podstawowego aparatu.

- Jawny Konstruktor z argumentem `Engine&& eng`. To do obsługi konstrukcji przenoszenia przy użyciu podstawowego aparatu.

- `void seed()` który inicjuje generator wartością inicjującą domyślny aparat podstawowej.

- `const Engine& base()` Funkcja właściwość, która zwraca podstawowy aparat, który został użyty do utworzenia generator.

Każdy silnik utrzymuje *stanu* który określa kolejność wartości, które mają być generowane przez kolejne wywołania `operator()`. Stany dwóch generatorów utworzonych na podstawie aparatów tego samego typu można porównać przy użyciu `operator==` i `operator!=`. Jeśli porównanie obu stanów wskazuje jako równe, generują tę samą sekwencję wartości. Stan obiektu, który można zapisać do strumienia jako sekwencja 32-bitowych wartości bez znaku przy użyciu `operator<<` generatora. Stan nie jest zmieniany przez zapisywanie go. Zapisany stan można odczytać na tworzone przez silnik tego samego typu przy użyciu generatora `operator>>`.

### <a name="distributions"></a>Dystrybucje

A [losową liczbę dystrybucje](#distributions) jest klasą lub klasą szablonu, której wystąpienia przekształcają strumień równomiernie rozproszonych liczb losowych uzyskanych przez silnik do strumienia liczb losowych, dla określonych dystrybucji. Każda dystrybucja ma następujące składowe:

- `typedef` `numeric-type` `result_type` jest to typ, który jest zwracany przez funkcję dystrybucji `operator()`. `numeric-type` Jest przekazywany jako parametr przy tworzeniu wystąpienia szablonu.

- `template <class URNG> result_type operator()(URNG& gen)` Zwraca wartości, które są dystrybuowane zgodnie z definicją dystrybucji, za pomocą `gen` jako źródła równomiernie rozłożonych wartości losowych i przechowywanego *parametry dystrybucji*.

- `template <class URNG> result_type operator()(URNG& gen, param_type p)` Zwraca wartości, które są dystrybuowane zgodnie z definicją dystrybucji, za pomocą `gen` jako źródła równomiernie rozłożonych wartości losowych i struktury parametrów `p`.

- `typedef` `unspecified-type` `param_type` Pakiet parametrów opcjonalnie przekazywany do `operator()` i jest używany zamiast przechowywanych parametrów do wygenerowania jego zwracanej wartości.

- A `const param&` Konstruktor inicjuje przechowywanych parametrów z jej argumentów.

- `param_type param() const` pobiera przechowywanych parametrów.

- `void param(const param_type&)` Ustawia przechowywanych parametrów z jej argumentów.

- `result_type min()` Zwraca minimalną wartość zwracaną przez funkcję dystrybucji `operator()`.

- `result_type max()` Zwraca maksymalną wartość zwracaną przez funkcję dystrybucji `operator()`. Gdy `result_type` to integralny typ, (wartości całkowitych), `max()` jest maksymalna wartość, która może rzeczywiście być zwrócony (włącznie); podczas `result_type` (przechowywanymi w rzeczywistym) typu zmiennoprzecinkowego, jest `max()` jest najmniejsza wartość większa niż wszystkie wartości które mogą być zwracane (wyłącznie).

- `void reset()` odrzuca wszystkie wartości z pamięci podręcznej, tak aby wynik następnego wywołania metody `operator()` nie zależy od żadnych wartości uzyskane z aparatu przed wywołaniem.

Struktura parametru jest obiektem, który przechowuje wszystkie parametry potrzebne dla dystrybucji. Zawiera:

- `typedef` `distribution-type` `distribution_type`, który jest typem dystrybucji.

- Wyświetla jeden lub więcej konstruktorów, które przyjmują parametr ten sam jak konstruktory rozkładające.

- Te same funkcje parametr dostęp jak w przypadku dystrybucji.

- Operatory porównania równości i nierówności.

Aby uzyskać więcej informacji zobacz podtematy odwołanie niższego od podanego wcześniej połączona w tym artykule.

## <a name="comments"></a> Uwagi

Istnieją dwa URNGs bardzo przydatne w programie Visual Studio —`mt19937` i `random_device`— jak pokazano w tej tabeli porównania:

|URNG|Szybka|Crypto-secure|Seedable|Deterministyczna|
|----------|-----------|---------------------|---------------|--------------------|
|`mt19937`|Tak|Nie|Yes|Tak<sup>*</sup>|
|`random_device`|Nie|Yes|Nie|Nie|

<sup>* Jeśli klient poda znanych inicjatora.</sup>

Mimo że standardu ISO C++ nie wymaga `random_device` jako kryptograficznie bezpieczny, w programie Visual Studio jest implementowany jako kryptograficznie bezpieczny. (Termin "kryptograficznie bezpieczne" oznacza gwarancje, ale odwołuje się do minimalnego poziomu entropii — i w związku z tym, poziom przewidywalność — algorytm danego losowe. Aby uzyskać więcej informacji, zobacz artykułu w Wikipedii [kryptograficznie bezpieczne generator liczb pseudolosowych](https://go.microsoft.com/fwlink/p/?linkid=398017).) Ponieważ standardu ISO C++ nie wymaga to, innych platform może wdrożyć `random_device` jako prosty numer generatora pseudolosowego (nie kryptograficznie bezpieczne), a następnie tylko może być nieodpowiedni w następujących jako źródło inicjatora dla innego generatora. Zapoznaj się z dokumentacją dla tych platform przy użyciu `random_device` w kodzie dla wielu platform.

Zgodnie z definicją `random_device` wyniki nie są powtarzalne i efekt uboczny jest, że może znacznie wolniejsze niż inne URNGs Uruchom. Większość aplikacji, które nie są wymagane jako kryptograficznie bezpieczny użyj `mt19937` lub podobne aparatu, chociaż może zajść potrzeba umieszczenia go z wywołaniem `random_device`, jak pokazano na [przykładowy kod](#code).

## <a name="see-also"></a>Zobacz także

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)<br/>
