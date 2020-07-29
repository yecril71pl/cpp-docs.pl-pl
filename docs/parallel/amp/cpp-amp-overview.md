---
title: Przegląd C++ AMP
ms.date: 11/19/2018
helpviewer_keywords:
- C++ Accelerated Massive Parallelism, requirements
- C++ Accelerated Massive Parallelism, architecture
- C++ AMP
- C++ Accelerated Massive Parallelism, overview
- C++ Accelerated Massive Parallelism
ms.assetid: 9e593b06-6e3c-43e9-8bae-6d89efdd39fc
ms.openlocfilehash: 249170e1e29d3ca8c488d15be8fa4ccd2b9070c1
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87222761"
---
# <a name="c-amp-overview"></a>Przegląd C++ AMP

C++ Accelerated Massive Parallelism (C++ AMP) przyspiesza wykonywanie kodu C++ przez skorzystanie z zalet sprzętu równoległego danych, takiego jak procesor graficzny (GPU) na dyskretnej karcie graficznej. Za pomocą C++ AMP można zdekodować wielowymiarowe algorytmy danych, aby można było przyspieszyć wykonywanie przy użyciu równoległości na heterogenicznym sprzęcie. Model programowania C++ AMP obejmuje tablice wielowymiarowe, indeksowanie, transfer pamięci, fragmentację i bibliotekę funkcji matematycznych. Za pomocą rozszerzeń języka C++ AMP można kontrolować sposób przenoszenia danych z procesora CPU do procesora GPU i z powrotem, dzięki czemu można poprawić wydajność.

## <a name="system-requirements"></a>Wymagania systemowe

- System Windows 7 lub nowszy

- Windows Server 2008 R2 lub nowszy

- Sprzęt DirectX 11 Level 11,0 lub nowszy

- W przypadku debugowania na emulatorze oprogramowania wymagany jest system Windows 8 lub Windows Server 2012. Na potrzeby debugowania sprzętu należy zainstalować sterowniki karty graficznej. Aby uzyskać więcej informacji, zobacz [Debugowanie kodu GPU](/visualstudio/debugger/debugging-gpu-code).

- Uwaga: AMP nie jest obecnie obsługiwana w ARM64.

## <a name="introduction"></a>Wprowadzenie

Poniższe dwa przykłady ilustrują podstawowe składniki C++ AMP. Załóżmy, że chcesz dodać odpowiednie elementy z tablic 2 1-wymiarowych. Na przykład możesz chcieć dodać `{1, 2, 3, 4, 5}` i `{6, 7, 8, 9, 10}` uzyskać `{7, 9, 11, 13, 15}` . Bez korzystania z C++ AMP można napisać następujący kod, aby dodać liczby i wyświetlić wyniki.

```cpp
#include <iostream>

void StandardMethod() {

    int aCPP[] = {1, 2, 3, 4, 5};
    int bCPP[] = {6, 7, 8, 9, 10};
    int sumCPP[5];

    for (int idx = 0; idx < 5; idx++)
    {
        sumCPP[idx] = aCPP[idx] + bCPP[idx];
    }

    for (int idx = 0; idx < 5; idx++)
    {
        std::cout << sumCPP[idx] << "\n";
    }
}
```

Ważne części kodu są następujące:

- Dane: dane składają się z trzech tablic. Wszystkie mają tę samą rangę (jeden) i długość (pięć).

- Iteracja: pierwsza **`for`** Pętla zapewnia mechanizm do iterowania przez elementy w tablicach. Kod, który chcesz wykonać, aby obliczyć sumy, jest zawarty w pierwszym **`for`** bloku.

- Indeks: `idx` zmienna uzyskuje dostęp do poszczególnych elementów tablic.

Przy użyciu C++ AMP można napisać poniższy kod zamiast.

```cpp
#include <amp.h>
#include <iostream>
using namespace concurrency;

const int size = 5;

void CppAmpMethod() {
    int aCPP[] = {1, 2, 3, 4, 5};
    int bCPP[] = {6, 7, 8, 9, 10};
    int sumCPP[size];

    // Create C++ AMP objects.
    array_view<const int, 1> a(size, aCPP);
    array_view<const int, 1> b(size, bCPP);
    array_view<int, 1> sum(size, sumCPP);
    sum.discard_data();

    parallel_for_each(
        // Define the compute domain, which is the set of threads that are created.
        sum.extent,
        // Define the code to run on each thread on the accelerator.
        [=](index<1> idx) restrict(amp) {
            sum[idx] = a[idx] + b[idx];
        }
    );

    // Print the results. The expected output is "7, 9, 11, 13, 15".
    for (int i = 0; i < size; i++) {
        std::cout << sum[i] << "\n";
    }
}
```

Te same elementy podstawowe są obecne, ale są używane konstrukcje C++ AMP:

- Dane: używasz tablic C++ do konstruowania trzech C++ AMP obiektów [array_view](../../parallel/amp/reference/array-view-class.md) . Podajesz cztery wartości do konstruowania `array_view` obiektu: wartości danych, ranga, typ elementu i długość `array_view` obiektu w każdym wymiarze. Ranga i typ są przesyłane jako parametry typu. Dane i długość są przesyłane jako parametry konstruktora. W tym przykładzie tablica języka C++, która jest przenoszona do konstruktora, jest Jednowymiarowa. Ranga i długość są używane do konstruowania prostokątnego kształtu danych w `array_view` obiekcie, a wartości danych są używane do wypełnienia tablicy. Biblioteka środowiska uruchomieniowego zawiera również [klasę Array](../../parallel/amp/reference/array-class.md), która ma interfejs podobny do `array_view` klasy i został omówiony w dalszej części tego artykułu.

- Iteracja: [funkcja parallel_for_each (C++ amp)](reference/concurrency-namespace-functions-amp.md#parallel_for_each) oferuje mechanizm do iterowania za pomocą elementów danych lub *domeny obliczeniowej*. W tym przykładzie domena obliczeniowa jest określana przez `sum.extent` . Kod, który chcesz wykonać, jest zawarty w wyrażeniu lambda lub *funkcji jądra*. `restrict(amp)`Wskazuje, że używany jest tylko podzbiór języka C++, który C++ amp może przyspieszyć.

- Indeks: zmienna [klasy indeksu](../../parallel/amp/reference/index-class.md) , `idx` ,, jest zadeklarowana z rangą 1 w celu dopasowania do rangi `array_view` obiektu. Za pomocą indeksu można uzyskać dostęp do poszczególnych elementów `array_view` obiektów.

## <a name="shaping-and-indexing-data-index-and-extent"></a>Kształtowanie i indeksowanie danych: indeks i zakres

Aby można było uruchomić kod jądra, należy zdefiniować wartości danych i zadeklarować kształt danych. Wszystkie dane są zdefiniowane jako tablica (prostokątna) i można zdefiniować tablicę, aby miała dowolną rangę (liczbę wymiarów). Dane mogą być dowolnego rozmiaru w dowolnym wymiarze.

### <a name="index-class"></a>index — Klasa

[Klasa index](../../parallel/amp/reference/index-class.md) określa lokalizację w `array` `array_view` obiekcie lub przez hermetyzację przesunięcia od początku w każdym wymiarze do jednego obiektu. Gdy uzyskujesz dostęp do lokalizacji w tablicy, przekazujesz `index` obiekt do operatora indeksowania, `[]` zamiast listy indeksów liczb całkowitych. Dostęp do elementów w każdym wymiarze można uzyskać za pomocą operatora [Array:: operator ()](reference/array-class.md#operator_call) lub operatora [array_view:: operator ()](reference/array-view-class.md#operator_call).

Poniższy przykład tworzy jednowymiarowy indeks, który określa trzeci element w jednowymiarowym `array_view` obiekcie. Indeks jest używany do drukowania trzeciego elementu w `array_view` obiekcie. Dane wyjściowe to 3.

```cpp
int aCPP[] = {1, 2, 3, 4, 5};
array_view<int, 1> a(5, aCPP);

index<1> idx(2);

std::cout << a[idx] << "\n";
// Output: 3
```

Poniższy przykład tworzy dwuwymiarowy indeks, który określa element, gdzie wiersz = 1 i kolumna = 2 w jednowymiarowym `array_view` obiekcie. Pierwszy parametr w `index` konstruktorze jest składnikiem wiersza, a drugi parametr jest składnikiem kolumny. Dane wyjściowe to 6.

```cpp
int aCPP[] = {1, 2, 3, 4, 5, 6};
array_view<int, 2> a(2, 3, aCPP);

index<2> idx(1, 2);

std::cout <<a[idx] << "\n";
// Output: 6
```

Poniższy przykład tworzy trójwymiarowy indeks, który określa element, gdzie głębokość = 0, wiersz = 1 i kolumna = 3 w obiekcie trójwymiarowym `array_view` . Należy zauważyć, że pierwszy parametr jest składnikiem głębokości, drugi parametr jest składnikiem wiersza, a trzeci parametr jest składnikiem kolumny. Dane wyjściowe to 8.

```cpp
int aCPP[] = {
    1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12,
    1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12};

array_view<int, 3> a(2, 3, 4, aCPP);

// Specifies the element at 3, 1, 0.
index<3> idx(0, 1, 3);

std::cout << a[idx] << "\n";
// Output: 8
```

### <a name="extent-class"></a>extent — Klasa

[Klasa zakresu](../../parallel/amp/reference/extent-class.md) określa długość danych w każdym wymiarze `array` lub `array_view` obiektu. Możesz utworzyć zakres i użyć go do utworzenia `array` `array_view` obiektu lub. Możesz również pobrać zakres istniejącego `array` `array_view` obiektu lub. Poniższy przykład drukuje długość zakresu w każdym wymiarze `array_view` obiektu.

```cpp
int aCPP[] = {
    1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12,
    1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12};
// There are 3 rows and 4 columns, and the depth is two.
array_view<int, 3> a(2, 3, 4, aCPP);

std::cout << "The number of columns is " << a.extent[2] << "\n";
std::cout << "The number of rows is " << a.extent[1] << "\n";
std::cout << "The depth is " << a.extent[0] << "\n";
std::cout << "Length in most significant dimension is " << a.extent[0] << "\n";
```

Poniższy przykład tworzy `array_view` obiekt, który ma te same wymiary co obiekt w poprzednim przykładzie, ale w tym przykładzie użyto `extent` obiektu zamiast używania jawnych parametrów w `array_view` konstruktorze.

```cpp
int aCPP[] = {1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21, 22, 23, 24};
extent<3> e(2, 3, 4);

array_view<int, 3> a(e, aCPP);

std::cout << "The number of columns is " << a.extent[2] << "\n";
std::cout << "The number of rows is " << a.extent[1] << "\n";
std::cout << "The depth is " << a.extent[0] << "\n";
```

## <a name="moving-data-to-the-accelerator-array-and-array_view"></a>Przeniesienie danych do akceleratora: Array i array_view

Dwa kontenery danych używane do przenoszenia danych do akceleratora są zdefiniowane w bibliotece środowiska uruchomieniowego. Są one [klasą Array](../../parallel/amp/reference/array-class.md) i [klasą array_view](../../parallel/amp/reference/array-view-class.md). `array`Klasa jest klasą kontenera, która tworzy głębokie kopie danych podczas konstruowania obiektu. `array_view`Klasa jest klasą otoki, która kopiuje dane, gdy funkcja jądra uzyskuje dostęp do danych. Gdy dane są zbędne na urządzeniu źródłowym, dane są kopiowane z powrotem.

### <a name="array-class"></a>array — Klasa

Gdy `array` obiekt jest skonstruowany, szczegółowa kopia danych jest tworzona w akceleratorze, jeśli używasz konstruktora, który zawiera wskaźnik do zestawu danych. Funkcja jądra modyfikuje kopię na akceleratorze. Po zakończeniu wykonywania funkcji jądra należy skopiować dane z powrotem do struktury danych źródłowych. Poniższy przykład mnoży każdy element w wektorze o 10. Po zakończeniu działania jądra, `vector conversion operator` służy do kopiowania danych z powrotem do obiektu Vector.

```cpp
std::vector<int> data(5);

for (int count = 0; count <5; count++)
{
    data[count] = count;
}

array<int, 1> a(5, data.begin(), data.end());

parallel_for_each(
    a.extent,
    [=, &a](index<1> idx) restrict(amp) {
        a[idx] = a[idx]* 10;
    });

data = a;
for (int i = 0; i < 5; i++)
{
    std::cout << data[i] << "\n";
}
```

### <a name="array_view-class"></a>array_view — Klasa

`array_view`Ma niemal te same elementy członkowskie co `array` Klasa, ale zachowanie podstawowe nie jest takie samo. Dane przesłane do `array_view` konstruktora nie są replikowane na procesorze GPU, ponieważ jest on z `array` konstruktorem. Zamiast tego dane są kopiowane do akceleratora po wykonaniu funkcji jądra. W związku z tym, jeśli tworzysz dwa `array_view` obiekty, które używają tych samych danych, oba `array_view` obiekty odnoszą się do tego samego miejsca w pamięci. Po wykonaniu tej czynności należy zsynchronizować dowolny dostęp wielowątkowy. Główną zaletą korzystania z `array_view` klasy jest przeniesienie danych tylko wtedy, gdy jest to konieczne.

### <a name="comparison-of-array-and-array_view"></a>Porównanie tablic i array_view

W poniższej tabeli zestawiono podobieństwa i różnice między `array` `array_view` klasami i.

|Opis|array — Klasa|array_view — klasa|
|-----------------|-----------------|-----------------------|
|Po ustaleniu rangi|W czasie kompilacji.|W czasie kompilacji.|
|Po ustaleniu zakresu|W czasie wykonywania.|W czasie wykonywania.|
|Kształt|Wzdłuż.|Wzdłuż.|
|Magazyn danych|Jest kontenerem danych.|Jest otoką danych.|
|Kopiuj|Jawna i szczegółowa kopia w definicji.|Niejawne kopiowanie, gdy uzyskuje dostęp do funkcji jądra.|
|Pobieranie danych|Kopiując dane tablicowe z powrotem do obiektu w wątku procesora CPU.|Dzięki bezpośredniemu dostępowi do `array_view` obiektu lub wywołując [metodę array_view:: synchroniz](reference/array-view-class.md#synchronize) , aby kontynuować dostęp do danych w oryginalnym kontenerze.|

### <a name="shared-memory-with-array-and-array_view"></a>Pamięć współdzielona z tablicą i array_view

Pamięć współdzielona jest pamięcią, do której można uzyskać dostęp zarówno przy użyciu procesora, jak i akceleratora. Użycie pamięci współużytkowanej eliminuje lub znacznie zmniejsza obciążenie związane z kopiowaniem danych między PROCESORem a akceleratorem. Mimo że pamięć jest udostępniona, dostęp do niej nie jest możliwy jednocześnie przez procesor i akcelerator, a tym samym powoduje niezdefiniowane zachowanie.

`array`obiekty mogą służyć do określania precyzyjnej kontroli nad użyciem pamięci współdzielonej, jeśli skojarzony akcelerator obsługuje tę funkcję. Czy akcelerator obsługuje pamięć współużytkowaną jest określany przez właściwość [supports_cpu_shared_memory](reference/accelerator-class.md#supports_cpu_shared_memory) akceleratora, która zwraca wartość, **`true`** gdy obsługiwana jest pamięć współdzielona. Jeśli obsługiwana jest pamięć współdzielona, domyślne [wyliczenie access_type](reference/concurrency-namespace-enums-amp.md#access_type) dla alokacji pamięci w akceleratorze jest określane przez `default_cpu_access_type` Właściwość. Domyślnie `array` obiekty i są `array_view` wykonywane w taki sam `access_type` sposób, jak skojarzona z nim podstawowa `accelerator` .

Przez ustawienie właściwości [element członkowski danych Array:: cpu_access_type](reference/array-class.md#cpu_access_type) `array` jawnie można wykonać szczegółową kontrolę nad sposobem używania pamięci współużytkowanej, aby zoptymalizować aplikację pod kątem charakterystyki wydajności sprzętu w oparciu o wzorce dostępu do pamięci w jądrach obliczeniowych. `array_view`Odzwierciedla te same dane, `cpu_access_type` które są `array` skojarzone z; lub, jeśli array_view jest konstruowany bez źródła danych, `access_type` odzwierciedla środowisko, które po raz pierwszy powoduje przydzielenie magazynu. Oznacza to, że jeśli dostęp do niego następuje po raz pierwszy przez hosta (procesor CPU), działa on tak, jakby został utworzony za pośrednictwem źródła danych procesora CPU i ma udział w `access_type` `accelerator_view` przechwyceniu. Jeśli jednak dostęp do niego następuje po raz pierwszy `accelerator_view` , jest on traktowany tak, jakby został utworzony `array` w ramach utworzonego elementu `accelerator_view` i `array` udostępnia `access_type` .

Poniższy przykład kodu pokazuje, jak ustalić, czy akcelerator domyślny obsługuje pamięć współużytkowaną, a następnie tworzy kilka tablic, które mają różne konfiguracje cpu_access_type.

```cpp
#include <amp.h>
#include <iostream>

using namespace Concurrency;

int main()
{
    accelerator acc = accelerator(accelerator::default_accelerator);

    // Early out if the default accelerator doesn’t support shared memory.
    if (!acc.supports_cpu_shared_memory)
    {
        std::cout << "The default accelerator does not support shared memory" << std::endl;
        return 1;
    }

    // Override the default CPU access type.
    acc.default_cpu_access_type = access_type_read_write

    // Create an accelerator_view from the default accelerator. The
    // accelerator_view inherits its default_cpu_access_type from acc.
    accelerator_view acc_v = acc.default_view;

    // Create an extent object to size the arrays.
    extent<1> ex(10);

    // Input array that can be written on the CPU.
    array<int, 1> arr_w(ex, acc_v, access_type_write);

    // Output array that can be read on the CPU.
    array<int, 1> arr_r(ex, acc_v, access_type_read);

    // Read-write array that can be both written to and read from on the CPU.
    array<int, 1> arr_rw(ex, acc_v, access_type_read_write);
}
```

## <a name="executing-code-over-data-parallel_for_each"></a>Wykonywanie kodu przez dane: parallel_for_each

Funkcja [parallel_for_each](reference/concurrency-namespace-functions-amp.md#parallel_for_each) definiuje kod, który ma być uruchamiany na akceleratorze względem danych w `array` `array_view` obiekcie lub. Rozważmy następujący kod z wprowadzenia tego tematu.

```cpp
#include <amp.h>
#include <iostream>
using namespace concurrency;

void AddArrays() {
    int aCPP[] = {1, 2, 3, 4, 5};
    int bCPP[] = {6, 7, 8, 9, 10};
    int sumCPP[5] = {0, 0, 0, 0, 0};

    array_view<int, 1> a(5, aCPP);
    array_view<int, 1> b(5, bCPP);
    array_view<int, 1> sum(5, sumCPP);

    parallel_for_each(
        sum.extent,
        [=](index<1> idx) restrict(amp)
        {
            sum[idx] = a[idx] + b[idx];
        }
    );

    for (int i = 0; i < 5; i++) {
        std::cout << sum[i] << "\n";
    }
}
```

`parallel_for_each`Metoda przyjmuje dwa argumenty, domenę obliczeniową i wyrażenie lambda.

*Domena obliczeniowa* jest `extent` obiektem lub `tiled_extent` obiektem, który definiuje zestaw wątków do utworzenia na potrzeby wykonywania równoległego. Jeden wątek jest generowany dla każdego elementu w domenie obliczeniowej. W tym przypadku `extent` obiekt jest jednowymiarowy i zawiera pięć elementów. W związku z tym uruchamiane są pięć wątków.

*Wyrażenie lambda* definiuje kod do uruchomienia w każdym wątku. Klauzula Capture, `[=]` określa, że treść wyrażenia lambda uzyskuje dostęp do wszystkich przechwyconych zmiennych według wartości, które w tym przypadku są `a` , `b` i `sum` . W tym przykładzie lista parametrów tworzy zmienną jednowymiarową `index` o nazwie `idx` . Wartość `idx[0]` jest równa 0 w pierwszym wątku i zwiększa się o jeden w każdym następnym wątku. `restrict(amp)`Wskazuje, że używany jest tylko podzbiór języka C++, który C++ amp może przyspieszyć.  Ograniczenia dotyczące funkcji, które mają modyfikator ograniczenia są opisane w [Ogranicz (C++ amp)](../../cpp/restrict-cpp-amp.md). Aby uzyskać więcej informacji, zobacz, [składnia wyrażenia lambda](../../cpp/lambda-expression-syntax.md).

Wyrażenie lambda może zawierać kod do wykonania lub może wywołać oddzielną funkcję jądra. Funkcja jądra musi zawierać `restrict(amp)` modyfikator. Poniższy przykład jest odpowiednikiem poprzedniego przykładu, ale wywołuje oddzielną funkcję jądra.

```cpp
#include <amp.h>
#include <iostream>
using namespace concurrency;

void AddElements(
    index<1> idx,
    array_view<int, 1> sum,
    array_view<int, 1> a,
    array_view<int, 1> b) restrict(amp) {
    sum[idx] = a[idx] + b[idx];
}

void AddArraysWithFunction() {

    int aCPP[] = {1, 2, 3, 4, 5};
    int bCPP[] = {6, 7, 8, 9, 10};
    int sumCPP[5] = {0, 0, 0, 0, 0};

    array_view<int, 1> a(5, aCPP);
    array_view<int, 1> b(5, bCPP);
    array_view<int, 1> sum(5, sumCPP);

    parallel_for_each(
        sum.extent,
        [=](index<1> idx) restrict(amp) {
            AddElements(idx, sum, a, b);
        }
    );

    for (int i = 0; i < 5; i++) {
        std::cout << sum[i] << "\n";
    }
}
```

## <a name="accelerating-code-tiles-and-barriers"></a>Przyspieszanie kodu: kafelki i bariery

Dodatkowe przyspieszenie można uzyskać, korzystając z dzielenia. Dzielenie dzieli wątki na równe prostokątne podzestawy lub *kafelki*. Należy określić odpowiedni rozmiar kafelka na podstawie zestawu danych i algorytmu, który jest używany do kodowania. Dla każdego wątku masz dostęp do *globalnej* lokalizacji elementu danych względem całości `array` lub `array_view` i dostępu do lokalizacji *lokalnej* względem kafelka. Użycie wartości indeksu lokalnego upraszcza kod, ponieważ nie trzeba pisać kodu w celu przetłumaczenia wartości indeksu z globalnego na Local. Aby użyć dzielenia, wywołaj [metodę zakres:: kafelek](reference/extent-class.md#tile) w domenie obliczeniowej w `parallel_for_each` metodzie i użyj obiektu [tiled_index](../../parallel/amp/reference/tiled-index-class.md) w wyrażeniu lambda.

W typowych aplikacjach elementy w kafelku są powiązane w jakiś sposób, a kod musi mieć dostęp i śledzić wartości na kafelku. Użyj słowa kluczowego [Tile_static słowo kluczowe](../../cpp/tile-static-keyword.md) i [metody tile_barrier:: wait](reference/tile-barrier-class.md#wait) , aby to zrobić. Zmienna, która ma **tile_static** słowo kluczowe ma zakres w całym kafelku, a wystąpienie zmiennej jest tworzone dla każdego kafelka. Musisz obsłużyć synchronizację dostępu do wątku kafelków ze zmienną. [Metoda tile_barrier:: wait](reference/tile-barrier-class.md#wait) przerywa wykonywanie bieżącego wątku, dopóki wszystkie wątki we fragmencie nie osiągną wywołania `tile_barrier::wait` . Dzięki temu można zbierać wartości na kafelku przy użyciu zmiennych **tile_static** . Następnie można zakończyć wszelkie obliczenia, które wymagają dostępu do wszystkich wartości.

Poniższy diagram przedstawia dwuwymiarową tablicę danych próbkowania, które są rozmieszczone na kafelkach.

![Indeksuj wartości w rozdzielnym zakresie](../../parallel/amp/media/camptiledgridexample.png "Indeksuj wartości w rozdzielnym zakresie")

Poniższy przykład kodu używa danych próbkowania z poprzedniego diagramu. Kod zastępuje każdą wartość na kafelku przez średnią wartości na kafelku.

```cpp
// Sample data:
int sampledata[] = {
    2, 2, 9, 7, 1, 4,
    4, 4, 8, 8, 3, 4,
    1, 5, 1, 2, 5, 2,
    6, 8, 3, 2, 7, 2};

// The tiles:
// 2 2    9 7    1 4
// 4 4    8 8    3 4
//
// 1 5    1 2    5 2
// 6 8    3 2    7 2

// Averages:
int averagedata[] = {
    0, 0, 0, 0, 0, 0,
    0, 0, 0, 0, 0, 0,
    0, 0, 0, 0, 0, 0,
    0, 0, 0, 0, 0, 0,
};

array_view<int, 2> sample(4, 6, sampledata);

array_view<int, 2> average(4, 6, averagedata);

parallel_for_each(
    // Create threads for sample.extent and divide the extent into 2 x 2 tiles.
    sample.extent.tile<2,2>(),
        [=](tiled_index<2,2> idx) restrict(amp) {
        // Create a 2 x 2 array to hold the values in this tile.
        tile_static int nums[2][2];

        // Copy the values for the tile into the 2 x 2 array.
        nums[idx.local[1]][idx.local[0]] = sample[idx.global];

        // When all the threads have executed and the 2 x 2 array is complete, find the average.
        idx.barrier.wait();
        int sum = nums[0][0] + nums[0][1] + nums[1][0] + nums[1][1];

        // Copy the average into the array_view.
        average[idx.global] = sum / 4;
    });

for (int i = 0; i <4; i++) {
    for (int j = 0; j <6; j++) {
        std::cout << average(i,j) << " ";
    }
    std::cout << "\n";
}

// Output:
// 3 3 8 8 3 3
// 3 3 8 8 3 3
// 5 5 2 2 4 4
// 5 5 2 2 4 4
```

## <a name="math-libraries"></a>Biblioteki matematyczne

C++ AMP obejmuje dwie biblioteki matematyczne. Biblioteka o podwójnej precyzji w [przestrzeni nazw współbieżności::p recise_math](../../parallel/amp/reference/concurrency-precise-math-namespace.md) zapewnia obsługę funkcji podwójnej precyzji. Zapewnia również obsługę funkcji o pojedynczej precyzji, chociaż pomoc techniczna o podwójnej precyzji na sprzęcie jest nadal wymagana. Jest on zgodny ze [specyfikacją C99 (ISO/IEC 9899)](https://go.microsoft.com/fwlink/p/?linkid=225887). Akcelerator musi obsługiwać pełną podwójną precyzję. Można określić, czy robi to poprzez sprawdzenie wartości [elementu członkowskiego danych akceleratora:: supports_double_precision](reference/accelerator-class.md#supports_double_precision). Szybka Biblioteka matematyczna w [przestrzeni nazw Concurrency:: fast_math](../../parallel/amp/reference/concurrency-fast-math-namespace.md)zawiera inny zestaw funkcji matematycznych. Te funkcje, które obsługują tylko **`float`** operandy, wykonują się szybciej, ale nie są tak dokładne jak te w bibliotece matematycznej o podwójnej precyzji. Funkcje są zawarte w \<amp_math.h> pliku nagłówka i wszystkie są zadeklarowane za pomocą `restrict(amp)` . Funkcje w \<cmath> pliku nagłówkowym są importowane do `fast_math` `precise_math` przestrzeni nazw i. **`restrict`** Słowo kluczowe jest używane do rozróżnienia \<cmath> wersji i wersji C++ amp. Poniższy kod oblicza logarytm dziesiętny przy użyciu metody Fast dla każdej wartości, która znajduje się w domenie obliczeniowej.

```cpp
#include <amp.h>
#include <amp_math.h>
#include <iostream>
using namespace concurrency;

void MathExample() {

    double numbers[] = { 1.0, 10.0, 60.0, 100.0, 600.0, 1000.0 };
    array_view<double, 1> logs(6, numbers);

    parallel_for_each(
        logs.extent,
        [=] (index<1> idx) restrict(amp) {
            logs[idx] = concurrency::fast_math::log10(numbers[idx]);
        }
    );

    for (int i = 0; i < 6; i++) {
        std::cout << logs[i] << "\n";
    }
}
```

## <a name="graphics-library"></a>Biblioteka grafiki

C++ AMP zawiera bibliotekę grafiki, która została zaprojektowana do przyspieszenia programowania grafiki. Ta biblioteka jest używana tylko na urządzeniach, które obsługują natywną funkcjonalność grafiki. Metody znajdują się w [przestrzeni nazw Concurrency:: Graphics](../../parallel/amp/reference/concurrency-graphics-namespace.md) i są zawarte w \<amp_graphics.h> pliku nagłówkowym. Najważniejsze składniki biblioteki graficznej to:

- [Klasa tekstury](../../parallel/amp/reference/texture-class.md): można użyć klasy texture do tworzenia tekstury z pamięci lub z pliku. Tekstury są podobne do tablic, ponieważ zawierają dane i są podobne do kontenerów w standardowej bibliotece języka C++, w odniesieniu do konstrukcji i kopiowania. Aby uzyskać więcej informacji, zobacz [kontenery standardowej biblioteki języka C++](../../standard-library/stl-containers.md). Parametry szablonu dla `texture` klasy to typ elementu i ranga. Rangą może być 1, 2 lub 3. Typ elementu może być jednym z typów krótkich wektorów, które zostały opisane w dalszej części tego artykułu.

- [klasa writeonly_texture_view](../../parallel/amp/reference/writeonly-texture-view-class.md): zapewnia dostęp tylko do zapisu do dowolnej tekstury.

- Krótka Biblioteka wektorów: definiuje zestaw krótkich typów wektorów o długości 2, 3 i 4, które są oparte na **`int`** , `uint` ,, **`float`** **`double`** , [normie](../../parallel/amp/reference/norm-class.md)lub [unorm](../../parallel/amp/reference/unorm-class.md).

## <a name="universal-windows-platform-uwp-apps"></a>Aplikacje platforma uniwersalna systemu Windows (platformy UWP)

Podobnie jak w przypadku innych bibliotek C++, możesz używać C++ AMP w aplikacjach platformy UWP. W tych artykułach opisano sposób dołączania kodu C++ AMP w aplikacjach utworzonych przy użyciu języka C++, C#, Visual Basic lub JavaScript:

- [Używanie C++ AMP w aplikacjach platformy UWP](../../parallel/amp/using-cpp-amp-in-windows-store-apps.md)

- [Przewodnik: Tworzenie podstawowego składnika środowisko wykonawcze systemu Windows w języku C++ i wywoływanie go przy użyciu języka JavaScript](https://go.microsoft.com/fwlink/p/?linkid=249077)

- [Optymalizator podróży w usłudze mapy Bing — aplikacja ze sklepu Windows w języku JavaScript i C++](https://go.microsoft.com/fwlink/p/?linkid=249078)

- [Jak używać C++ AMP z języka C# przy użyciu środowisko wykonawcze systemu Windows](https://devblogs.microsoft.com/pfxteam/how-to-use-c-amp-from-c-using-winrt/)

- [Jak używać C++ AMP z języka C #](https://devblogs.microsoft.com/pfxteam/how-to-use-c-amp-from-c/)

- [Wywoływanie funkcji natywnych z kodu zarządzanego](../../dotnet/calling-native-functions-from-managed-code.md)

## <a name="c-amp-and-concurrency-visualizer"></a>C++ AMP i Concurrency Visualizer

Wizualizator współbieżności obejmuje obsługę analizowania wydajności kodu C++ AMP. Te artykuły zawierają opis tych funkcji:

- [Wykres aktywności GPU](/visualstudio/profiling/gpu-activity-graph)

- [Aktywność GPU (Stronicowanie)](/visualstudio/profiling/gpu-activity-paging)

- [Aktywności procesora GPU (ten proces)](/visualstudio/profiling/gpu-activity-this-process)

- [Aktywność procesora GPU (inne procesy)](/visualstudio/profiling/gpu-activity-other-processes)

- [Kanały (Widok wątków)](/visualstudio/profiling/channels-threads-view)

- [Analizowanie kodu C++ AMP za pomocą wizualizatora współbieżności](/archive/blogs/nativeconcurrency/analyzing-c-amp-code-with-the-concurrency-visualizer)

## <a name="performance-recommendations"></a>Zalecenia dotyczące wydajności

Modulo i dzielenie liczb całkowitych bez znaku znacznie lepsza wydajność niż moduł i dzielenie liczb całkowitych ze znakiem. Zalecamy używanie niepodpisanych liczb całkowitych, gdy jest to możliwe.

## <a name="see-also"></a>Zobacz także

[C++ AMP (C++ Accelerated Massive Parallelism)](../../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)<br/>
[Składnia wyrażenia lambda](../../cpp/lambda-expression-syntax.md)<br/>
[Odwołanie (C++ AMP)](../../parallel/amp/reference/reference-cpp-amp.md)<br/>
[Programowanie równoległe w kodzie natywnym blogu](https://go.microsoft.com/fwlink/p/?linkid=238472)
