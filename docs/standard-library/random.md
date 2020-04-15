---
title: '&lt;Losowe&gt;'
ms.date: 08/24/2017
f1_keywords:
- <random>
helpviewer_keywords:
- random header
ms.assetid: 60afc25c-b162-4811-97c1-1b65398d4c57
ms.openlocfilehash: 540daa5bafa28b1d56c55daf33f0b5f5461c8ed6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320232"
---
# <a name="ltrandomgt"></a>&lt;Losowe&gt;

Definiuje możliwości generowania liczb losowych, umożliwiając tworzenie jednolicie rozmieszczonych liczb losowych.

## <a name="requirements"></a>Wymagania

**Nagłówek** \<: losowe>

**Przestrzeń nazw:** std

> [!NOTE]
> Losowa biblioteka \<> używa instrukcji "#include <initializer_list>".

## <a name="summary"></a>Podsumowanie

Generator *liczb losowych* jest obiektem, który tworzy sekwencję wartości pseudolosowych. Generator, który produkuje wartości, które są równomiernie rozłożone w określonym zakresie jest *jednolity generator liczb losowych* (URNG). Szablon klasy przeznaczony do działania jako URNG jest określany jako *aparat,* jeśli ta klasa ma pewne wspólne cechy, które zostały omówione w dalszej części tego artykułu. UrnG może być i zwykle jest w połączeniu z *dystrybucją,* przekazując URNG jako argument do dystrybucji `operator()` do produkcji wartości, które są dystrybuowane w sposób, który jest zdefiniowany przez dystrybucję.

Te linki przejść do głównych sekcji tego artykułu:

- [Przykłady](#code)

- [Lista skategoryzowana](#listing)

- [Silniki i dystrybucje](#engdist)

- [Uwagi](#comments)

### <a name="quick-tips"></a>Szybkie porady

Oto kilka wskazówek, o których \<należy pamiętać podczas korzystania z losowych>:

- W większości celów urngs produkcji nieprzetworzonych bitów, które muszą być kształtowane przez dystrybucje. (Godnym uwagi wyjątkiem jest [std::shuffle(),](../standard-library/algorithm-functions.md#shuffle) ponieważ używa urng bezpośrednio.)

- Pojedyncze wystąpienie urng lub dystrybucji nie można bezpiecznie wywołać jednocześnie, ponieważ uruchamianie URNG lub dystrybucji jest operacją modyfikującą. Aby uzyskać więcej informacji, zobacz [Bezpieczeństwo wątków w standardowej bibliotece języka C++](../standard-library/thread-safety-in-the-cpp-standard-library.md).

- [Predefedzone typedefs](#typedefs) kilku silników są dostarczane; jest to preferowany sposób tworzenia URNG, jeśli używany jest silnik.

- Najbardziej przydatne parowanie dla większości `mt19937` aplikacji `uniform_int_distribution`jest aparat z , jak pokazano w [przykładzie kodu](#code) w dalszej części tego artykułu.

Istnieje wiele opcji do wyboru \<w losowym nagłówku>, a każdy z nich jest `rand()`lepszy od przestarzałej funkcji C Runtime . Aby uzyskać informacje o `rand()` tym, \<co jest nie tak i jak losowe> rozwiązuje te niedociągnięcia, zobacz [ten film](https://go.microsoft.com/fwlink/p/?linkid=397615).

## <a name="examples"></a><a name="code"></a>Przykłady

Poniższy przykład kodu pokazuje, jak wygenerować kilka liczb losowych w tym przypadku pięć z nich przy użyciu generatora utworzonego z niedeterministycznym materiałem siewnym.

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

Chociaż są to wysokiej jakości liczby losowe i różne za każdym razem, gdy ten program jest uruchamiany, niekoniecznie są one w użytecznym zakresie. Aby kontrolować zakres, należy użyć równomiernego rozkładu, jak pokazano w poniższym kodzie:

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

Następny przykład kodu pokazuje bardziej realistyczny zestaw przypadków użycia z jednolicie rozproszonych generatorów liczb losowych tasowania zawartości wektora i tablicy.

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

Ten kod pokazuje dwie różne randomizacji — losowo wektor liczb całkowitych i shuffle tablicy indeksowanych danych — z funkcją szablonu testu. Pierwsze wywołanie funkcji testowej używa krypto-bezpieczne, niedeterministyczne, nie-seedable, `random_device`nie powtarzalne URNG . Drugi przebieg testu `mersenne_twister_engine` używa jako URNG, z deterministycznym stałym 32-bitowym materiałem siewnym, co oznacza, że wyniki są powtarzalne. Trzeci test uruchomić `mersenne_twister_engine` nasiona z 32-bitowy `random_device`wynik niedeterministyczny z . Czwarty przebieg testu rozszerza się na ten temat `random_device` przy użyciu [sekwencji materiału siewnego](../standard-library/seed-seq-class.md) wypełnionej wynikami, co skutecznie daje więcej niż 32-bitową niedeterministyczną losowość (ale nadal nie jest bezpieczna krypto). Aby uzyskać więcej informacji, czytaj dalej.

## <a name="categorized-listing"></a><a name="listing"></a>Lista skategoryzowana

### <a name="uniform-random-number-generators"></a><a name="urngs"></a>Jednolite generatory liczb losowych

URNGs są często opisane w kategoriach tych właściwości:

1. **Długość okresu:** Ile iteracji potrzeba, aby powtórzyć sekwencję wygenerowanych liczb. Im dłużej, tym lepiej.

2. **Wydajność:** Jak szybko można wygenerować liczby i ile pamięci zajmuje. Im mniejsza, tym lepiej.

3. **Jakość:** Jak blisko prawdziwych liczb losowych jest wygenerowana sekwencja. Jest to często nazywane "*przypadkowością*".

W poniższych sekcjach przedstawiono jednolite generatory liczb \<losowych (URNGs) podane w losowym nagłówku>.

#### <a name="non-deterministic-generator"></a><a name="rd"></a>Generator niedeterministyczny

|||
|-|-|
|[Klasa random_device](../standard-library/random-device-class.md)|Generuje niedeterministyczną, kryptograficznie bezpieczną losową sekwencję przy użyciu urządzenia zewnętrznego. Zwykle używane do nasion silnika. Niska wydajność, bardzo wysoka jakość. Aby uzyskać więcej informacji, zobacz [Uwagi](#comments).|

#### <a name="engine-typedefs-with-predefined-parameters"></a><a name="typedefs"></a>Typedefs silnika ze wstępnie zdefiniowanymi parametrami

Do tworzenia komunikatów i tworzenia komunikatorów silnika. Aby uzyskać więcej informacji, zobacz [Aparaty i dystrybucje](#engdist).

- `default_random_engine`Domyślny aparat.

    ```cpp
    typedef mt19937 default_random_engine;
    ```

- `knuth_b`Silnik Knuth.

    ```cpp
    typedef shuffle_order_engine<minstd_rand0, 256> knuth_b;
    ```

- `minstd_rand0`1988 minimalny standardowy silnik (Lewis, Goodman i Miller, 1969).

    ```cpp
    typedef linear_congruential_engine<unsigned int, 16807, 0, 2147483647> minstd_rand0;
    ```

- `minstd_rand`Zaktualizowano minimalny `minstd_rand0` silnik standardowy (Park, Miller i Stockmeyer, 1993).

    ```cpp
    typedef linear_congruential_engine<unsigned int, 48271, 0, 2147483647> minstd_rand;
    ```

- `mt19937`32-bitowy silnik Twister Mersenne (Matsumoto i Nishimura, 1998).

    ```cpp
    typedef mersenne_twister_engine<
        unsigned int, 32, 624, 397,
        31, 0x9908b0df,
        11, 0xffffffff,
        7, 0x9d2c5680,
        15, 0xefc60000,
        18, 1812433253> mt19937;
    ```

- `mt19937_64`64-bitowy silnik Twister Mersenne (Matsumoto i Nishimura, 2000).

    ```cpp
    typedef mersenne_twister_engine<
        unsigned long long, 64, 312, 156,
        31, 0xb5026f5aa96619e9ULL,
        29, 0x5555555555555555ULL,
        17, 0x71d67fffeda60000ULL,
        37, 0xfff7eee000000000ULL,
        43, 6364136223846793005ULL> mt19937_64;
    ```

- `ranlux24`24-bitowy silnik RANLUX (Martin Lüscher i Fred James, 1994).

    ```cpp
    typedef discard_block_engine<ranlux24_base, 223, 23> ranlux24;
    ```

- `ranlux24_base`Używany jako podstawa `ranlux24`dla .

    ```cpp
    typedef subtract_with_carry_engine<unsigned int, 24, 10, 24> ranlux24_base;
    ```

- `ranlux48`48-bitowy silnik RANLUX (Martin Lüscher i Fred James, 1994).

    ```cpp
    typedef discard_block_engine<ranlux48_base, 389, 11> ranlux48;
    ```

- `ranlux48_base`Używany jako podstawa `ranlux48`dla .

    ```cpp
    typedef subtract_with_carry_engine<unsigned long long, 48, 5, 12> ranlux48_base;
    ```

#### <a name="engine-templates"></a><a name="eng"></a>Szablony silników

Szablony silników są używane jako samodzielne urny lub jako silniki bazowe przekazywane do [adapterów silnika.](#engadapt) Zazwyczaj są one tworzone z [predefi zdefiniowanym typedef silnika](#typedefs) i przekazywane do [dystrybucji](#distributions). Aby uzyskać więcej informacji, zobacz [aparaty i dystrybucje](#engdist) sekcji.

|||
|-|-|
|[linear_congruential_engine — Klasa](../standard-library/linear-congruential-engine-class.md)|Generuje losową sekwencję przy użyciu liniowego algorytmu konwekcyjnego. Najbardziej uproszczone i najniższej jakości.|
|[Klasa mersenne_twister_engine](../standard-library/mersenne-twister-engine-class.md)|Generuje losową sekwencję przy użyciu algorytmu twister Mersenne. Najbardziej złożone i jest najwyższej jakości, z wyjątkiem random_device klasy. Bardzo szybka wydajność.|
|[Klasa subtract_with_carry_engine](../standard-library/subtract-with-carry-engine-class.md)|Generuje losową sekwencję przy użyciu algorytmu odejmowania z przenoszeniem. Poprawa na `linear_congruential_engine`, ale znacznie niższa jakość i wydajność niż `mersenne_twister_engine`.|

#### <a name="engine-adaptor-templates"></a><a name="engadapt"></a>Szablony adapterów silnika

Adaptery silnika to szablony, które dostosowują inne (podstawowe) silniki. Zazwyczaj są one tworzone z [predefi zdefiniowanym typedef silnika](#typedefs) i przekazywane do [dystrybucji](#distributions). Aby uzyskać więcej informacji, zobacz [aparaty i dystrybucje](#engdist) sekcji.

|||
|-|-|
|[Klasa discard_block_engine](../standard-library/discard-block-engine-class.md)|Generuje losową sekwencję, odrzucając wartości zwracane przez jego aparat podstawowy.|
|[Klasa independent_bits_engine](../standard-library/independent-bits-engine-class.md)|Generuje losową sekwencję z określoną liczbą bitów przez przepakowanie bitów z wartości zwracanych przez jego aparat podstawowy.|
|[shuffle_order_engine — Klasa](../standard-library/shuffle-order-engine-class.md)|Generuje losową sekwencję, ponownie zapisując wartości zwrócone z jego aparatu podstawowego.|

[[Szablony silników](#eng)]

### <a name="random-number-distributions"></a><a name="distributions"></a>Rozkłady liczb losowych

W poniższych sekcjach przedstawiono \<rozkłady podane w losowym nagłówku>. Dystrybucje są mechanizmem przetwarzania końcowego, zwykle przy użyciu wyjścia URNG jako danych wejściowych i dystrybucji danych wyjściowych za pomocą zdefiniowanej funkcji statystycznej gęstości prawdopodobieństwa. Aby uzyskać więcej informacji, zobacz [aparaty i dystrybucje](#engdist) sekcji.

#### <a name="uniform-distributions"></a>Jednolite rozkłady

|||
|-|-|
|[Klasa uniform_int_distribution](../standard-library/uniform-int-distribution-class.md)|Tworzy jednolity rozkład wartości całkowitej w zakresie \[w zamkniętym przedziale a, b] (włącznie).|
|[Klasa uniform_real_distribution](../standard-library/uniform-real-distribution-class.md)|Tworzy jednolity rozkład wartości rzeczywistej (zmiennoprzecinowej) w zakresie w interwale pół-otwartej [a, b) (wyłączności włącznie).|
|[generate_canonical](../standard-library/random-functions.md#generate_canonical)|Tworzy równomierny rozkład rzeczywistych (zmiennoprzecinkowych) wartości danej precyzji w całej [0, 1) (włącznie wyłączne).|

[[Rozkłady liczb losowych](#distributions)]

#### <a name="bernoulli-distributions"></a>Rozkłady Bernoulli

|||
|-|-|
|[Klasa bernoulli_distribution](../standard-library/bernoulli-distribution-class.md)|Tworzy rozkład Bernoulli wartości **bool.**|
|[Klasa binomial_distribution](../standard-library/binomial-distribution-class.md)|Tworzy dwumianowy rozkład wartości całkowitych.|
|[Klasa geometric_distribution](../standard-library/geometric-distribution-class.md)|Tworzy geometryczny rozkład wartości całkowitych.|
|[Klasa negative_binomial_distribution](../standard-library/negative-binomial-distribution-class.md)|Tworzy ujemny rozkład dwumianowy wartości całkowitych.|

[[Rozkłady liczb losowych](#distributions)]

#### <a name="normal-distributions"></a>Rozkłady normalne

|||
|-|-|
|[cauchy_distribution — Klasa](../standard-library/cauchy-distribution-class.md)|Tworzy rozkład Cauchy'ego wartości rzeczywistych (zmiennoprzecinkowych).|
|[Klasa chi_squared_distribution](../standard-library/chi-squared-distribution-class.md)|Tworzy chi-kwadrat rozkład wartości rzeczywistych (zmiennoprzecinkowy).|
|[Klasa fisher_f_distribution](../standard-library/fisher-f-distribution-class.md)|Tworzy rozkład F (znany również jako rozkład F Snedecora lub rozkład Fishera-Snedecora) wartości rzeczywistych (zmiennoprzecinkowych).|
|[Klasa lognormal_distribution](../standard-library/lognormal-distribution-class.md)|Tworzy rozkład log-normal wartości rzeczywistych (zmiennoprzecinkowych).|
|[Klasa normal_distribution](../standard-library/normal-distribution-class.md)|Tworzy normalny (gaussowski) rozkład wartości rzeczywistych (zmiennoprzecinkowych).|
|[student_t_distribution — Klasa](../standard-library/student-t-distribution-class.md)|Tworzy studenta *t-rozkład*wartości rzeczywistych (zmiennoprzecinkowych) wartości.|

[[Rozkłady liczb losowych](#distributions)]

#### <a name="poisson-distributions"></a>Rozkłady Poissona

|||
|-|-|
|[exponential_distribution — Klasa](../standard-library/exponential-distribution-class.md)|Tworzy wykładniczy rozkład wartości rzeczywistych (zmiennoprzecinkowych).|
|[extreme_value_distribution — Klasa](../standard-library/extreme-value-distribution-class.md)|Tworzy skrajne rozkład wartości rzeczywistych (zmiennoprzecinkowych) wartości.|
|[gamma_distribution — Klasa](../standard-library/gamma-distribution-class.md)|Tworzy rozkład gamma wartości rzeczywistych (zmiennoprzecinkowych).|
|[poisson_distribution — Klasa](../standard-library/poisson-distribution-class.md)|Tworzy rozkład poissona wartości całkowitych.|
|[Klasa weibull_distribution](../standard-library/weibull-distribution-class.md)|Tworzy rozkład Weibulla wartości rzeczywistych (zmiennoprzecinkowych).|

[[Rozkłady liczb losowych](#distributions)]

#### <a name="sampling-distributions"></a>Rozkłady próbek

|||
|-|-|
|[Klasa discrete_distribution](../standard-library/discrete-distribution-class.md)|Tworzy dyskretny rozkład liczby całkowitej.|
|[Klasa piecewise_constant_distribution](../standard-library/piecewise-constant-distribution-class.md)|Tworzy fragmentarycznie stały rozkład wartości rzeczywistych (zmiennoprzecinkowych).|
|[piecewise_linear_distribution — Klasa](../standard-library/piecewise-linear-distribution-class.md)|Tworzy fragmentarycznie liniowy rozkład wartości rzeczywistych (zmiennoprzecinkowych).|

[[Rozkłady liczb losowych](#distributions)]

### <a name="utility-functions"></a>Funkcje narzędzia

W tej sekcji wymieniono ogólne \<funkcje narzędzia dostępne w nagłówku> losowej.

|||
|-|-|
|[seed_seq — Klasa](../standard-library/seed-seq-class.md)|Generuje nieuprzechostniczą sekwencję kodowany materiału siewnego. Służy do unikania replikacji losowych strumieni zmiennych. Przydatne, gdy wiele urng są tworzone z silników.|

### <a name="operators"></a>Operatory

W tej sekcji wymieniono \<operatorów podanych w nagłówku> losowej.

|||
|-|-|
|`operator==`|Sprawdza, czy urng po lewej stronie operatora jest równa silnikowi po prawej stronie.|
|`operator!=`|Sprawdza, czy urng po lewej stronie operatora nie jest równa silnikowi po prawej stronie.|
|`operator<<`|Zapisuje informacje o stanie do strumienia.|
|`operator>>`|Wyodrębnia informacje o stanie ze strumienia.|

## <a name="engines-and-distributions"></a><a name="engdist"></a>Silniki i dystrybucje

Zapoznaj się z poniższymi sekcjami, aby uzyskać informacje \<na temat każdej z tych kategorii szablonów klas zdefiniowanych w losowych>. Obie te kategorie szablonów klas przyjmują typ jako argument i używają nazw parametrów szablonu udostępnionego do opisania właściwości typu, które są dozwolone jako rzeczywisty typ argumentu, w następujący sposób:

- `IntType`oznacza **krótki**, **int**, **długi,** **długi,** **niepodpisany krótki,** **niepodpisany int,** **niepodpisany długi**lub **niepodpisany długo.**

- `UIntType`oznacza **niepodpisane krótkie,** **niepodpisane int,** **niepodpisane długie**lub **niepodpisane długie.**

- `RealType`wskazuje **float,** **double**lub **long double**.

### <a name="engines"></a>Silniki

[Szablony silnika](#eng) i [szablony adaptera silnika](#engadapt) to szablony, których parametry dostosowują utworzony generator.

*Aparat* jest szablonem klasy lub klasy, którego wystąpienia (generatory) działają jako źródło liczb losowych równomiernie rozłożonych między wartością minimalną i maksymalną. *Adapter aparatu* dostarcza sekwencję wartości, które mają różne właściwości losowości, biorąc wartości wytwarzane przez inny aparat liczb losowych i stosując algorytm pewnego rodzaju do tych wartości.

Każdy silnik i adapter silnika ma następujące elementy:

- `typedef`jest typem zwracany przez generatora `operator()`. `numeric-type` `result_type` Jest `numeric-type` przekazywana jako parametr szablonu w wystąpieniu.

- `result_type operator()`zwraca wartości, które są `min()` równomiernie rozłożone między i `max()`.

- `result_type min()`zwraca minimalną wartość zwracaną przez `operator()`generatora . Adaptery silnika wykorzystują `min()` wynik silnika bazowego.

- `result_type max()`zwraca maksymalną wartość zwracaną przez `operator()`generatora . Gdy `result_type` jest typem integralnym (wartość `max()` całkowita) jest maksymalną wartością, która może być faktycznie zwracana (włącznie); gdy `result_type` jest typu zmiennoprzecinkowego `max()` (wartość rzeczywista), jest najmniejszą wartość większą niż wszystkie wartości, które mogą być zwracane (non-inclusive). Adaptery silnika wykorzystują `max()` wynik silnika bazowego.

- `void seed(result_type s)`nasiona generatora `s`o wartości materiału siewnego. W przypadku silników `void seed(result_type s = default_seed)` podpis jest przeznaczony do obsługi `void seed()`parametrów domyślnych (adaptery aparatu definiują osobny , patrz następna podsekcja).

- `template <class Seq> void seed(Seq& q)`nasiona generatora za pomocą [seed_seq](../standard-library/seed-seq-class.md)`Seq`.

- Jawny konstruktor `result_type x` z argumentem, który tworzy `seed(x)`generator rozstawiony tak, jakby przez wywołanie .

- Jawny konstruktor `seed_seq& seq` z argumentem, który tworzy `seed(seq)`generator rozstawiony tak, jakby przez wywołanie .

- `void discard(unsigned long long count)`skutecznie `operator()` `count` wywołuje czasy i odrzuca każdą wartość.

**Adaptery silnika** dodatkowo obsługują`Engine` te elementy ( jest pierwszym parametrem szablonu adaptera silnika, określającym typ silnika bazowego):

- Domyślny konstruktor do inicjowania generatora tak, jakby z domyślnego konstruktora aparatu podstawowego.

- Jawny konstruktor `const Engine& eng`z argumentem . Ma to na celu obsługę konstrukcji kopiowania przy użyciu silnika podstawowego.

- Jawny konstruktor `Engine&& eng`z argumentem . Ma to na celu wsparcie konstrukcji ruchowej za pomocą silnika bazowego.

- `void seed()`który inicjuje generator z domyślną wartością inicjatora silnika podstawowego.

- `const Engine& base()`funkcja właściwości, która zwraca aparat podstawowy, który został użyty do skonstruowania generatora.

Każdy aparat utrzymuje *stan,* który określa kolejność wartości, które będą `operator()`generowane przez kolejne wywołania . Stany dwóch generatorów z silników tego samego typu można `operator==` porównać za pomocą i `operator!=`. Jeśli dwa stany porównać jako równe, będą generować taką samą sekwencję wartości. Stan obiektu można zapisać w strumieniu jako sekwencję 32-bitowych niepodpisanych wartości przy użyciu `operator<<` generatora. Stan nie jest zmieniany przez zapisanie go. Zapisany stan można odczytać do generatora wystąpienia z aparatu tego `operator>>`samego typu przy użyciu .

### <a name="distributions"></a>Dystrybucji

[Rozkłady liczb losowych](#distributions) to szablon klasy lub klasy, którego wystąpienia przekształcają strumień równomiernie rozłożonych liczb losowych uzyskanych z aparatu w strumień liczb losowych, które mają określoną dystrybucję. Każda dystrybucja ma następujących członków:

- `typedef`jest typem zwracany przez dystrybucję `operator()`. `numeric-type` `result_type` Jest `numeric-type` przekazywana jako parametr szablonu w wystąpieniu.

- `template <class URNG> result_type operator()(URNG& gen)`zwraca wartości, które są dystrybuowane zgodnie z `gen` definicją dystrybucji, przy użyciu jako źródła równomiernie rozłożonych wartości losowych i *przechowywanych parametrów rozkładu*.

- `template <class URNG> result_type operator()(URNG& gen, param_type p)`zwraca wartości rozłożone zgodnie z definicją dystrybucji, przy użyciu `gen` jako źródła równomiernie rozłożonych wartości losowych i struktury `p`parametrów .

- `typedef`jest pakietem parametrów opcjonalnie przekazanych do `operator()` i jest używany zamiast przechowywanych parametrów do generowania jego wartości zwracanej. `unspecified-type` `param_type`

- Konstruktor `const param&` inicjuje przechowywane parametry z jego argumentu.

- `param_type param() const`pobiera zapisane parametry.

- `void param(const param_type&)`ustawia zapisane parametry z jego argumentu.

- `result_type min()`zwraca minimalną wartość zwracaną przez `operator()`rozkład.

- `result_type max()`zwraca maksymalną wartość zwracaną przez `operator()`rozkład. Gdy `result_type` jest typem integralnym (wartość `max()` całkowita) jest maksymalną wartością, która może być faktycznie zwracana (włącznie); gdy `result_type` jest typu zmiennoprzecinkowego `max()` (wartość rzeczywista), jest najmniejszą wartość większą niż wszystkie wartości, które mogą być zwracane (non-inclusive).

- `void reset()`odrzuca wszystkie buforowane wartości, tak aby wynik `operator()` następnego wywołania nie zależy od żadnych wartości uzyskanych z aparatu przed wywołaniem.

Struktura parametrów jest obiektem, który przechowuje wszystkie parametry potrzebne do dystrybucji. Zawiera ona:

- `typedef``distribution-type` , który jest rodzajem jego `distribution_type`dystrybucji.

- Jeden lub więcej konstruktorów, które przyjmują te same listy parametrów, jak konstruktory dystrybucji podjąć.

- Te same funkcje dostępu do parametrów co dystrybucja.

- Operatory porównywania równości i nierówności.

Aby uzyskać więcej informacji, zobacz podtematy referencyjne poniżej tego, połączone wcześniej w tym artykule.

## <a name="remarks"></a><a name="comments"></a>Uwagi

Istnieją dwa bardzo przydatne urngs`mt19937` w `random_device`programie Visual Studio i — jak pokazano w tej tabeli porównawczej:

|Urng|Szybko|Krypto-bezpieczne|Seedable (Możliwe do wys|Deterministyczne|
|----------|-----------|---------------------|---------------|--------------------|
|`mt19937`|Tak|Nie|Tak|Tak<sup>*</sup>|
|`random_device`|Nie|Tak|Nie|Nie|

<sup>* Po podaniu znanego materiału siewnego.</sup>

Mimo że standard ISO C++ nie wymaga `random_device` kryptografii bezpieczne, w programie Visual Studio jest implementowany do kryptograficznie bezpieczne. (Termin "kryptograficznie bezpieczne" nie oznacza gwarancji, ale odnosi się do minimalnego poziomu entropii, a tym samym do poziomu przewidywalności — danego algorytmu randomizacji zapewnia. Aby uzyskać więcej informacji, zobacz artykuł Wikipedia [Kryptograficznie bezpieczny generator numerów pseudolosowych](https://go.microsoft.com/fwlink/p/?linkid=398017).) Ponieważ norma ISO C++ nie wymaga tego, inne platformy mogą implementować `random_device` jako prosty generator liczb pseudolosowych (nie zabezpieczony kryptograficznie) i mogą być odpowiednie tylko jako źródło materiału siewnego dla innego generatora. Sprawdź dokumentację dla tych `random_device` platform podczas korzystania z kodu między platformami.

Z definicji `random_device` wyniki nie są powtarzalne, a efektem ubocznym jest to, że może działać znacznie wolniej niż inne urny. Większość aplikacji, które nie muszą być kryptograficznie bezpieczne go używać `mt19937` lub podobny aparat, chociaż można zasiewać go z wywołaniem `random_device`, jak pokazano w [przykładzie kodu](#code).

## <a name="see-also"></a>Zobacz też

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)
